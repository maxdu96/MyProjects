>## Azure Open AI 
>> Chat API <b>Tool calls</b> Implement with PHP

Result:
 <img src="/AzureOpenAI/Image/win_1000.png"/>


 MySQL database:
 <img src="/AzureOpenAI/Image/db_screenCap.png"/>


Full code here:
``` php
<?php
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);

function searchProducts($productName = null, $winnerName = null) {
    if (empty($productName) && empty($winnerName)) {
        return [];
    }
 
    $dbHost = '**.**.**.***';
    $dbUser = '********';
    $dbPass = '********';
    $dbName = '********';

    $conn = mysqli_connect($dbHost, $dbUser, $dbPass, $dbName);
    if (!$conn) {
        echo "Connection failed: ";
        return [];
    }

    $sql = "SELECT description, winner_staffname FROM lucky_draw_list WHERE 1=1";
    $types = '';
    $params = [];
    
    if ($productName !== null) {
        $sql .= " AND description LIKE CONCAT('%', ?, '%')";
        $types .= 's';
        $params[] = $productName;
    }
    
    if ($winnerName !== null) {
        $sql .= " AND winner_staffname LIKE CONCAT('%', ?, '%')";
        $types .= 's';
        $params[] = $winnerName;
    }
    
    $stmt = mysqli_prepare($conn, $sql);
    
    if ($params) {
        mysqli_stmt_bind_param($stmt, $types, ...$params);
    }
    
    mysqli_stmt_execute($stmt);
    $result = mysqli_stmt_get_result($stmt);
    
    $results = [];
    while ($row = mysqli_fetch_assoc($result)) {
        $results[] = $row;
    }

    mysqli_close($conn);
    return $results;
}

function getAnswer($gptAPI_token, $content, $gptAPI) {
    $proxyUrl = 'http://proxy.****.***:****';
    $tools = [
        [
            'type' => 'function',
            'function' => [
                'name' => 'searchProducts',
                'description' => 'Search products and their winners by product name OR winner name. At least one parameter is required.',
                'parameters' => [
                    'type' => 'object',
                    'properties' => [
                        'productName' => [
                            'type' => 'string',
                            'description' => 'Partial or full product name to search (e.g. "iPad")'
                        ],
                        'winnerName' => [
                            'type' => 'string',
                            'description' => 'Partial or full staff name of the winner (e.g. "John Smith")'
                        ]
                        ],
                        // 'required'=> [
                        //     'productName'
                        // ]
                ]
            ]
        ]
    ];

    $data = [
        'approach' => 'rrr',
        'history' => [
            [
                'role' => 'user',
                'content' => $content,
            ]
        ],

        'overrides' => [
            'tools' => $tools,
            'top' => 0,
            'model' => 'gpt-4o-mini',
            'max_tokens' => 1000,
            'temperature' => 0,
            'top_p' => 1,
            'presence_penalty' => 0,
            'frequency_penalty' => 0,
            'security_scan' => 'OFF'
        ]
    ];

    $headers = [
        'x-api-key: ' . $gptAPI_token,
        'Content-Type: application/json'
    ];

    $executeApiCall = function($data) use ($gptAPI, $headers, $proxyUrl) {
        $ch = curl_init();
        curl_setopt_array($ch, [
            CURLOPT_URL => $gptAPI,
            CURLOPT_POST => true,
            CURLOPT_POSTFIELDS => json_encode($data),
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_HTTPHEADER => $headers,
            CURLOPT_PROXY => $proxyUrl,
            CURLOPT_PROXYTYPE => CURLPROXY_HTTP,
            CURLOPT_SSL_VERIFYPEER => false
        ]);
        $response = curl_exec($ch);
        if (curl_errno($ch)) {
            throw new Exception('Curl error: ' . curl_error($ch));
        }
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        curl_close($ch);
        if ($httpCode !== 200) {
            throw new Exception("API returned HTTP code $httpCode: $response");
        }
        return json_decode($response, true);
    };

    $responseData = $executeApiCall($data);

    // Process tool calls
    if (isset($responseData['message']['tool_calls'])) {
        foreach ($responseData['message']['tool_calls'] as $toolCall) {
            $functionName = $toolCall['function']['name'];
            
            $arguments = json_decode($toolCall['function']['arguments'], true);

            $functionResult = [];
            if ($functionName == 'searchProducts') {
                try {
                    $productName = $arguments['productName'];
                    $winnerName = $arguments['winnerName'];
                    $functionResult = searchProducts($productName, $winnerName);
                } catch (Exception $e) {
                    $functionResult = ['error' => $e->getMessage()];
                }
            }

            // Update message history
            $data['history'][] = [
                'role' => 'assistant',
                'content' => null,
                'tool_calls' => [$toolCall]
            ];
           
            $data['history'][] = [
                'role' => 'tool',
                'content' => json_encode($functionResult),
                'name' => $functionName,
                'tool_call_id' => $toolCall['id']
            ];
        }

        // Second API call with tool results
        $responseData = $executeApiCall($data);
    }

    return $responseData["answer"];
}


$gptAPI_token = '******************************************';
// $content = 'Who picked the $1000 gift card?';
$content = 'Is Dick picked the $1000 gift card?';
// $content = 'what product does Chris picked?';
// $content = 'tell me a joke';
$gptAPI = 'https://api.uat.bot-builder/******************************';

// Call the function with tools
echo getAnswer($gptAPI_token, $content, $gptAPI);

?>
```

