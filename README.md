<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Kéo Tâm FF</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #111;
      color: #0f0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    button {
      padding: 10px 20px;
      font-size: 18px;
      margin-top: 20px;
      cursor: pointer;
    }

    .status {
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>Kéo Tâm Free Fire (Demo)</h1>
  <button id="toggleBtn">Bật Kéo Tâm</button>
  <div class="status" id="status">Trạng thái: Tắt</div>

  <script>
    let isActive = false;
    let recoilInterval;

    const toggleBtn = document.getElementById('toggleBtn');
    const status = document.getElementById('status');

    // Bật/Tắt chế độ kéo tâm
    toggleBtn.addEventListener('click', () => {
      isActive = !isActive;
      status.textContent = 'Trạng thái: ' + (isActive ? 'Bật' : 'Tắt');
      toggleBtn.textContent = isActive ? 'Tắt Kéo Tâm' : 'Bật Kéo Tâm';
    });

    // Sử dụng mousemove liên tục khi giữ chuột trái
    document.addEventListener('mousedown', (e) => {
      if (isActive && e.button === 0) { // Chuột trái
        recoilInterval = setInterval(() => {
          simulateMouseMove(0, 3); // Di chuyển chuột xuống 3px
        }, 15); // mỗi 15ms
      }
    });

    document.addEventListener('mouseup', () => {
      clearInterval(recoilInterval);
    });

    // Hàm giả lập di chuyển chuột
    function simulateMouseMove(x, y) {
      // Không thể di chuyển chuột thật bằng JS do giới hạn trình duyệt
      // Chỉ hoạt động nếu build thành app desktop (Electron hoặc AutoHotKey)
      console.log(`Di chuyển chuột: ${x}, ${y}`);
    }

  </script>
</body>
</html>
