<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>TrueSim Workstation</title>
  <style>
    body {
      font-family: Tahoma, sans-serif;
      background-color: #f2f2f2;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #005b8d, #0082c8);
      padding: 10px;
      color: white;
      font-size: 1.2rem;
      font-weight: bold;
      display: flex;
      align-items: center;
    }
    header img {
      height: 28px;
      margin-right: 10px;
    }
    .toolbar {
      background: #c9dbee;
      padding: 5px;
      display: flex;
      gap: 10px;
      align-items: center;
      border-bottom: 2px solid #99bce4;
    }
    .toolbar button {
      background-color: #e7f0fb;
      border: 1px solid #7faad0;
      padding: 5px 10px;
      font-size: 0.9rem;
      cursor: pointer;
    }
    .status-bar {
      display: flex;
      justify-content: space-around;
      background-color: #d9e9f6;
      padding: 10px 0;
      border-bottom: 2px solid #a6c8e6;
    }
    .status-box {
      border-radius: 8px;
      padding: 20px 30px;
      font-weight: bold;
      color: white;
      font-size: 1.2rem;
    }
    .fire { background-color: #c00; }
    .pri2 { background-color: #00c2c7; }
    .supervisory { background-color: #f0b400; }
    .trouble { background-color: #e0b100; }

    .event-log {
      margin: 20px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.9rem;
    }
    th, td {
      padding: 8px;
      border: 1px solid #aaa;
      text-align: left;
    }
    th {
      background-color: #ddefff;
    }
    .flashing {
      animation: flash 1s infinite;
    }
    @keyframes flash {
      0% { opacity: 1; }
      50% { opacity: 0.2; }
      100% { opacity: 1; }
    }
    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      background-color: #dbe9fa;
      border: 1px solid #888;
      padding: 20px;
      width: 400px;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }
    .modal-header {
      font-weight: bold;
      margin-bottom: 10px;
    }
    .modal-buttons {
      margin-top: 15px;
      text-align: right;
    }
    .modal-buttons button {
      margin-left: 10px;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Tyco_SimplexGrinnell_logo.svg/2560px-Tyco_SimplexGrinnell_logo.svg.png" alt="Simplex Logo">
    TrueSite Workstation Simulator
  </header>

  <div class="toolbar">
    <select id="eventType">
      <option value="Fire">Fire</option>
      <option value="Trouble">Trouble</option>
      <option value="Supervisory">Supervisory</option>
    </select>
    <select id="zone">
      <option value="Zone 1 - Lobby">Zone 1 - Lobby</option>
      <option value="Zone 2 - Mechanical Room">Zone 2 - Mechanical Room</option>
      <option value="Zone 3 - Elevator Lobby Smoke Detector">Zone 3 - Elevator Lobby Smoke Detector</option>
      <option value="Zone 4 - 3rd Floor Kitchen Smoke Detector">Zone 4 - 3rd Floor Kitchen Smoke Detector</option>
      <option value="Zone 5 - 4th Floor Electrical Closet">Zone 5 - 4th Floor Electrical Closet</option>
      <option value="Zone 6 - Lobby Pull Station">Zone 6 - Lobby Pull Station</option>
      <option value="Zone 7 - Fire Pump Active">Zone 7 - Fire Pump Active</option>
      <option value="Zone 8 - Stair 3 Tamper">Zone 8 - Stair 3 Tamper</option>
      <option value="Zone 9 - Floor 2 Devices Bypassed">Zone 9 - Floor 2 Devices Bypassed</option>
      <option value="Zone 10 - Floor 10 Speakers">Zone 10 - Floor 10 Speakers</option>
    </select>
    <button onclick="triggerEvent()">Trigger</button>
    <button onclick="silence()">Silence</button>
    <button onclick="resetSystem()">Reset System</button>
  </div>

  <div class="status-bar">
    <div id="statusFire" class="status-box fire">Fire</div>
    <div id="statusPri2" class="status-box pri2">Pri2 Total=0</div>
    <div id="statusSupervisory" class="status-box supervisory">Supervisory</div>
    <div id="statusTrouble" class="status-box trouble">Trouble Total=0</div>
  </div>

  <div class="event-log">
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>Time</th>
          <th>Date</th>
          <th>Point Name</th>
          <th>Node</th>
          <th>Event</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody id="logTable"></tbody>
    </table>
  </div>

  <div id="ackModal" class="modal">
    <div class="modal-header">Acknowledge Box</div>
    <div id="modalContent"></div>
    <div class="modal-buttons">
      <button onclick="confirmAcknowledge()">Acknowledge</button>
      <button onclick="closeModal()">Close</button>
    </div>
  </div>

  <audio id="beep" src="https://actions.google.com/sounds/v1/alarms/alarm_clock.ogg"></audio>

  <script>
    const events = [];
    let eventCount = 0;
    let beepInterval = null;
    let currentEventIndex = null;

    function triggerEvent() {
      const troubleZones = [
        "Zone 7 - Fire Pump Active",
        "Zone 8 - Stair 3 Tamper",
        "Zone 9 - Floor 2 Devices Bypassed",
        "Zone 10 - Floor 10 Speakers"
      ];

      const fireZones = [
        "Zone 1 - Lobby",
        "Zone 2 - Mechanical Room",
        "Zone 3 - Elevator Lobby Smoke Detector",
        "Zone 4 - 3rd Floor Kitchen Smoke Detector",
        "Zone 5 - 4th Floor Electrical Closet",
        "Zone 6 - Lobby Pull Station"
      ];

      let selectedType;
      let selectedZone;

      if (Math.random() < 0.5) {
        selectedType = "Fire";
        selectedZone = fireZones[Math.floor(Math.random() * fireZones.length)];
      } else {
        selectedType = "Trouble";
        selectedZone = troubleZones[Math.floor(Math.random() * troubleZones.length)];
      }

      logEvent(selectedType, selectedZone);
    }

    function logEvent(type, zone) {
      const table = document.getElementById("logTable");
      const row = table.insertRow(0);
      const now = new Date();
      const time = now.toLocaleTimeString();
      const date = now.toDateString();
      const pointName = `1:M2-${40 + eventCount}`;

      eventCount++;
      row.insertCell(0).textContent = eventCount;
      row.insertCell(1).textContent = time;
      row.insertCell(2).textContent = date;
      row.insertCell(3).textContent = pointName;
      row.insertCell(4).textContent = "(NODE 1)";
      row.insertCell(5).textContent = `${zone} - ${type.toUpperCase()}`;
      row.insertCell(6).textContent = "UNACKNOWLEDGED";

      row.classList.add("flashing");
      row.style.cursor = "pointer";
      const eventIndex = events.length;
      row.onclick = () => showModal(eventIndex);

      events.push({ row, type, acknowledged: false, time, date, zone, pointName });

      updateStatusCounts();
      startBeeping();
    }

    function startBeeping() {
      if (!beepInterval) {
        beepInterval = setInterval(() => {
          const hasUnack = events.some(e => !e.acknowledged);
          if (hasUnack) document.getElementById("beep").play();
        }, 1000);
      }
    }

    function stopBeeping() {
      clearInterval(beepInterval);
      beepInterval = null;
    }

    function showModal(index) {
      if (index < 0 || index >= events.length) return;
      currentEventIndex = index;
      const e = events[index];
      const modal = document.getElementById("ackModal");
      document.getElementById("modalContent").innerHTML = `
        <p><strong>(NODE 1)</strong></p>
        <p>${e.time}<br>${e.date} - ${e.pointName}</p>
        <p>${e.zone.toUpperCase()} - ${e.type.toUpperCase()}</p>
        <textarea rows="3" style="width: 100%;">Default ${e.type} State Message</textarea>
        <p>Press Button to Acknowledge point</p>
      `;
      modal.style.display = "block";
    }

    function closeModal() {
      document.getElementById("ackModal").style.display = "none";
    }

    function confirmAcknowledge() {
      if (currentEventIndex === null || currentEventIndex >= events.length) return;
      const e = events[currentEventIndex];
      e.row.cells[6].textContent = "ACKNOWLEDGED";
      e.row.classList.remove("flashing");
      e.acknowledged = true;
      closeModal();

      updateStatusCounts();

      if (!events.some(e => !e.acknowledged)) stopBeeping();
    }

    function silence() {
      console.log("Silenced");
    }

    function resetSystem() {
      const table = document.getElementById("logTable");
      while (table.firstChild) table.removeChild(table.firstChild);
      events.length = 0;
      eventCount = 0;
      stopBeeping();
      updateStatusCounts();
    }

    function updateStatusCounts() {
      const pri2 = events.length;
      const fireUnack = events.some(e => e.type === "Fire" && !e.acknowledged);
      const troubleUnack = events.some(e => e.type === "Trouble" && !e.acknowledged);
      const supervisoryUnack = events.some(e => e.type === "Supervisory" && !e.acknowledged);
      const fire = events.filter(e => e.type === "Fire").length;
      const trouble = events.filter(e => e.type === "Trouble").length;

      document.getElementById("statusPri2").textContent = `Pri2 Total=${pri2}`;
      document.getElementById("statusTrouble").textContent = `Trouble Total=${trouble}`;

      document.getElementById("statusFire").classList.toggle("flashing", fireUnack);
      document.getElementById("statusSupervisory").classList.toggle("flashing", supervisoryUnack);
      document.getElementById("statusTrouble").classList.toggle("flashing", troubleUnack);
    }
  </script>
</body>
</html>
