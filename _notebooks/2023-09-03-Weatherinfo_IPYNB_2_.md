---
layout: post
title: Weather Information
description: Find The Weather in Any Location
toc: True
categories: ['5.A', 'C4.1']
courses: {'compsci': {'week': 3, 'categories': ['6.B']}}
type: hacks
---

![](_notebooks/XHqB.gif)

<div id="output"></div>
<script>
const output = document.getElementById("output");
</script>


```python

```

<script>
    function Weather() {
        const apiKey = '41c77cef54444957bbb80248230609';

        // Define the API endpoint URL
        const apiUrl = 'https://api.weatherapi.com/v1/current.json';

        // Get the user's input location
        const location = document.getElementById('input2').value;

        // Set up the request parameters, including the API key and location
        const params = {
            key: apiKey,
            q: location, // Use the user's input as the location
            // Add other parameters as needed based on the API documentation
        };

        // Build the URL with query parameters
        const url = new URL(apiUrl);
        url.search = new URLSearchParams(params).toString();

        // Make an HTTP GET request to the API
        fetch(url)
            .then(response => {
                if (response.ok) {
                    return response.json(); // Parse the JSON response
                } else {
                    throw new Error('Request failed.');
                }
            })
            .then(data => {
                // Handle the API response data here
                console.log(data);
                output.innerHTML="The current weather at this location in Farenheit is "+data.current.temp_f+ "degrees and in celcius it is "+data.current.temp_c+" degrees.";
            })
            .catch(error => {
                console.error('Error:', error);
            });
    }
</script>

<body>
    <input type="text" id="input2">
    <button onclick="Weather()">Submit Location</button>
</body>


