# FRAME — creator / brand marketplace prototype

A responsive, self-contained web prototype for demonstrating business ad uploads, creator uploads, a shared ad library, clip insertion previews, and saved projects.

## Run locally

Requires Node.js 20+.

```sh
npm run dev
```

Open http://localhost:3000. No packages, API keys, or environment variables are required.

## Deploy to Vercel

1. Unzip this project and put its contents in a GitHub repository you control.
2. In Vercel, choose **Add New → Project** and import the repository.
3. Set **Framework Preset: Other**.
4. Set **Build Command: npm run build**.
5. Set **Output Directory: dist**.
6. Leave the install command at its default; there are no dependencies.
7. Deploy. If the repository contains a parent folder, set Root Directory to the folder containing package.json.

Alternatively, run `npx vercel` from this project directory, select Other, and use the same build/output settings. This requires your Vercel account. The included vercel.json provides static-site headers. No backend needs deploying for this demo.

## Demo walkthrough

1. Open the Ad marketplace as Jordan Lee (Creator).
2. Filter categories or search for an ad.
3. Click the play icon to inspect a bundled sample clip.
4. Choose **Use this ad** to open the placement editor.
5. Select a creator video and adjust the insertion point.
6. Click **Play sequence**: the creator clip plays until the insertion point, the brand ad plays, then the creator clip resumes.
7. Give the project a name and choose **Save project**. Reopen it from Saved projects, even after reloading.
8. Upload an MP4/WebM from My videos to try your own footage.
9. Switch account to Northstar Studio (Business) and upload an ad. Switch back to Creator to use it.

## Scope and limitations

- This is a functional frontend prototype, not a production multi-user marketplace.
- Account switching is a demo selector. There is no authentication or security boundary. Everyone using the same browser profile can see its locally stored data.
- Uploaded video blobs and project records are stored in IndexedDB on the current browser/device/origin. They are not uploaded to a server or shared across devices. Clearing browser data removes them. Private browsing and browser quotas can limit persistence.
- Bundled videos are original synthetic title-card samples, not real brand campaigns or stock footage. Sample brand names and content are illustrative.
- Video uploads are capped at 100 MB per file. Codec support depends on the browser; MP4 H.264 and WebM are recommended. No server-side transcoding is performed.
- Preview is a sequential video-player composition. Source switching can introduce a short loading pause. No merged MP4 is generated. Saving preserves editable asset references and insertion time.
- One ad insertion per composition is supported. Overlay editing, payments, payouts, chat, moderation, licensing, and analytics are not included.
- Google Fonts is optional: system font fallbacks work without internet access. Sample videos are bundled locally.

## Production next steps

Replace demo accounts with authentication and server-enforced roles. Store accounts, published ads, creator assets, and versioned projects in PostgreSQL. Use signed direct uploads to object storage, background transcoding/rendering jobs, metadata validation, upload quotas, moderation, and asset usage permissions. Keep composition timing server-side as well as in the editor. Add rendering for downloadable exports and integration tests for authorization and video workflows.

## Files

- index.html — app shell and accessible modal forms
- style.css — responsive dark workspace styling
- app.js — navigation, uploads, IndexedDB persistence, preview composition
- assets/ — bundled sample MP4 videos
- server.mjs — local server supporting media range requests
- build.mjs — creates the deployable dist directory
- vercel.json — hosting configuration

All source code is included. There are no runtime npm dependencies.
