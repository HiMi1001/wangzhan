# wangzhan
01
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>遮罩滑块切换图片</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .container {
            position: relative;
            width: 80%;
            max-width: 600px;
            height: 400px;
            overflow: hidden;
            border: 2px solid #ccc;
            border-radius: 10px;
        }
        .image1, .image2 {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .image2 {
            z-index: 2;
            clip-path: inset(0% 0% 0% 0%);
            transition: clip-path 0.1s ease-out;
        }
        .slider {
            margin-top: 20px;
            width: 80%;
            max-width: 600px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 图片1在底层 -->
        <img src="https://cdn.myportfolio.com/b4c711c2-6633-4968-93d0-3679cf0f02af/2c5d509f-842f-4d89-bdea-f7ecba711eb2_rwc_0x0x1916x1080x640.jpg?h=d2dedefd4bec0c28abb9af19b685d557" alt="Image 1" class="image1">
        <!-- 图片2在上层，受遮罩影响 -->
        <img src="https://cdn.myportfolio.com/b4c711c2-6633-4968-93d0-3679cf0f02af/73573594-91df-44ed-b609-7f791c8f7288_rwc_8x0x1909x1076x640.png?h=659b4ca5819191207ada5a22977c235b" alt="Image 2" class="image2" id="image2">
    </div>
    <input type="range" min="0" max="100" value="100" class="slider" id="slider">

    <script>
        const slider = document.getElementById('slider');
        const image2 = document.getElementById('image2');

        slider.addEventListener('input', () => {
            const value = slider.value; // 获取滑块值
            // 根据滑块值调整遮罩大小
            image2.style.clipPath = `inset(0% ${100 - value}% 0% 0%)`;
        });
    </script>
</body>
</html>
