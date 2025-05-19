This part of the project documentation focuses on the **SCDO** API. Terms from the **SCDO** are accessible through an API endpoint.The **SCDO** API is organized around REST. Our API has predictable resource-oriented URLs, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

## API Request in Python

Displayed below is the code you would use to execute this API request in Python.

#### API Request: All terms
Returns all terms in the **SCDO**.

    import requests

    URL = 'https://2db8-41-157-180-219.sa.ngrok.io'

    # sending get request and saving the response as response object
    r = requests.get(url=URL)

    # extracting data in json format
    data = r.json()

    print(data['result'])

#### API Request: Specific terms
Returns speficic terms in the **SCDO**. Parses in a phrases or an array of phrases and returns all terms in the **SCDO** with specified phrases.

    import requests

    URL = 'https://2db8-41-157-180-219.sa.ngrok.io'

    # Array of terms
    terms = ["pain", "management"]

    # sending get request and saving the response as response object
    r = requests.get(url=URL, params={'terms': term})

    # extracting data in json format
    data = r.json()

    print(data['result'])

## API Request in PHP

Displayed below is the code you would use to execute this API request in PHP.

#### API Request: All terms
Returns all terms in the **SCDO**.

    <?php

    $ch = curl_init();

    $url = "https://2db8-41-157-180-219.sa.ngrok.io";

    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

    $resp = curl_exec($ch);

    if($e = curl_exec($ch)){
        echo $e;
    }
    else {
        $decoded = json_decode($resp, true);
        return $decoded;
    }

    curl_close($ch);

#### API Request: Specific terms
Returns speficic terms in the **SCDO**. Parses in a phrases or an array of phrases and returns all terms in the **SCDO** with specified phrases.

    <?php

    $url = "https://2db8-41-157-180-219.sa.ngrok.io";

    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, $url);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "GET");
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

    $headers = array(
    "Accept: application/json",
    "Content-Type: application/json",
    );
    curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);

    ## Array of terms
    $terms = <<<DATA
    {
        "term": ["pain", "management"]
    }
    DATA;

    curl_setopt($curl, CURLOPT_POSTFIELDS, $terms);

    $resp = curl_exec($curl);

    if (curl_errno($curl)) {
        $error_msg = curl_error($curl);
        echo $error_msg;
    }
    else{
        $decoded = json_decode($resp, true);

        if($decoded["result"][0][0][0] == NULL){
            var_dump($decoded["result"]);
            return $decoded;
        }
        else{
            var_dump($decoded["result"][0]);
            return $decoded["result"][0];
        }

    }

    curl_close($ch);

## Response

Both API requests return a **JSON** array of **SCDO** terms and their descriptions.

    {
        "result": [
            [
                1,
                "SCDO:0000005",
                "Abdominal Ultrasound",
                "A method of ultrasound imaging in which the ultrasound probe is pressed against the skin of the abdomen in order to create an image of the abdominal organs."
            ],
            [
                2,
                "SCDO:0000006",
                "Ability to Carry Out Activities of Daily Living",
                "The performance of the basic activities of self care, such as dressing, ambulation, or eating."
            ],