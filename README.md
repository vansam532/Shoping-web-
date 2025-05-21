<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>My Shop</title>
  <style>
    body { font-family: Arial; margin: 0; }
    .product { border: 1px solid #ddd; padding: 10px; margin: 10px; width: 200px; }
    .add-to-cart { cursor: pointer; background: green; color: white; border: none; padding: 5px; }
  </style>
</head>
<body>
  <h1>My Shopping Store</h1>
  <div id="products"></div>
  <h2>Cart: <span id="cart-count">0</span></h2>

  <script>
    let cart = 0;
    const products = [
      { id: 1, name: "T-Shirt", price: 500 },
      { id: 2, name: "Shoes", price: 1200 },
      { id: 3, name: "Bag", price: 800 }
    ];

    function renderProducts() {
      const container = document.getElementById("products");
      products.forEach(p => {
        const div = document.createElement("div");
        div.className = "product";
        div.innerHTML = `
          <h3>${p.name}</h3>
          <p>Rs. ${p.price}</p>
          <button class="add-to-cart" onclick="addToCart(${p.id})">Add to Cart</button>
        `;
        container.appendChild(div);
      });
    }

    function addToCart(productId) {
      cart++;
      document.getElementById("cart-count").innerText = cart;
      alert("Item added to cart!");
    }

    renderProducts();
  </script>
</body>
</html>
