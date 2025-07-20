<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Dashboard</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; background: #f4f4f4;}
    .dashboard { background: #fff; padding: 20px; border-radius: 8px; max-width: 500px; margin: auto;}
    h2 { color: #333; }
    ul { list-style-type: none; padding: 0; }
    li { background: #e9e9e9; margin-bottom: 10px; padding: 10px; border-radius: 5px;}
    .input-row { margin-top: 15px; display: flex; gap: 10px; }
    input[type="text"] { flex: 1; padding: 8px; border-radius: 4px; border: 1px solid #ccc; }
    button { padding: 8px 14px; border: none; border-radius: 4px; background: #007bff; color: #fff; cursor: pointer;}
    button:hover { background: #0056b3;}
  </style>
</head>
<body>
  <div class="dashboard">
    <h2>Announcements</h2>
    <ul id="announcementList">
      <li><strong>2025-07-20:</strong> Welcome to the new semester!</li>
      <li><strong>2025-07-18:</strong> Don’t forget to submit your assignments by Friday.</li>
    </ul>
    <div class="input-row">
      <input type="text" id="announcementInput" placeholder="Type new announcement..." />
      <button onclick="addAnnouncement()">Add</button>
    </div>
  </div>
  <script>
    function addAnnouncement() {
      const input = document.getElementById('announcementInput');
      const list = document.getElementById('announcementList');
      if (input.value.trim() !== '') {
        const date = new Date().toISOString().split('T')[0];
        const li = document.createElement('li');
        li.innerHTML = `<strong>${date}:</strong> ${input.value}`;
        list.insertBefore(li, list.firstChild);
        input.value = '';
      }
    }
  </script>
</body>
</html>
