# AutoFit developer website

This directory contains the static developer website for AutoFit and the `app-ads.txt` file required for Google AdMob app verification.

## Required AdMob URL

AdMob must be able to fetch this exact root-level URL:

```text
https://<your-domain>/app-ads.txt
```

The file must contain:

```text
google.com, pub-3971219491693844, DIRECT, f08c47fec0942fa0
```

## GitHub Pages setup

Use one of these deployment shapes:

- Recommended without a custom domain: create or use the GitHub repository named `<github-username>.github.io`, enable Pages with **GitHub Actions**, and deploy this repository. The website URL becomes `https://<github-username>.github.io`.
- Recommended with a custom domain: configure the custom domain in GitHub Pages and put the same domain in Google Play Console.

Do not rely on a project Pages URL like `https://<github-username>.github.io/<repo-name>` for AdMob verification. AdMob uses the hostname from the Play Store developer website and checks `/app-ads.txt` at that hostname root.

## Play Console value

In Google Play Console, set the developer website to the website root, not the text file path:

```text
https://<your-domain>
```

Do not enter:

```text
https://<your-domain>/app-ads.txt
```

## Verification

After deployment, verify:

```bash
curl -L https://<your-domain>/app-ads.txt
```

Expected output:

```text
google.com, pub-3971219491693844, DIRECT, f08c47fec0942fa0
```

Then request an update in AdMob, or wait up to 24 hours for AdMob to detect the Play Console website change and crawl the file.
