<!-- HEAD kısmı -->
<script src="https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.js"></script>
<link href="https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.css" rel="stylesheet" />

<!-- BODY kısmı -->
<button class="snipcart-add-item"
  data-item-id="urun1"
  data-item-price="50"
  data-item-url="https://maglyshop.github.io/my-shop"
  data-item-description="Harika ürün 1"
  data-item-name="Ürün 1">
  Sepete Ekle
</button>

<!-- Snipcart Sepet -->
<div hidden id="snipcart" data-api-key="GERÇEK_API_ANAHTARINIZ"></div><!DOCTYPE html>
<html>
<head>
  <title>Kolay E-Ticaret</title>
  <script src="https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.js"></script>
  <link href="https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.css" rel="stylesheet" />
</head>
<body>

  <h1>Ürünlerimiz</h1>

  <div>
    <h2>Ürün 1</h2>
    <p>Fiyat: 50₺</p>
    <button class="snipcart-add-item"
      data-item-id="urun1"
      data-item-price="50"
      data-item-url="https://kullaniciadi.github.io/my-shop"
      data-item-description="Harika ürün 1"
      data-item-name="Ürün 1">
      Sepete Ekle
    </button>
  </div>

  <div>
    <h2>Ürün 2</h2>
    <p>Fiyat: 80₺</p>
    <button class="snipcart-add-item"
      data-item-id="urun2"
      data-item-price="80"
      data-item-url="https://kullaniciadi.github.io/my-shop"
      data-item-description="Harika ürün 2"
      data-item-name="Ürün 2">
      Sepete Ekle
    </button>
  </div>

  <!-- Snipcart Sepet -->
  <div hidden id="snipcart" data-api-key="SNIPCART_API_KEY"></div>

</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <title>Ücretsiz E-Ticaret</title>
  <script src="https://js.stripe.com/v3/"></script>
  <style>
    body { font-family: Arial, sans-serif; max-width: 600px; margin: 30px auto; }
    .product { border: 1px solid #ddd; padding: 15px; margin-bottom: 20px; }
    button { background-color: #6772e5; color: white; border: none; padding: 10px 15px; cursor: pointer; }
  </style>
</head>
<body>

  <h1>Mağazam</h1>

  <div class="product">
    <h2>Ürün 1</h2>
    <p>Fiyat: 100₺</p>
    <button id="checkout-button-1">Satın Al</button>
  </div>

  <div class="product">
    <h2>Ürün 2</h2>
    <p>Fiyat: 200₺</p>
    <button id="checkout-button-2">Satın Al</button>
  </div>

  <script>
    // Stripe Publishable key (kendi anahtarını koy)
    const stripe = Stripe("pk_test_XXXXXXXXXXXXXXXXXXXXXXXX");

    // Ürün 1 için ödeme
    const checkoutButton1 = document.getElementById("checkout-button-1");
    checkoutButton1.addEventListener("click", function () {
      fetch("/create-checkout-session", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ productId: 1 }),
      })
      .then((res) => res.json())
      .then((session) => {
        return stripe.redirectToCheckout({ sessionId: session.id });
      })
      .then((result) => {
        if (result.error) {
          alert(result.error.message);
        }
      })
      .catch((error) => console.error("Error:", error));
    });

    // Ürün 2 için ödeme (aynı şekilde)
    const checkoutButton2 = document.getElementById("checkout-button-2");
    checkoutButton2.addEventListener("click", function () {
      fetch("/create-checkout-session", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ productId: 2 }),
      })
      .then((res) => res.json())
      .then((session) => {
        return stripe.redirectToCheckout({ sessionId: session.id });
      })
      .then((result) => {
        if (result.error) {
          alert(result.error.message);
        }
      })
      .catch((error) => console.error("Error:", error));
    });
  </script>

</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <title>Bedava E-Ticaret</title>
  <style>
    body { font-family: Arial, sans-serif; }
    .product { border: 1px solid #ccc; padding: 10px; margin: 10px; }
    button { background: green; color: white; border: none; padding: 10px; cursor: pointer; }
  </style>
</head>
<body>
  <h1>Mağazam</h1>
  
  <div class="product">
    <h2>Ürün 1</h2>
    <p>Fiyat: 100₺</p>
    <button onclick="alert('Satın alma işlemi yakında ekleniyor')">Satın Al</button>
  </div>
  
  <div class="product">
    <h2>Ürün 2</h2>
    <p>Fiyat: 200₺</p>
    <button onclick="alert('Satın alma işlemi yakında ekleniyor')">Satın Al</button>
  </div>
  
</body>
</html>
