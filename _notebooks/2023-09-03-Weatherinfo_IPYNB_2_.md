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



<script>
    function Weather() {
        const apiKey = '41c77cef54444957bbb80248230609';
        const apiUrl = 'https://api.weatherapi.com/v1/current.json';
        const location = document.getElementById('input2').value;
        const params = {
            key: apiKey,
            q: location, 
        };
        const url = new URL(apiUrl);
        url.search = new URLSearchParams(params).toString();
        fetch(url)
            .then(response => {
                if (response.ok) {
                    return response.json(); 
                } else {
                    throw new Error('Request failed.');
                }
            })
            .then(data => {
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


