# Stockroom — Order Allocation

A self-contained browser prototype for allocating limited inventory across customer orders. It uses plain HTML, CSS and JavaScript; no build step or server is required.

## Run it

Open `index.html` in a current browser. Changes are saved in that browser's local storage. Use **Reset example** to restore the starting scenario.

## Allocation behavior

For each product, orders are sorted by confirmed priority from high to low, promised date from earliest to latest, then order ID. Orders with no promised date sort after dated orders. Each order receives its full request when stock permits. When stock is short, a partial-accepting order receives the remainder only if that remainder meets its minimum; otherwise it is deferred. Orders that do not accept partial delivery are filled in full or deferred. Inventory pools are independent by product.

Each allocation has a customer-facing explanation. Recalculation compares the new quantity and status with the previous run and lists every order that changed.

## Priority suggestions

The prototype scans free-text notes for urgency, safety, hospital, contract penalty, and routine language to propose a priority weight and reason. A coordinator must confirm the suggested weight before it affects the sort order. Notes never change stock quantities, minimum quantities, or partial-delivery settings. This is a local demonstration heuristic and does not call an AI service.

## Demonstration

The starting example has 60 AeroSeal Filters. City Hospital requests 20, and two routine orders compete for the remaining stock. Select **Run urgent spike** to increase the hospital request to 32. Recalculation shows the later order's allocation and status change when the remaining 3 units fall below its 10-unit minimum.
