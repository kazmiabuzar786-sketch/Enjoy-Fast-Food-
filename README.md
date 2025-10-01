# Enjoy-Fast-Food-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🍔 Enjoy Fast Food 🍟</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

<header>🍔🍟 Enjoy Fast Food 🍟🍔</header>

<div class="container">

<h2>Menu</h2>

<div class="menu-item">
    <span>🍔 Burger (₹20 each)</span>
    <input type="number" min="0" value="0" data-price="20" data-name="Burger">
</div>

<div class="menu-item">
    <span>🍜 Chowmein (₹20 per plate)</span>
    <input type="number" min="0" value="0" data-price="20" data-name="Chowmein">
</div>

<div class="menu-item">
    <span>🌯 Chowmein Roll (₹15 each)</span>
    <input type="number" min="0" value="0" data-price="15" data-name="Chowmein Roll">
</div>

<div class="menu-item">
    <span>🥟 Momos (₹10 for 3 pcs)</span>
    <input type="number" min="0" value="0" data-price="10" data-name="Momos">
</div>

<div class="menu-item">
    <span>🍞 Bread Pakoda (₹12 each)</span>
    <input type="number" min="0" value="0" data-price="12" data-name="Bread Pakoda">
</div>

<div class="menu-item">
    <span>🧆 Pakodi (₹40 per Pao)</span>
    <input type="number" min="0" value="0" data-price="40" data-name="Pakodi">
</div>

<div class="menu-item">
    <span>🍘 Namak Pare (₹40 per Pao)</span>
    <input type="number" min="0" value="0" data-price="40" data-name="Namak Pare">
</div>

<div class="menu-item">
    <span>🍬 Sweet Samosa (₹10 for 2 pcs)</span>
    <input type="number" min="0" value="0" data-price="10" data-name="Sweet Samosa">
</div>

<button id="generate">Generate WhatsApp Link</button>

<div id="orderSummary"></div>

</div>

<script>
const inputs = document.querySelectorAll('.menu-item input');
const orderSummary = document.getElementById('orderSummary');
const button = document.getElementById('generate');

button.addEventListener('click', () => {
    let total = 0;
    let orderText = '';
    inputs.forEach(input => {
        const qty = parseInt(input.value);
        if(qty > 0){
            const name = input.getAttribute('data-name');
            const price = parseInt(input.getAttribute('data-price'));
            const subtotal = qty * price;
            total += subtotal;
            orderText += `${name}: ${qty} × ₹${price} = ₹${subtotal}\n`;
        }
    });
    if(total === 0){
        alert("Please select at least one item!");
        return;
    }
    const customerName = prompt("Enter your name:");
    const phone = prompt("Enter your phone number:");
    const address = prompt("Enter delivery address:");
    if(!customerName || !phone || !address){
        alert("All details are required!");
        return;
    }
    orderText = `Order from ${customerName}\nPhone: ${phone}\nAddress: ${address}\n\nItems:\n${orderText}\nTotal = ₹${total}`;
    orderSummary.innerHTML = `<pre>${orderText}</pre>`;
    const encoded = encodeURIComponent(orderText);
    const waLink = `https://wa.me/918899630707?text=${encoded}`;
    orderSummary.innerHTML += `<p><a href="${waLink}" target="_blank">Place Order via WhatsApp</a></p>`;
});
</script>

</body>
</html>body {
    font-family: Arial, sans-serif;
    margin:0;
    padding:0;
    background:#fff8f0;
    color:#333;
}

header {
    background:#ff5733;
    color:#fff;
    padding:20px;
    text-align:center;
    font-size:1.8em;
}

.container {
    max-width:600px;
    margin:auto;
    padding:20px;
}

.menu-item {
    display:flex;
    justify-content:space-between;
    align-items:center;
    background:#fff;
    padding:15px;
    margin:10px 0;
    border-radius:8px;
    box-shadow:0 2px 5px rgba(0,0,0,0.1);
}

.menu-item input {
    width:60px;
    padding:5px;
    text-align:center;
}

#generate {
    margin-top:20px;
    padding:10px 20px;
    background:#25D366;
    color:#fff;
    border:none;
    border-radius:5px;
    cursor:pointer;
    font-weight:bold;
}

#generate:hover {
    background:#128C7E;
}

#orderSummary {
    margin-top:20px;
    padding:15px;
    background:#ffe6cc;
    border-radius:8px;
}
