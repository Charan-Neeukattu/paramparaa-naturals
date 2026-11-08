# Paramparaa Naturals 🌿

> Fresh, chemical-free organic produce & groceries online ordering portal.

**Paramparaa Naturals** is a lightweight, responsive single-page web application designed for weekly household ordering of farm-fresh organic produce. It provides a simple, frictionless shopping experience tailored for weekly orders, featuring real-time cart calculation, fractional quantity adjustments (1/4 kg steps), category-based filtering, and serverless email order dispatching.

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Running Locally](#running-locally)
- [Configuration & Customization](#-configuration--customization)
  - [1. Order Form & Email (Web3Forms)](#1-order-form--email-web3forms)
  - [2. Products & Categories](#2-products--categories)
  - [3. Dynamic Price Overrides (`prices.json`)](#3-dynamic-price-overrides-pricesjson)
  - [4. Weekly Nutrition Notes](#4-weekly-nutrition-notes)
  - [5. Order Window & Delivery Schedule](#5-order-window--delivery-schedule)
  - [6. Product Images](#6-product-images)
- [Deployment](#-deployment)
- [Contact & Store Information](#-contact--store-information)
- [License](#-license)

---

## ✨ Features

- **Intuitive Weekly Order Window**:
  - Highlights weekly order cut-off times and delivery schedules directly in header callouts.
- **Shop by Category**:
  - Organizes items into categories like *Desi Seed Vegetables*, *Leafy Vegetables*, *Veggies*, *Creeper Veggies*, *Roots & Tubers*, *Salad Veggies*, *Fruits*, *Desi Cow Dairy Products*, and more.
  - Sticky mobile category chips and desktop navigation sidebar for smooth scrolling.
- **Smart Quantity Steps**:
  - Supports unit-based counters (e.g., `pc`, `Bunch`) as well as fractional weights (`kg` items increment in `1/4 kg` / 250g steps).
- **Responsive Dual-Mode Cart**:
  - **Desktop**: Persistent sticky sidebar showing item breakdown and running subtotal.
  - **Mobile**: Floating bottom cart bar that expands into a bottom sheet drawer.
- **Order Review Modal**:
  - Allows customers to review items, quantities, estimated total, and delivery notes before submitting.
- **Serverless Order Submission**:
  - Powered by [Web3Forms](https://web3forms.com/)—sends completed orders straight to the store's email inbox without requiring a backend server or database.
- **Dynamic Price Override Support**:
  - Automatically loads and overrides item prices at runtime using `prices.json`.
- **Weekly Nutrition Notes**:
  - Features science-backed dietary guidance and nutrition coaching tips from certified coaches.
- **Zero External Build Tools Needed**:
  - Standard HTML5, CSS (via Tailwind CDN), and vanilla JavaScript. No `npm install` or bundlers required.

---

## 🛠 Tech Stack

- **Markup & Layout**: HTML5
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) (CDN)
- **Typography**: [Google Fonts (Inter)](https://fonts.google.com/specimen/Inter)
- **Logic**: Vanilla JavaScript (ES6+, Async/Await, DOM APIs)
- **Form Delivery**: [Web3Forms API](https://web3forms.com/)

---

## 📁 Project Structure

```text
Paramparaa Naturals/
├── images/             # Product photography (named following item slugs)
│   ├── tomato.jpg
│   ├── green-chillies.jpg
│   └── placeholder.jpg
├── index.html          # Main application (HTML, Tailwind CSS, & client JS)
├── prices.json         # Optional JSON file for live remote price overrides
└── README.md           # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

All you need is a modern web browser (Google Chrome, Firefox, Safari, Edge).

### Running Locally

You can run the project using any local web server:

#### Option A: Using VS Code Live Server
1. Open the project folder in **VS Code**.
2. Install the **Live Server** extension (by Ritwick Dey).
3. Right-click `index.html` and choose **"Open with Live Server"**.

#### Option B: Using Python
If you have Python installed, run in your terminal:
```bash
# Python 3
python -m http.server 8000
```
Open `http://localhost:8000` in your browser.

#### Option C: Direct File Opening
Double-click `index.html` to open it in your browser. *(Note: fetching `prices.json` may be blocked by CORS when using `file:///`; run a local HTTP server if you wish to test price overrides).*

---

## ⚙️ Configuration & Customization

All primary configurations and content live directly in [index.html](file:///c:/Users/neeru/OneDrive/Desktop/Paramparaa%20Naturals/index.html) and [prices.json](file:///c:/Users/neeru/OneDrive/Desktop/Paramparaa%20Naturals/prices.json).

### 1. Order Form & Email (Web3Forms)
To send orders to a different email address:
1. Generate an access key at [web3forms.com](https://web3forms.com/).
2. Locate line 486 in `index.html` and update:
   ```javascript
   const WEB3FORMS_ACCESS_KEY = "YOUR-ACCESS-KEY-HERE";
   ```

### 2. Products & Categories
Products and their order status are managed within the `productList` array inside `index.html`:
```javascript
{
  category: 'Veggies',
  item: 'Tomato',
  price: 65,
  unit: 'kg',           // 'kg', 'pc', '250gms', etc.
  outOfStock: false     // Set to true to disable adding to cart
}
```

### 3. Dynamic Price Overrides (`prices.json`)
You can adjust pricing without modifying `index.html` by adding key-value pairs matching item names into `prices.json`:
```json
{
  "Tomato": 70,
  "Green Chillies": 40
}
```

### 4. Weekly Nutrition Notes
Update weekly content by modifying the `WEEKLY_NOTE` object in `index.html`:
```javascript
const WEEKLY_NOTE = {
  FruitName: "Mango",
  bullets: [
    "The Principles of Organic Agriculture are Health, Ecology, Fairness and Care.",
    "Strong Immunity Support: Mangoes are rich in Vitamin A and C..."
  ],
  nutritionTip: "Start your meal with protein component before touching carbs."
};
```

### 5. Order Window & Delivery Schedule
Adjust the banner texts near the top of `index.html` inside the order window and delivery schedule blocks:
```html
<!-- Order Window -->
<div class="text-sm text-gray-700 mt-1">
  8th November (Sunday) <b>11:00 AM</b> to<br>
  9th November (Monday) <b>01:00 PM</b>
</div>
```

### 6. Product Images
Images are loaded from the `images/` directory. By default, the app transforms item names into lowercase slugified filenames:
- Example: `"Green Chillies"` $\rightarrow$ `images/green-chillies.jpg`
- For manual mapping, specify the file in the `IMAGE_OVERRIDES` object in `index.html`.

---

## 🌐 Deployment

Since this project consists of purely static files, it can be hosted for free on:

- **GitHub Pages**:
  1. Push the repository to GitHub.
  2. Go to repository **Settings** > **Pages**.
  3. Under **Branch**, select `main` and root directory `/`, then click **Save**.
- **Netlify**: Drag and drop the folder into the Netlify dashboard.
- **Vercel**: Import the GitHub repository or deploy via `vercel deploy`.
- **Cloudflare Pages**: Connect the Git repository and select standard static site output.

---

## 📍 Contact & Store Information

- **Store**: Paramparaa Naturals (Echo-Mate)
- **Address**: Shop No. 5, H.No: 1-5-1082, Silver Petals Apartment, Father Balaiah Nagar, Old Alwal, Secunderabad – 500010
- **Landmark**: Beside Ion Digital Zone – Exam Centre (Ratnadeep Super Market), diagonally opposite BATA showroom
- **Phone / WhatsApp**: +91 6304622533, +91 9640335320
- **Email**: paramsustainables@gmail.com
- **Google Maps**: [Location Link](https://maps.app.goo.gl/B87LW6qmEFZuiccx9?g_st=awb)

---

## 📄 License

This project is proprietary and maintained for **Paramparaa Naturals**. All rights reserved.

