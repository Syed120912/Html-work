#
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pak SIM Information</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #121212; color: #fff; text-align: center; }
        .container { margin-top: 100px; }
        input { padding: 10px; width: 300px; border-radius: 5px; border: 1px solid #ccc; }
        button { padding: 10px 20px; background-color: teal; color: #fff; border: none; border-radius: 5px; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Pak SIM Information</h1>
        <p>Enter a phone number to get details:</p>
        <input type="text" id="phone" placeholder="e.g., 03XX-XXXXXXX">
        <button onclick="fetchSimData()">Search</button>
        <div id="result"></div>
    </div>
    <script>
        async function fetchSimData() {
            const phone = document.getElementById('phone').value;
            const response = await fetch('/api/sim-info?phone=' + phone);
            const data = await response.json();
            document.getElementById('result').innerHTML = data ? 
                `<p><strong>SIM Details:</strong> ${JSON.stringify(data)}</p>` : 
                '<p>No data found.</p>';
        }
    </script>
</body>
</html>
ok


