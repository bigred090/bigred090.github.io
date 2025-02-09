<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snow Rider 3D</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #231F20;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        #gameContainer {
            width: 960px;
            height: 600px;
        }
        #playButton {
            padding: 10px 20px;
            background-color: #ffffff;
            color: #231F20;
            border: none;
            cursor: pointer;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div id="gameContainer"></div>
    <button id="playButton" onclick="startGame()">Play Snow Rider 3D</button>

    <script>
        var gameInstance = null;

        function startGame() {
            document.getElementById('playButton').style.display = 'none';
            var gameContainer = document.getElementById('gameContainer');
            var script = document.createElement('script');
            script.src = "Build/UnityLoader.js"; // Adjust the path to your UnityLoader.js file
            script.onload = () => {
                gameInstance = UnityLoader.instantiate("gameContainer", "Build/SnowRider3D.json", {
                    dataUrl: "Build/SnowRider3D-gd-1.data.unityweb",
                    frameworkUrl: "Build/SnowRider3D-gd-1.wasm.framework.unityweb",
                    codeUrl: "Build/SnowRider3D-gd-1.wasm.code.unityweb",
                    memory: 268435456,
                    graphicsAPI: ["WebGL 2.0", "WebGL 1.0"],
                    webglContextAttributes: { preserveDrawingBuffer: false },
                    splashScreenStyle: "Dark",
                    backgroundColor: "#231F20"
                });
            };
            document.body.appendChild(script);
        }
    </script>
</body>
</html>
