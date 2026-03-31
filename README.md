# Shop.shoes.SNG
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sneaker Store</title>

<style>
body {
    margin: 0;
    font-family: Arial;
    background: #111;
    color: white;
}

/* HEADER */
header {
    display: flex;
    justify-content: space-between;
    padding: 15px 30px;
    background: black;
}

.logo {
    font-size: 22px;
    font-weight: bold;
}

.cart-btn {
    cursor: pointer;
}

/* PRODUCTS */
.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.card {
    background: #1c1c1c;
    margin: 15px;
    padding: 15px;
    width: 220px;
    border-radius: 10px;
    text-align: center;
}

.card img {
    width: 100%;
}

button {
    background: #00c853;
    border: none;
    padding: 10px;
    color: white;
    cursor: pointer;
    border-radius: 5px;
}

button:hover {
    background: #009624;
}

/* CART */
#cart {
    position: fixed;
    right: -400px;
    top: 0;
    width: 300px;
    height: 100%;
    background: #222;
    padding: 20px;
    transition: 0.3s;
}

#cart.active {
    right: 0;
}

.cart-item {
    margin-bottom: 10px;
}

/* PAYMENT */
#payment {
    display: none;
    text-align: center;
    padding: 20px;
}

input {
    padding: 10px;
    margin: 5px;
    width: 200px;
}

/* MOBILE */
@media (max-width: 600px) {
    .card {
        width: 90%;
    }
}
</style>
</head>

<body>

<header>
<div class="logo">🔥 SneakerShop</div>
<div class="cart-btn" onclick="toggleCart()">🛒 Корзина (<span id="count">0</span>)</div>
</header>

<div class="container">

<div class="card">
<img src="https://via.placeholder.com/200">
<h3>Nike Air Max</h3>
<p>120$</p>
<button onclick="addToCart('Nike Air Max',120)">Добавить</button>
</div>

<div class="card">
<img src="https://via.placeholder.com/200">
<h3>Adidas Ultraboost</h3>
<p>150$</p>
<button onclick="addToCart('Adidas Ultraboost',150)">Добавить</button>
</div>

<div class="card">
<img src="https://via.placeholder.com/200">
<h3>Puma Runner</h3>
<p>90$</p>
<button onclick="addToCart('Puma Runner',90)">Добавить</button>
</div>

</div>

<!-- CART -->
<div id="cart">
<h2>🛒 Корзина</h2>
<div id="items"></div>
<p>Итого: <span id="total">0</span>$</p>
<button onclick="checkout()">Оформить</button>
</div>

<!-- PAYMENT -->
<div id="payment">
<h2>💳 Оплата</h2>
<p>Введите данные карты</p>

<input placeholder="Номер карты"><br>
<input placeholder="MM/YY"><br>
<input placeholder="CVV"><br><br>

<button onclick="pay()">Оплатить</button>
</div>

<script>
let cart = [];
let total = 0;

function addToCart(name, price) {
    cart.push({name, price});
    total += price;
    updateCart();
}

function updateCart() {
    document.getElementById("items").innerHTML = "";
    cart.forEach(item => {
        document.getElementById("items").innerHTML += 
            `<div class="cart-item">${item.name} - ${item.price}$</div>`;
    });

    document.getElementById("total").innerText = total;
    document.getElementById("count").innerText = cart.length;
}

function toggleCart() {
    document.getElementById("cart").classList.toggle("active");
}

function checkout() {
    document.getElementById("payment").style.display = "block";
}

function pay() {
    alert("✅ Оплата прошла успешно (демо)");
    cart = [];
    total = 0;
    updateCart();
}
</script>

</body>
