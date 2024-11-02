<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Individual Image Upload</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            background-color: #f4f4f9;
        }
        h1 {
            font-size: 24px;
            color: #333;
            margin-bottom: 20px;
        }
        .container {
            display: flex;
            gap: 20px;
            justify-content: center;
        }
        .box {
            width: 600px;
            height: 600px;
            border: 2px solid #333;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background-color: #eee;
            overflow: hidden;
            position: relative;
        }
        .box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .upload-btn {
            position: absolute;
            bottom: 10px;
            background-color: #333;
            color: #fff;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
            font-size: 14px;
        }
    </style>
</head>
<body>

    <h1>세대 갈등</h1>
    <div class="container">
        <div class="box" id="box1">
            <p>No Image</p>
            <input type="file" accept="image/*" style="display: none;" onchange="uploadImage(event, 'box1')" />
            <button class="upload-btn" onclick="document.getElementById('box1').querySelector('input').click()">Upload Image</button>
        </div>
        <div class="box" id="box2">
            <p>No Image</p>
            <input type="file" accept="image/*" style="display: none;" onchange="uploadImage(event, 'box2')" />
            <button class="upload-btn" onclick="document.getElementById('box2').querySelector('input').click()">Upload Image</button>
        </div>
        <div class="box" id="box3">
            <p>No Image</p>
            <input type="file" accept="image/*" style="display: none;" onchange="uploadImage(event, 'box3')" />
            <button class="upload-btn" onclick="document.getElementById('box3').querySelector('input').click()">Upload Image</button>
        </div>
    </div>

    <script>
        function uploadImage(event, boxId) {
            const file = event.target.files[0];
            const box = document.getElementById(boxId);

            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    box.innerHTML = `<img src="${e.target.result}" alt="Uploaded Image">`;
                    const uploadButton = document.createElement("button");
                    uploadButton.className = "upload-btn";
                    uploadButton.textContent = "Upload Image";
                    uploadButton.onclick = () => box.querySelector("input").click();
                    box.appendChild(uploadButton);
                };
                reader.readAsDataURL(file);
            }
        }
    </script>

</body>
</html>
