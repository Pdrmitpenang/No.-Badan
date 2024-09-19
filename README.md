<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>No. Badan Search</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .result {
            margin-top: 20px;
            border: 1px solid #ccc;
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1>Search No. Badan</h1>
    <form id="searchForm">
        <label for="noBadan">Enter No. Badan:</label>
        <input type="text" id="noBadan" name="noBadan" required>
        <button type="submit">Search</button>
    </form>
    
    <div id="result" class="result"></div>

    <script>
        document.getElementById('searchForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const noBadan = document.getElementById('noBadan').value;
            fetch(`YOUR_SCRIPT_URL?noBadan=${noBadan}`)
                .then(response => response.json())
                .then(data => {
                    if (data.PangkatGred) {
                        document.getElementById('result').innerHTML = `
                            <h2>Results:</h2>
                            <p><strong>Pangkat/Gred:</strong> ${data.PangkatGred}</p>
                            <p><strong>No. Badan:</strong> ${data.NoBadan}</p>
                            <p><strong>Nama:</strong> ${data.Nama}</p>
                            <p><strong>Jawatan:</strong> ${data.Jawatan}</p>
                            <p><strong>Tempat Bertugas:</strong> ${data.TempatBertugas}</p>
                            <p><strong>No. Meja:</strong> ${data.NoMeja}</p>
                        `;
                    } else {
                        document.getElementById('result').innerHTML = `<p>No. Badan not found</p>`;
                    }
                })
                .catch(error => {
                    document.getElementById('result').innerHTML = `<p>Error fetching data</p>`;
                });
        });
    </script>
</body>
</html>
