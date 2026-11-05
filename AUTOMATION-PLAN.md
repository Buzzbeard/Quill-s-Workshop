# Automatic delivery — engineering plan

## Target experience
User says "Quill, send that to Owlbear." A specific ChatGPT-generated image arrives in Quill's Workshop, where the user approves importing it into Owlbear. No manual file download, upload, or clipboard step.

## Proven today
- Clipboard image paste from ChatGPT into Owlbear works (user-tested).
- Public HTTPS PNG in a GitHub Pages delivery list imports into Owlbear (user-tested).
- GitHub connector can edit text files in this repository.
- Clipboard copy is a working fallback.

## Unproven / blocked
- No verified mechanism in this environment to transfer arbitrary newly generated multi-megabyte image bytes from ChatGPT's image workspace to the GitHub connector.
- The GitHub connector accepts text/base64 blobs but does not expose a direct workspace-file upload action.
- A sandbox path is not a public image URL; it cannot be placed in deliveries.json for browser retrieval.
- Browser clipboard APIs cannot be assumed to allow silent cross-app reads or writes.
- No automatic end-to-end transfer has been demonstrated.

## Minimal secure architecture if a file handoff becomes available
1. ChatGPT obtains the **specific image bytes** selected by the user.
2. A trusted server-side action stores the bytes at a URL accessible to the Owlbear extension. Prefer private, time-limited access where feasible; public GitHub Pages only with explicit consent.
3. ChatGPT writes a delivery manifest entry containing an image identifier, name, format, and retrieval URL.
4. Workshop displays a pending delivery. User clicks Import to Owlbear.
5. Workshop validates format and uploads through Owlbear SDK.
6. Optional cleanup only after explicit user confirmation; never silently delete artwork.

## Non-goals
- No GitHub tokens or secrets embedded in client-side extension code.
- No unrestricted inbound upload endpoint.
- No public exposure of private campaign art by default.
- No new paid infrastructure or broader repository permissions without approval.
- Do not claim that polling a manifest solves the image-bytes handoff.

## Next feasibility test
Determine whether a newly generated image has a **verified tool-accessible binary source or authorized public URL** that the GitHub connector or another connected action can ingest. If no such bridge exists, retain the proven clipboard workflow and explain the limitation rather than adding superficial features.
