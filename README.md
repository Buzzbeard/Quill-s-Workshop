# Quill's Workshop

A lightweight [Owlbear Rodeo](https://www.owlbear.rodeo/) extension for importing campaign artwork.

**Install manifest:** https://buzzbeard.github.io/Quill-s-Workshop/manifest.json

## Current workflow

1. Open Quill's Workshop from Owlbear Rodeo.
2. Select an image in the **Delivery Inbox** and choose **Import to Owlbear**.
3. Alternatively, import an image from your computer or from a direct image URL.

The inbox is populated by `deliveries.json`. Each item has a display `name` and a publicly reachable HTTPS `url` for a PNG, JPEG, or WebP image.

```json
[
  {
    "name": "Example delivery",
    "url": "https://example.com/example.png"
  }
]
```

## Status

- Confirmed: full-resolution PNG artwork can be imported from the delivery inbox into Owlbear.
- Implemented but awaiting in-Owlbear verification: version 1.5 connection safeguards and preservation of original image data for normal-size artwork.
- Not yet solved: transferring freshly generated ChatGPT image files into GitHub automatically. ChatGPT's connected GitHub file tools do not currently provide a verified, reliable multi-megabyte image-file handoff from the image workspace.
- No extra accounts, paid hosting, GitHub credentials in browser code, or broader GitHub permissions are required for the current manual-delivery workflow.

## Safety notes

- `deliveries.json` and artwork hosted by GitHub Pages are public; do not publish private images.
- The extension does not store a GitHub token or write to the GitHub repository from the browser.
- The user approves each Owlbear import. Importing an image does not delete the source delivery.

## Testing checklist

- Open the extension in Owlbear and confirm **Connected to Owlbear!** appears.
- Refresh the inbox and verify the listed deliveries.
- Import a verified PNG, then check it in the Owlbear asset library.
- Import a full-resolution image and check dimensions and appearance.
- Test an invalid image URL and confirm a useful error message appears.
