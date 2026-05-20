# AI Instructions for Traffic Dashboard

**IMPORTANT: Read this file whenever you are asked to make changes to the Traffic Dashboard.**

## Project Overview
- **Core File:** `traffic.html` (Single file containing HTML, CSS, and JS).
- **Theme:** Minimalist, Light Mode (White background, `#1e293b` text).
- **Layout:** Glassmorphism UI elements were removed in favor of a clean, flat, fast UI without heavy progress bars.

## Technical Details
- **Data Handling:** 
  - Originally relied heavily on JS in-memory aggregation via a global `RAW` object.
  - **DuckDB-WASM** has been initialized (script injected, `DB_CONN` available) and tables (`sales`, `traffic`) are registered upon file upload.
  - *Future Goal / Current Transition:* Migrate filtering and aggregation logic (e.g., `fDays()`, `renderApple()`, `drawBrTable()`) to use direct SQL queries on DuckDB for better performance with large datasets.

## Development Rules
1. **No External Frameworks:** Do not add React, Vue, or Tailwind. Stick to Vanilla JS and Vanilla CSS.
2. **Minimal Changes:** When editing `traffic.html`, only modify the specific functions requested. Ensure `Chart.js` instances are properly destroyed before re-rendering (`dc(id)`).
3. **Aesthetics:** The user prefers clean, minimal design without unnecessary visual clutter (e.g., removed `.mbar` progress bars).
4. **Real-time Updates:** Filter inputs (`<select>`, `<input type="date">`) should trigger `onchange` events instantly; do not add manual "Apply" buttons unless explicitly requested.

## DuckDB Schema
- **sales**: `date` (DATE), `branch_id` (VARCHAR), `branch_name` (VARCHAR), `officer_id` (VARCHAR), `officer_name` (VARCHAR), `category` (VARCHAR), `revenue` (DOUBLE), `transactions` (INT), `units` (INT)
- **traffic**: `date` (DATE), `branch_id` (VARCHAR), `traffic` (INT)

*End of instructions.*
