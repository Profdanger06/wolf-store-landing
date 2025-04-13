# wolf-store-landing
from zipfile import ZipFile
import os

# Define updated HTML and CSS content for a stylish black & red Wolf Store landing page
updated_files = {
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
  <div class="container">
    <header>
      <h1 class="logo">Wolf Store</h1>
      <p class="tagline">Your Marketplace. Your Rules.</p>
      <a href="#" class="download-btn">Download the App</a>
      <p class="promo">Use code <strong>WOLF10</strong> for 10% off your first order!</p>
    </header>

    <section class="features">
      <h2>Why Shop With Us?</h2>
      <ul>
        <li>Cash on Delivery</li>
        <li>Fast Worldwide Shipping</li>
        <li>Live Order Tracking</li>
        <li>All Products, One App</li>
      </ul>
    </section>

    <footer>
      <p>© 2025 Wolf Store. All rights reserved.</p>
    </footer>
  </div>
</body>
</html>
""",
    "style.css": """
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #0d0d0d;
  color: #fff;
}

.container {
  max-width: 960px;
  margin: auto;
  padding: 20px;
  text-align: center;
}

header {
  padding: 60px 20px 40px;
  background: linear-gradient(135deg, #000, #c00);
  border-radius: 8px;
}

.logo {
  font-size: 48px;
  color: white;
  margin-bottom: 10px;
}

.tagline {
  font-size: 20px;
  color: #ddd;
  margin-bottom: 20px;
}

.download-btn {
  display: inline-block;
  padding: 14px 30px;
  background-color: #fff;
  color: #c00;
  font-weight: bold;
  text-decoration: none;
  border-radius: 6px;
  transition: background-color 0.3s ease;
}

.download-btn:hover {
  background-color: #eee;
}

.promo {
  margin-top: 15px;
  font-size: 16px;
  color: #ffcccc;
}

.features {
  padding: 40px 20px;
}

.features h2 {
  margin-bottom: 20px;
  color: #ff4444;
}

.features ul {
  list-style: none;
  padding: 0;
  font-size: 18px;
}

.features li {
  margin: 10px 0;
}

footer {
  padding: 20px 10px;
  font-size: 14px;
  color: #aaa;
  border-top: 1px solid #222;
  margin-top: 40px;
}
"""
}

# Create directory and save updated files
updated_dir = "/mnt/data/wolf_store_rebuild"
os.makedirs(updated_dir, exist_ok=True)

for filename, content in updated_files.items():
    with open(os.path.join(updated_dir, filename), "w") as f:
        f.write(content.strip())

# Zip the project
zip_file_path = "/mnt/data/wolf_store_rebuild.zip"
with ZipFile(zip_file_path, "w") as zipf:
    for filename in updated_files:
        zipf.write(os.path.join(updated_dir, filename), arcname=filename)

zip_file_path
