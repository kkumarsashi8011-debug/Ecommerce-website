# Ecommerce-website
Shopsy is a modern and responsive e-commerce website built using HTML, CSS, and JavaScript. It provides a smooth shopping experience where users can browse products, view details, and add items to their cart in real-time.
<!-- =========================
Shopsy - Enhanced E-commerce Website
Now with MORE products + REAL images
========================= -->

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shopsy</title>

  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
    }

    header {
      background: #111;
      color: white;
      padding: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    header h1 { color: #00ffcc; }

    nav a {
      color: white;
      margin: 0 10px;
      text-decoration: none;
      font-weight: bold;
    }

    .container {
      padding: 20px;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }

    .card {
      background: white;
      padding: 15px;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.1);
      text-align: center;
      transition: transform 0.2s;
    }

    .card:hover { transform: scale(1.05); }

    .card img {
      width: 100%;
      height: 160px;
      object-fit: cover;
      border-radius: 10px;
    }

    .card h3 { margin: 10px 0; }

    .card button {
      background: #00ffcc;
      border: none;
      padding: 10px;
      color: black;
      cursor: pointer;
      border-radius: 6px;
      margin-top: 8px;
    }

    .cart {
      position: fixed;
      right: 0;
      top: 0;
      width: 300px;
      height: 100%;
      background: white;
      box-shadow: -2px 0 10px rgba(0,0,0,0.2);
      padding: 15px;
      overflow-y: auto;
    }

    footer {
      text-align: center;
      padding: 15px;
      background: #111;
      color: white;
      margin-top: 20px;
    }
  </style>
</head>

<body>

<header>
  <h1>Shopsy</h1>
  <nav>
    <a href="#">Home</a>
    <a href="#">Products</a>
    <a href="#">Cart (<span id="cart-count">0</span>)</a>
  </nav>
</header>

<div class="container">
  <h2>Featured Products</h2>
  <div class="products" id="product-list"></div>
</div>

<div class="cart">
  <h2>Your Cart</h2>
  <ul id="cart-items"></ul>
  <h3>Total: ₹<span id="total">0</span></h3>
</div>

<footer>
  <p>© 2026 Shopsy | E-commerce Website</p>
</footer>

<script>
  const products = [
    { id: 1, name: "Wireless Headphones", price: 1499, img: "https://images.unsplash.com/photo-1518443895914-6f03f3b5a3c4" },
    { id: 2, name: "Running Shoes", price: 2499, img: "https://images.unsplash.com/photo-1528701800489-20be3c0b9a0c" },
    { id: 3, name: "Smart Watch", price: 1999, img: "https://images.unsplash.com/photo-1517433456452-f9633a875f6f" },
    { id: 4, name: "Smartphone", price: 12999, img: "https://images.unsplash.com/photo-1511707171634-5f897ff02aa9" },
    { id: 5, name: "Backpack", price: 899, img: "https://images.unsplash.com/photo-1503342217505-b0a15ec3261c" },
    { id: 6, name: "Sunglasses", price: 699, img: "https://images.unsplash.com/photo-1511499767150-a48a237f0083" },
    { id: 7, name: "Gaming Mouse", price: 1299, img: "https://images.unsplash.com/photo-1587202372775-e229f172b9d7" },
    { id: 8, name: "Laptop", price: 45999, img: "https://images.unsplash.com/photo-1517336714731-489689fd1ca8" }
  ];

  let cart = [];

  const productList = document.getElementById("product-list");
  const cartItems = document.getElementById("cart-items");
  const totalDisplay = document.getElementById("total");
  const cartCount = document.getElementById("cart-count");

  function renderProducts() {
    productList.innerHTML = "";

    products.forEach(product => {
      const div = document.createElement("div");
      div.classList.add("card");

      div.innerHTML = `
        <img src="${product.img}?auto=format&fit=crop&w=400&q=80">
        <h3>${product.name}</h3>
        <p>₹${product.price}</p>
        <button onclick="addToCart(${product.id})">Add to Cart</button>
      `;

      productList.appendChild(div);
    });
  }

  function addToCart(id) {
    const product = products.find(p => p.id === id);
    cart.push(product);
    updateCart();
  }

  function updateCart() {
    cartItems.innerHTML = "";
    let total = 0;

    cart.forEach(item => {
      const li = document.createElement("li");
      li.textContent = `${item.name} - ₹${item.price}`;
      cartItems.appendChild(li);
      total += item.price;
    });

    totalDisplay.textContent = total;
    cartCount.textContent = cart.length;
  }

  renderProducts();
</script>

</body>
</html>
