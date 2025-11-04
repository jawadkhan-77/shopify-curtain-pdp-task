# 🪟 Custom Curtain Product Template (Shopify)

This custom Product Detail Page (PDP) dynamically calculates curtain prices using **Shopify metafields** and customer input.

---

## 💡 What It Does
- Lets customers enter a **width (cm)** and select a **drop** (curtain length).  
- Automatically calculates total price based on **custom metafields**.  
- Updates the price and “Add to Cart” button text in real time.  
- Keeps a clean, side-by-side layout (image left, details right).

---

## ⚙️ How It Works

### 1. Metafields Required
Add these metafields under the **`custom` namespace** for your product:

#### `custom_width_ranges` (JSON)
Defines how many panels are needed for each width range.
```json
[
  { "min": 0, "max": 100, "panels": 1 },
  { "min": 101, "max": 200, "panels": 2 },
  { "min": 201, "max": 300, "panels": 3 }
]
```

#### `custom_pricing_table` (JSON)
Defines prices for each drop and panel count.
```json
{
  "drop_100": [30, 60, 90],
  "drop_150": [40, 80, 120],
  "drop_200": [50, 100, 150]
}
```

---

## 🧮 How Price is Calculated

1. Customer enters a width → script finds which range it falls in.  
2. The range defines the number of **panels** (e.g., 2 panels).  
3. Customer selects a **drop** (e.g., 150 cm).  
4. Script looks up price in metafield: `pricingTable["drop_150"][panels - 1]`.  
5. Updates the display:
   ```
   💰 Total Price: $80
   Add to Cart — $80
   ```

---

## 🎨 Layout & Style
- 50% width for image, 50% for product info.  
- Responsive — stacks vertically below 768px.  
- Modern, minimal button styling with hover effect.

---

## 🧱 File Placement
Save this template as:
```
/templates/product.custom-curtain.liquid
```
Assign it to your product from the Shopify Admin → **Product → Theme template → custom-curtain**.

---

## 🧰 Tech Stack
- **Liquid** for metafield access  
- **Vanilla JavaScript** for dynamic pricing  
- **CSS Flexbox** for layout  

---

## ✅ Example Output
```
💰 Total Price: $updates without page reload 
[ Add to Cart — $updates without page reload ]
```


