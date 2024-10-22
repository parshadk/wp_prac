Creating a dynamic shopping cart using JavaScript allows users to add, remove, and modify items in real time. Below is a complete example demonstrating how to implement a simple shopping cart for an online store.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `shopping-cart.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the shopping cart, which includes items that can be added to the cart, a cart display, and functionality for managing items.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Cart Example</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        h2 {
            text-align: center;
        }

        .item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid #ccc;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid #ccc;
        }

        input[type="number"] {
            width: 50px;
            margin-left: 10px;
        }

        .total {
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Online Store</h2>

        <div id="items">
            <div class="item">
                <span>Product 1 - $10</span>
                <button onclick="addToCart('Product 1', 10)">Add to Cart</button>
            </div>
            <div class="item">
                <span>Product 2 - $15</span>
                <button onclick="addToCart('Product 2', 15)">Add to Cart</button>
            </div>
            <div class="item">
                <span>Product 3 - $20</span>
                <button onclick="addToCart('Product 3', 20)">Add to Cart</button>
            </div>
        </div>

        <h2>Your Cart</h2>
        <div id="cart"></div>
        <div class="total" id="total">Total: $0</div>
    </div>

    <script>
        const cartItems = {};

        function addToCart(productName, productPrice) {
            if (!cartItems[productName]) {
                cartItems[productName] = { price: productPrice, quantity: 1 };
            } else {
                cartItems[productName].quantity++;
            }
            renderCart();
        }

        function removeFromCart(productName) {
            delete cartItems[productName];
            renderCart();
        }

        function updateQuantity(productName, quantity) {
            if (quantity <= 0) {
                removeFromCart(productName);
            } else {
                cartItems[productName].quantity = quantity;
            }
            renderCart();
        }

        function renderCart() {
            const cart = document.getElementById("cart");
            cart.innerHTML = ""; // Clear the current cart display
            let total = 0;

            for (const productName in cartItems) {
                const item = cartItems[productName];
                total += item.price * item.quantity;

                const cartItem = document.createElement("div");
                cartItem.className = "cart-item";
                cartItem.innerHTML = `
                    <span>${productName} - $${item.price} x <input type="number" value="${item.quantity}" min="0" onchange="updateQuantity('${productName}', this.value)"></span>
                    <button onclick="removeFromCart('${productName}')">Remove</button>
                `;
                cart.appendChild(cartItem);
            }

            document.getElementById("total").innerText = `Total: $${total}`;
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The shopping cart is contained within a `<div class="container">`, which includes available products and the cart itself.
   - Each product has a button that allows users to add it to the cart.

2. **CSS Styles**:
   - Basic styles are applied to create a clean and user-friendly layout for the shopping cart and products.

3. **JavaScript Functionality**:
   - **`addToCart(productName, productPrice)`**: This function adds a product to the cart. If the product already exists, it increases the quantity.
   - **`removeFromCart(productName)`**: This function removes a product from the cart.
   - **`updateQuantity(productName, quantity)`**: This function updates the quantity of a product in the cart. If the quantity is set to 0, it removes the item from the cart.
   - **`renderCart()`**: This function updates the cart display and calculates the total price. It dynamically creates cart items and inputs for quantity.

### 3. Open Your Shopping Cart in a Browser

To see your shopping cart in action, open the `shopping-cart.html` file in a web browser. You should be able to add items to the cart, change their quantities, and remove them as needed.

### Conclusion

You’ve successfully created a dynamic shopping cart for an online store using JavaScript. This example allows users to interact with the cart in real time, making it a great starting point for a more comprehensive e-commerce application. You can further enhance this shopping cart by adding features like saving to local storage, applying discounts, or integrating with a backend system for checkout functionality. Enjoy building your online store!
