# XER Look-Ahead Dashboard

A single-page web app that turns a raw Primavera P6 **.xer** schedule export into an interactive look-ahead dashboard — no plugins, no backend, no server required. Upload a `.xer` file and it generates a rolling look-ahead window, EVM and progress metrics, a population "skyline" chart, a Gantt chart, and a client-side PDF report, all in the browser.

## Features

- **Native XER parsing** — reads `TASK`, `PROJWBS`, and `PROJECT` tables directly from the tab-delimited `.xer` format (no conversion step needed).
- **Configurable look-ahead window** — set a data date and a number of days; the dashboard filters to activities that are active or not-started within that window.
- **Critical path highlighting** — activities are flagged critical (total float ≤ 0) or near-critical (total float ≤ 80 hrs) using conditional formatting, matching P6 conventions.
- **Progress & schedule statistics** — total/completed/in-progress/not-started counts, on-time vs. delayed completions, performance % complete vs. baseline % complete, and a forecast completion date compared against the baseline finish.
- **Earned Value Management (EVM) panel** — Plan %, Progress %, SPI, and CPI from user-entered BAC/PV/EV/AC.
- **Population Skyline chart** — an SVG chart showing how many activities are running per week over an 8-week horizon, useful for resourcing/crew-size conversations.
- **Interactive Gantt chart** — grouped by WBS, with a dynamically scaled year/quarter/month timeline and critical-path color coding.
- **One-click PDF export** — using jsPDF + html2canvas, produces a multi-page, print-ready report (cover/summary, statistics table, skyline, paginated Gantt, and activity table) with running headers/footers.

## Tech Stack

Plain HTML/CSS/JavaScript (no build step, no framework). Charting/export via CDN-hosted libraries:
- [Chart.js](https://www.chartjs.org/)
- [jsPDF](https://github.com/parallax/jsPDF) + [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable)
- [html2canvas](https://html2canvas.hertzen.com/)

## Usage

1. Open `index.html` in any modern browser (or visit the [live demo](https://adnahjennifer.github.io/xer-lookahead-dashboard/) once deployed via GitHub Pages).
2. Choose a `.xer` file exported from Primavera P6.
3. Set the **Data Date** and **Look Ahead (days)** window.
4. Click **Generate** to build the dashboard.
5. Optionally click **Populate Skyline** / **Populate Gantt** for the visual charts, or **Export to PDF** for a shareable report.

No data ever leaves the browser — the file is parsed entirely client-side with the `FileReader` API.

## Project Structure

```
.
├── index.html   # entire application (markup, styles, and logic)
└── README.md
```

## Author

Developed by **Adnah Jennifer**.

## License

MIT — see [LICENSE](LICENSE).
