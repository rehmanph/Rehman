# Rehm<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram Reel Downloader</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #8E2DE2, #4A00E0);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            color: white;
            text-align: center;
        }
        
        .container {
            background: rgba(255, 255, 255, 0.1);
            padding: 50px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
        
        .blue-light {
            animation: blue-light-effect 2s infinite;
        }
        
        @keyframes blue-light-effect {
            0% {
                text-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
            }
            50% {
                text-shadow: 0 0 20px rgba(0, 123, 255, 1);
            }
            100% {
                text-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
            }
        }
        
        input[type="text"] {
            width: 80%;
            padding: 10px;
            border: 2px solid red;
            border-radius: 5px;
            margin-bottom: 10px;
            outline: none;
        }
        
        button {
            padding: 10px 20px;
            font-size: 16px;
            color: white;
            background: linear-gradient(45deg, #ff416c, #ff4b2b);
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }
        
        button:hover {
            background: #e63956;
        }
        
        .result {
            margin-top: 20px;
        }
        
        video, img {
            max-width: 100%;
            border-radius: 10px;
        }
        
        .footer {
            margin-top: 20px;
            font-size: 14px;
            color: #ddd;
        }
        
        .whatsapp-button {
            margin-top: 15px;
            padding: 10px 20px;
            background: linear-gradient(135deg, #11998e, #38ef7d);
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="blue-light">Rehman 𝐈𝐧𝐬𝐭𝐚 𝐑𝐞𝐞𝐥 𝐃𝐨𝐰𝐧𝐥𝐨𝐚𝐝𝐞𝐫</h1>
        <input type="text" id="urlInput" placeholder="Enter Instagram Reel URL">
        <button onclick="fetchInstagramReel()">Download</button>
        <div id="result" class="result"></div>
        <a href="https:                                                                                                     
    </div>
    <div class="footer">𝐌𝐀𝐃𝐄 𝐁𝐘 REHMAN-PANHWER</div>
    <script>
        function fetchInstagramReel() {
            const url = document.getElementById('urlInput').value;
            const resultContainer = document.getElementById('result');
            resultContainer.innerHTML = '';
            if (!url) {
                alert("Please enter a valid URL");
                return;
            }
            resultContainer.innerHTML = '<p>Fetching...</p>';
            const apiUrl = `https://insta-dl.hazex.workers.dev/?url=${encodeURIComponent(url)}`;
            fetch(apiUrl)
                .then(response => response.json())
                .then(data => {
                    resultContainer.innerHTML = '';
                    if (!data.error) {
                        const mediaUrl = data.result.url;
                        const extension = data.result.extension;
                        if (extension === 'mp4') {
                            const videoElement = document.createElement('video');
                            videoElement.src = mediaUrl;
                            videoElement.controls = true;
                            
