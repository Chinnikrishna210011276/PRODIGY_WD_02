<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Stopwatch</title>
    <style>
      body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background-color: #e0f7fa;
        margin: 0;
      }

      .container {
        text-align: center;
        background-color: #ffffff;
        padding: 30px;
        border-radius: 15px;
        box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
      }

      .stopwatch {
        margin: 0 auto;
        max-width: 300px;
      }

      .time-display {
        font-size: 4em;
        margin-bottom: 30px;
        font-weight: 600;
        color: #00796b;
      }

      .buttons {
        display: flex;
        justify-content: center;
        gap: 15px;
      }

      .buttons button {
        background-color: #00796b;
        color: #ffffff;
        border: none;
        padding: 15px 25px;
        font-size: 1.2em;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s;
      }

      .buttons button:hover {
        background-color: #00695c;
      }

      .buttons button:active {
        background-color: #004d40;
      }

      .laps {
        max-height: 200px;
        overflow-y: auto;
        text-align: left;
        padding: 15px;
        margin-top: 20px;
        background-color: #e0f2f1;
        border-radius: 10px;
        box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
      }

      .laps div {
        padding: 10px;
        border-bottom: 1px solid #b2dfdb;
      }

      .laps div:last-child {
        border-bottom: none;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="stopwatch">
        <h1>Stopwatch</h1>
        <div class="time-display" id="time-display">00:00:00.00</div>
        <div class="buttons">
          <button id="start-pause-button" onclick="startPause()">Start</button>
          <button id="reset-button" onclick="reset()">Reset</button>
          <button id="lap-button" onclick="lap()">Lap</button>
        </div>
        <div class="laps" id="laps"></div>
      </div>
    </div>
    <script>
      let startTime;
      let updatedTime;
      let difference;
      let timerID;
      let running = false;
      let lapCounter = 0;

      const startPauseButton = document.getElementById("start-pause-button");
      const resetButton = document.getElementById("reset-button");
      const lapButton = document.getElementById("lap-button");
      const timeDisplay = document.getElementById("time-display");
      const laps = document.getElementById("laps");

      function startPause() {
        if (!running) {
          startTime = new Date().getTime() - (difference || 0);
          timerID = setInterval(updateTime, 10);
          startPauseButton.textContent = "Pause";
          running = true;
        } else {
          clearInterval(timerID);
          difference = new Date().getTime() - startTime;
          startPauseButton.textContent = "Start";
          running = false;
        }
      }

      function reset() {
        clearInterval(timerID);
        startTime = null;
        difference = null;
        running = false;
        lapCounter = 0;
        timeDisplay.textContent = "00:00:00.00";
        startPauseButton.textContent = "Start";
        laps.innerHTML = "";
      }

      function lap() {
        if (running) {
          const lapTime = new Date().getTime() - startTime;
          const formattedLapTime = formatTime(lapTime);
          const lapElement = document.createElement("div");
          lapElement.textContent = `Lap ${++lapCounter}: ${formattedLapTime}`;
          laps.appendChild(lapElement);
        }
      }

      function updateTime() {
        updatedTime = new Date().getTime();
        difference = updatedTime - startTime;
        timeDisplay.textContent = formatTime(difference);
      }

      function formatTime(ms) {
        const milliseconds = parseInt((ms % 1000) / 10);
        const seconds = Math.floor((ms / 1000) % 60);
        const minutes = Math.floor((ms / (1000 * 60)) % 60);
        const hours = Math.floor((ms / (1000 * 60 * 60)) % 24);

        return `${pad(hours)}:${pad(minutes)}:${pad(seconds)}.${pad(
          milliseconds,
          2
        )}`;
      }

      function pad(number, digits = 2) {
        return number.toString().padStart(digits, "0");
      }
    </script>
  </body>
</html>
