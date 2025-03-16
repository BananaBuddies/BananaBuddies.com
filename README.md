# BananaBuddies.com
Order bracelets and Necklaces here. Made by the 3 Banana Buddies, for you, for town.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Customize Jewelry</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 50px;
    }
    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
    }
    form {
      display: none;
      margin-top: 20px;
    }
    input, textarea {
      display: block;
      margin: 10px auto;
      padding: 10px;
      width: 80%;
      max-width: 400px;
    }
  </style>
</head>
<body>
  <h1>Customize Your Jewelry</h1>
  <button onclick="showForm('bracelet')">Customize your bracelet</button>
  <button onclick="showForm('necklace')">Customize your necklace</button>
  
  <form id="customForm" onsubmit="sendOrder(event)">
    <input type="hidden" id="jewelryType" name="jewelryType">
    <input type="text" id="colors" name="colors" placeholder="Enter colors in a specific order" required>
    <input type="number" id="wristSize" name="wristSize" placeholder="Wrist size (inches)" style="display: none;">
    <textarea id="address" name="address" placeholder="Enter your address or meeting place" required></textarea>
    <button type="submit">Submit Order</button>
  </form>

  <script>
    function showForm(type) {
      document.getElementById('customForm').style.display = 'block';
      document.getElementById('jewelryType').value = type;
      if (type === 'bracelet') {
        document.getElementById('wristSize').style.display = 'block';
      } else {
        document.getElementById('wristSize').style.display = 'none';
      }
    }

    function sendOrder(event) {
      event.preventDefault();
      const form = document.getElementById('customForm');
      const formData = new FormData(form);
      const data = {
        jewelryType: formData.get('jewelryType'),
        colors: formData.get('colors'),
        wristSize: formData.get('wristSize'),
        address: formData.get('address')
      };

      const email = 'lcitkatl@gmail.com';
      const subject = `New ${data.jewelryType} order`;
      const body = `Colors: ${data.colors}\nWrist Size: ${data.wristSize}\nAddress: ${data.address}`;

      window.location.href = `mailto:${email}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
    }
  </script>
</body>
</html>
