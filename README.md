# Excel Reports Consolidation

A UiPath RPA workflow that automatically consolidates multiple daily Excel sales reports into a single dated output file.

## What It Does

1. **Creates a dated output file** — generates `SalesResults-YYYY-MM-DD.xlsx` in the `Sales Results/` folder using today's date.
2. **Writes the header row** — populates columns: `Item`, `Unit Price ($)`, `Items Sold`, `Total Income ($)`.
3. **Loops over daily reports** — iterates through every `.xlsx` file in the `Daily Reports/` folder.
4. **Appends data** — copies each file's data (excluding its header) into the consolidated output sheet.

## Project Structure

```
├── Main.xaml              # Main workflow (entry point)
├── project.json           # UiPath project manifest
├── .settings/             # Studio environment settings
├── Daily Reports/         # Place input Excel files here (not committed)
└── Sales Results/         # Output files are generated here (not committed)
```

## Requirements

- UiPath Studio 26.0+
- UiPath.Excel.Activities package
- Input files must have a sheet named `Sheet1` with columns in order: Item, Unit Price, Items Sold, Total Income

## How to Run

1. Copy your daily `.xlsx` report files into the `Daily Reports/` folder.
2. Open `Main.xaml` in UiPath Studio.
3. Click **Run** — the consolidated file will appear in `Sales Results/`.

## Notes

- The output filename is auto-dated (`SalesResults-2026-10-29.xlsx`), so each day produces a new file.
- Header formatting is applied automatically (blue, Calibri 11).
- Excel alerts are suppressed during execution to avoid dialog interruptions.
