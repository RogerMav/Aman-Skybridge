# SkyBridge Air Cargo

A single-page website for a fictional air cargo logistics service. It includes shipment tracking, a manager dashboard, a delivery cost calculator and an enquiry form. It is plain HTML, CSS and JavaScript with no build step and no dependencies.

## Features

* **Home:** business name, logo, purpose, short description, a "Get Started" button and an order-number tracking box.
* **About:** what the company does, target customers, service area and key value proposition.
* **Services:** six air freight services.
* **Shipment tracking:** customer name, order number, delivery status, current location, expected delivery time, delivery partner and contact number, with search and status filter.
* **Manager dashboard:** six KPIs (active shipments, delivered today, on-time rate, delayed, revenue, average transit time), a weekly volume chart, a shipments-by-status chart and a "Needs attention" list.
* **Delivery cost calculator:** estimates the price from region, service level, weight, dimensions, declared value and optional extras.
* **Contact / enquiry:** contact details and an enquiry form.
* Light and dark mode follow the visitor's device setting.

## Run it

Open `index.html` in any modern browser.

## Publish with GitHub Pages

1. Upload `index.html` to the root of your repository.
2. Go to **Settings → Pages**.
3. Set the source to the `main` branch and the `/ (root)` folder, then save.
4. The site goes live at `https://<your-username>.github.io/<repository-name>/` after a minute or two.

## How the cost calculator works

```
Chargeable weight = max(actual weight, volumetric weight)
Volumetric weight = (L x W x H in cm x pieces) / 6000
Air freight       = chargeable weight x regional rate per kg x service multiplier
Fuel surcharge    = 12% of air freight
Insurance         = 1% of declared value
Total             = air freight + fuel + insurance + dangerous goods ($45) + pickup ($18)
```

|Region|Rate per kg (USD)|
|-|-|
|Domestic (India)|3.20|
|Middle East \& Asia|5.80|
|Europe|7.40|
|North America|8.90|

|Service|Multiplier|
|-|-|
|Standard|1.0x|
|Express|1.6x|
|Priority next-flight|2.2x|

All rates and fees are placeholder values for illustration, not real tariffs. To use your own, edit the two dropdowns in the calculator section and the `calc()` function in `index.html`. The same logic is available as a spreadsheet in `air\_cargo\_pricing.xlsx`.

## Customise

* **Shipment data:** edit the `S` array at the top of the `<script>` section. Each row is customer, order number, status, location, expected delivery, partner and contact number.
* **Dashboard figures:** active, delivered, on-time and delayed counts are calculated from the shipment data. Revenue, transit time and weekly volumes are set in the `K` and `wk` arrays.
* **Enquiry recipient:** change the address in the `mailto:` line of the form's submit handler.

## Notes and limitations

* All shipment, KPI and chart data is sample data. There is no backend or database, so nothing updates in real time.
* The enquiry form opens the visitor's email app with the message pre-filled, and the visitor must press Send. To send automatically, connect a form service such as Formspree, Web3Forms or EmailJS.
* Fonts load from Google Fonts. If they are blocked, the page falls back to system fonts.

## 

