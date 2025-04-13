# wolf-store-landing
from zipfile import ZipFile
import os

# Directory structure for the landing page (simulated with basic content)
landing_page_files = {
    "index.html": """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Wolf Store - Shop Anything</title>
  <link rel="stylesheet" href="style.css"/>
</head>
<body>
  <header>
    <h1>Wolf Store</h1>
    <p>Your Marketplace. Your Rules.</p>
    <a href="#" class="download-btn">Download the App</a>
    <p class="promo">Use code <strong>WOLF10</strong> for 10% off your first order!</p>
  </header>
  <section class="features">
    <h2>Why Shop With Us?</h2>
    <ul>
      <li>Cash on Delivery</li>
      <li>Fast Shipping</li>
      <li>Order Tracking</li>
    </ul>
  </section>
  <footer>
    <p>© 2025 Wolf Store. All rights reserved.</p>
  </footer>
</body>
</html>
""",
    "style.css": """
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background: linear-gradient(to bottom right, #111, #e50914);
  color: white;
  text-align: center;
}
header {
  padding: 50px 20px;
}
.download-btn {
  display: inline-block;
  margin: 20px auto;
  padding: 12px 30px;
  background: white;
  color: #e50914;
  text-decoration: none;
  font-weight: bold;
  border-radius: 5px;
}
.promo {
  margin-top: 10px;
  font-size: 16px;
  color: #ffaaaa;
}
.features {
  padding: 40px 20px;
}
footer {
  padding: 20px;
  background: #000;
  color: #888;
}
"""
}

# Save the files to a temp directory
temp_dir = "/mnt/data/wolf_store_landing_page"
os.makedirs(temp_dir, exist_ok=True)

for filename, content in landing_page_files.items():
    with open(os.path.join(temp_dir, filename), "w") as f:
        f.write(content.strip())

# Create a ZIP archive of the landing page
zip_path = "/mnt/data/wolf_store_landing_page.zip"
with ZipFile(zip_path, "w") as zipf:
    for filename in landing_page_files:
        zipf.write(os.path.join(temp_dir, filename), arcname=filename)

zip_path
