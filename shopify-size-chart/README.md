# Size chart block for Shopify Horizon

`blocks/size-chart.liquid` is a Horizon theme block. It adds a **Size chart** link with zero top and bottom padding to the product page. Clicking the link opens the size chart image in a modal that fits both desktop and mobile screens.

## Install

1. In Shopify admin, go to **Online Store → Themes**. On your Horizon theme, click **⋯ → Edit code**.
2. In the **blocks** folder, click **Add a new block** and name it `size-chart`.
3. Replace the contents of the new file with [`blocks/size-chart.liquid`](blocks/size-chart.liquid), then click **Save**.
4. Go to **Customize**, open a **product** template, select the **Product information** section, and click **Add block → Size chart**.
5. Drag the block to where you want it (usually under the variant picker), choose your **Size chart image**, and click **Save**.

## Settings

| Setting | What it does |
| --- | --- |
| Size chart image | Image shown in the modal. The link is hidden when no image is selected. |
| Mobile image (optional) | A separate image for screens under 750px, such as a taller version of a wide chart. |
| Modal heading | Title at the top of the modal. Leave it empty to hide it. |
| Modal max width (desktop) | Maximum width of the modal from 400 to 1400px. On mobile it always fills the screen width minus 8px on each side. |
| Link text / icon / underline / font size / color / alignment | Control how the link looks. |

## A different chart per product

1. Go to **Settings → Custom data → Products → Add definition**. Name it `Size chart` and use the type **File** (images).
2. Upload a chart to each product in that metafield.
3. In the theme editor, select the Size chart block. Click the **Connect dynamic source** icon next to *Size chart image* and choose the metafield.

Products with no chart in the metafield won't show the link.

## Behaviour

- **Link:** it has zero top and bottom padding and margin. It also overrides Horizon's button styling, so no extra height is added. If you still see space above or below it, it comes from the **Gap** setting of the parent group or section, not from this block.
- **Modal:** it uses the native `<dialog>` element. It closes with the X button, the Esc key, or a click on the dark backdrop, and focus returns to the link afterwards.
- **Scrolling:** the page behind the modal is locked. If the chart is taller than the screen, it scrolls inside the modal.
- **Loading:** the image is lazy-loaded and starts loading when the shopper hovers over or focuses the link, so it doesn't slow down the page.
- **Theme editor:** when you select the block in the editor, the modal opens so you can preview the chart.
