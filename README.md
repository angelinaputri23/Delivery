# Delivery Dashboard

A single-file web app (`delivery-dashboard.html`) for tracking items requested by each branch, preparing shipments, recording carrier and tracking codes, and generating the XMART delivery note (出貨單) as an Excel file.

## Workflow

1. **Item requests**: add what a branch asks for (date, branch, item, quantity, notes such as names or sizes). New items start as `Requested`.
2. **Prepare shipment**: tick items that belong to the same branch and click *Prepare shipment from ticked items*. They become one shipment with status `Prepared`.
3. **Shipments**: set the status (`Prepared` → `Shipped` → `Delivered`), choose the carrier (HCT, Maple or Hemao) and enter the tracking code. The delivered date is filled in automatically when you mark a shipment `Delivered`, and you can edit it.
4. **Delivery note**: click *Download delivery note (.xlsx)* on a shipment. The file contains the company header, branch name and address, item list (name, quantity, notes) and the recipient signature block.
5. **Summary**: item counts per branch by status, plus all packages currently in transit with carrier and tracking code.

## Keeping it organised

- Item requests and shipments can be filtered by **year, month, branch, status** (and **carrier** for shipments), and searched by item, note or tracking code.
- Lists are grouped by year and month, newest first, with a count per group.
- The Summary tab can be limited to a single year.

## Data and backup

- Data is stored in the browser (`localStorage`), so it stays on the device and browser you use. It is not shared between devices.
- Use **Backup** to download a JSON file and **Restore** to load it again. Back up regularly, and before clearing browser data.

## Hosting on GitHub Pages

1. Put `delivery-dashboard.html` in a repository (rename it to `index.html` if you want the root URL to open it).
2. In the repository, go to Settings → Pages and publish from the main branch.
3. Open the Pages URL. The delivery note download works there.

The delivery note uses the ExcelJS library loaded from cdnjs, so an internet connection is needed when downloading it.

## Customising

At the top of the `<script>` section:

- `BR`: branches, each with a display name and the address printed on the delivery note.
- `CR`: list of carriers (currently `HCT`, `Maple`, `Hemao`).

## Limitations

- Because data lives in each browser, use one browser/device as the main one, or move data with Backup and Restore.
- Tracking codes are stored as text only; there are no tracking links yet.
