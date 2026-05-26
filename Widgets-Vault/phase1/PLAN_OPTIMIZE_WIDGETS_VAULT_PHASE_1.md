# Widgets Vault Optimization Plan - Phase 1

## Document Info

- App: `Widgets Vault`
- Platform: `Google Play`
- Phase: `Phase 1 - Baseline, Diagnosis, Decision`
- Status: `In progress`
- Created: `2026-05-26`
- Owner: `Remi + Codex`
- Purpose of this document:
  - collect all required metrics in one place
  - diagnose the true bottleneck before changing product or ads
  - choose the first optimization direction based on evidence
  - define exactly what to change, how to track it, and how to evaluate it

## Why This Phase Exists

The current file state mixes raw numbers, code audit notes, and tentative ideas, but it does not yet answer the operational questions:

1. What full dataset is required before making a decision?
2. Which problem is actually the biggest bottleneck right now?
3. What optimization option should be chosen first?
4. Why is that option better than the other options?
5. What business outcome should improve?
6. What code, config, tracking, or console changes are required?
7. How long should the test run, what result is considered success, and what should be changed next?

This Phase 1 plan is designed to solve those questions cleanly.

## Phase 1 Objective

Do not commit to a monetization optimization direction yet.

Phase 1 has one job:

- build a complete baseline
- identify the real bottleneck
- choose the first optimization strategy after the baseline is complete

Only after the baseline is filled and reviewed should the team decide whether the first optimization cycle targets:

- store conversion
- retention / activation
- crash / quality
- ad yield
- ad coverage
- ad pressure
- paywall / purchase flow

## Final Deliverables Of Phase 1

Phase 1 is complete only when these outputs exist:

1. A complete baseline table with exact dates and sources.
2. A ranked bottleneck analysis.
3. A recommended optimization direction for Phase 2.
4. A written explanation of:
   - root cause
   - why this direction was selected
   - what it is meant to improve
   - what changes are required
   - how success will be measured
5. A rollout and follow-up plan for the first experiment.

## Linked Working Files

Dung cac file sau de theo doi Phase 1:

- Bao cao phuong an de confirm voi lead:
  - [REPORT_OPTIMIZATION_OPTIONS_WIDGETS_VAULT_PHASE1.md](/Users/remi/Documents/Marketing/Widgets-Vault/phase1/REPORT_OPTIMIZATION_OPTIONS_WIDGETS_VAULT_PHASE1.md)
- File TODO crashlist trong project:
  - [TODO_CRASHLIST_FIREBASE_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_CRASHLIST_FIREBASE_PHASE1.md)
- File TODO triển khai retention first session:
  - [TODO_RETENTION_FIRST_SESSION_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_RETENTION_FIRST_SESSION_PHASE1.md)
- File TODO tracking retention:
  - [TODO_RETENTION_TRACKING_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_RETENTION_TRACKING_PHASE1.md)
- File TODO banner cleanup:
  - [TODO_BANNER_CLEANUP_PHASE1.md](/Users/remi/Documents/AndroidProjects/OneWidget/OneWidget/docs/optimization/TODO_BANNER_CLEANUP_PHASE1.md)

Luu y cho cac phuong an can sua app:

- Truoc khi viet report cho lead, can co `TODO` trien khai trong repo neu phuong an do can code, tracking, QA, hoac release checklist.
- File report chi nen tom tat `Can lam` o muc hanh dong rollout va `Trien khai` o muc cong viec de ship duoc hanh dong do.
- Khong viet `Can lam` theo kieu dieu tra, dat cau hoi, hoac "review sau".

## Optimization Workflow Standard

This should be reused as the default workflow for future apps.

1. Collect baseline data.
2. Separate facts from assumptions.
3. Rank bottlenecks by business impact.
4. Choose one primary optimization direction only.
5. Define the smallest useful change set.
6. Define tracking before rollout if current tracking is insufficient.
7. Roll out one controlled change group.
8. Wait for a stable observation window.
9. Compare before vs after.
10. Keep, revert, or revise.

## Current Known Facts

These facts are already available and should remain visible as the starting context.

### Live Console Capture Status

- Latest live capture performed: `2026-05-26`
- Sources used in this pass:
  - `Google Play Console`
  - `Firebase Console`
- This document now contains:
  - confirmed app dashboard metrics
  - confirmed store acquisition / listing conversion metrics
  - confirmed country-level store conversion metrics
  - confirmed ratings and review volume metrics
  - confirmed top crash / ANR issue groups
  - confirmed AdMob format-level performance from exported CSVs
  - confirmed Google Analytics engagement overview metrics
  - confirmed Google Analytics pages and screens report metrics
- Still missing after this pass:
  - exact uninstall rate from Play Console
  - exact WAU
  - exact D30 retention
  - structured review-theme summary across a larger review sample
  - screenshot-level content audit per locale

### App Context

- Main countries: `Brazil, Mexico, Turkey, Indonesia, United States, Philippines`
- Latest public version: `19 (1.0.19)`
- Latest public release date: `2026-04-16`
- Monetization model: `Hybrid`, but current revenue is almost entirely ad-driven
- Active ad formats:
  - `Banner`
  - `Interstitial`
  - `Rewarded`
  - `Native`
  - `App Open`

### Play Console Snapshot

- Total installs shown on overview: `2.66k`
- Install-to-active-users metric shown on overview: `76.1%`
- Issue rate: `3.34%`
- Issue rate change: `+0.84pp`
- ANR rate: `0.09%`
- ANR change: `-0.10pp`
- Average rating: `4.48`
- Rating trend: `-0.06`
- First opens in overview period: `1.53k`
- First opens trend: `-3%`
- MAU: `3.22k`
- MAU trend: `+8%`

### Activity Snapshot

- Recent visible DAU range: roughly `221 - 277`
- Installed-user base observed: roughly `3.66k - 3.74k`
- Google Analytics current-period active users:
  - `1 day`: `303`
  - `7 days`: `1.4K`
  - `30 days`: `4.8K`

### Country-Level Ad Snapshot For Recent 30 Days

- `Brazil`: `1,559 AU`, `1,039 AV`, `57.92%` viewer rate, `$11.81`, `15,315` impressions
- `Mexico`: `764 AU`, `484 AV`, `56.94%` viewer rate, `$5.64`, `7,209` impressions
- `Turkey`: `815 AU`, `386 AV`, `40.00%` viewer rate, `$4.83`, `5,894` impressions
- `Indonesia`: `222 AU`, `108 AV`, `43.69%` viewer rate, `$1.63`, `2,312` impressions
- `United States`: `98 AU`, `48 AV`, `43.88%` viewer rate, `$11.33`, `624` impressions

### Format-Level Ad Snapshot For Recent 30 Days

- `Native`: `$24.90`, `20,608` impressions, weighted eCPM `~$1.21`, about `56.6%` of ad revenue
- `Interstitial`: `$13.79`, `4,962` impressions, weighted eCPM `~$2.78`, about `31.4%` of ad revenue
- `Banner`: `$3.50`, `10,058` impressions, weighted eCPM `~$0.35`, about `8.0%` of ad revenue
- `App Open`: `$1.78`, `1,755` impressions, weighted eCPM `~$1.01`, about `4.1%` of ad revenue

### Firebase Snapshot For Last 28 Days

- Date range: `2026-04-28 -> 2026-05-25`
- Total views: `68,725`
- Active users: `4,475`
- Views per active user: `15.36`
- Average engagement time per active user: `3m 54s`
- Event count: `130,650`
- Firebase total revenue: `$4.04`

### Key Screen Snapshot

- `MainActivity`: `2,583` active users, `6.55` views per active user, `2m 39s`, `$2.41` revenue
- `OnboardActivity`: `3,712` active users, `$0.29` revenue
- `AdActivity`: `2,380` active users, `$0.40` revenue
- `LanguageActivity`: `3,451` active users, `$0.11` revenue
- `CateFavoriteActivity`: `2,584` active users, `$0.06` revenue

### Firebase Retention Snapshot

- New users: `3.6K`
- Returning users: `1.7K`
- Visible recent retention band: roughly `5% - 15%`
- Long-tail visible endpoint: roughly `4% - 5%`

## Phase 1 Data Collection Checklist

No optimization direction should be chosen until this checklist is filled or explicitly marked `Not available`.

### A. Store Funnel Data

| Metric | Required Window | Source | Status | Current Value | Notes |
| --- | --- | --- | --- | --- | --- |
| Impressions | Last 28d vs previous 28d | Play Console | Missing |  | Not surfaced in current acquisition screens captured |
| Store listing visitors | Last 28d vs previous 28d | Play Console | Captured | `15,055` for `2026-04-21 -> 2026-05-18`, `+3.62%` | Store listing visitors |
| Visitor -> install CVR | Last 28d vs previous 28d | Play Console | Captured | `23.63%`, `-1.41%` | Store listing conversion |
| Search CVR | Last 28d vs previous 28d | Play Console | Missing |  | Need source-specific conversion screen |
| Browse CVR | Last 28d vs previous 28d | Play Console | Missing |  | Need source-specific conversion screen |
| Acquisition source split | Last 28d | Play Console | Captured | `Store listing acquisitions 3,558`: `Ads/Referrals 2,943`, `Browse 589`, `Search 26` | Window `2026-04-21 -> 2026-05-18` |
| Country-level install CVR | Last 28d | Play Console | Captured | `BR 25.4%`, `TR 23.22%`, `MX 26.72%`, `ID 19.6%`, `US 22.99%`, `PH 30.16%` | Also captured corresponding visitors and acquisitions |
| Search term insight | Last 28d if available | Play Console | Partial | `widget 25`, `widgett-widget a 6`, `widgets 3`, `Other 26` | Search-term data is limited / partially thresholded |

### B. Product And Retention Data

| Metric | Required Window | Source | Status | Current Value | Notes |
| --- | --- | --- | --- | --- | --- |
| First opens | Last 28d vs previous 28d | Play Console / Firebase | Partial | `1.53k` | Trend `-3%` known |
| DAU | Last 28d trend | Firebase / Play | Partial | `~221 - 277 recent days`, latest Firebase dashboard `303` | Need one normalized source/window for final baseline |
| WAU | Last 28d trend | Firebase | Partial | `1.4K` active users in last 7 days from GA / Firebase dashboard | Need direct WAU trend report only if required |
| MAU | Last 28d vs previous 28d | Play Console / Firebase | Partial | `3.22k` | Trend `+8%` known |
| D1 retention | Last 28d cohorts | Firebase | Captured | `7.0%` from GA retention insight on `2026-05-26`; Firebase dashboard card also showed `5.4%` on another recent window | Use GA value as current primary baseline unless a stricter cohort definition is needed |
| D7 retention | Last 28d cohorts | Firebase | Captured | `0.6%` | From GA retention insight |
| D30 retention | Last 60d cohorts | Firebase | Missing |  |  |
| Returning users | Last 28d | Firebase | Partial | `1.7K` |  |
| Engaged sessions per user | Last 28d | Firebase | Partial | `1.5` | Existing captured Firebase snapshot |
| Average session duration | Last 28d | Firebase | Partial | `3m 54s per active user`, `1m 46s per engaged session` | From GA / Firebase overview |
| Uninstall rate | Last 28d vs previous 28d | Play Console | Missing |  | Current console pass did not surface an exact uninstall-rate metric; nearest visible proxy is churn `3.72%` |

### C. Monetization Data

| Metric | Required Window | Source | Status | Current Value | Notes |
| --- | --- | --- | --- | --- | --- |
| Total revenue | Last 28d vs previous 28d | AppLovin + Play | Partial | Play-billed revenue shows `-` on app dashboard; Firebase 28d revenue snapshot `$4.04` | True total still needs AppLovin + billing combined |
| Ad revenue | Last 28d vs previous 28d | AppLovin | Partial | Format and country splits captured in known facts | Need same-window comparison vs previous period |
| Purchase revenue | Last 28d vs previous 28d | Play / Billing | Missing |  |  |
| Ad impressions per DAU | Last 28d | AppLovin + Firebase | Captured | Overall `~5.33` using `37,383 impressions / 7,010 summed DAU`; format-level values captured | Use carefully; this is based on daily summed DAU from format exports |
| Ad ARPDAU | Last 28d | AppLovin + Firebase | Captured | Overall `~$0.0063` using `43.97 / 7,010 summed DAU` | Format-level values captured below |
| ARPU | Last 28d | Revenue + active users | Missing |  |  |
| ARPPU | Last 28d | Revenue + payers | Partial | Play app dashboard shows `-` | Suggests effectively no meaningful Play purchase revenue in current window |
| Revenue by country | Last 28d | AppLovin | Partial |  | Need full top-country table |
| Revenue by format | Last 28d | AppLovin | Captured | `Native 24.90`, `Interstitial 13.79`, `Banner 3.50`, `App Open 1.78` | From CSV exports |
| Fill rate by format | Last 28d | AppLovin | Captured | `Native 88.60%`, `App Open 60.16%`, `Interstitial 44.44%`, `Banner 35.77%` | From CSV exports |
| eCPM by format | Last 28d | AppLovin | Captured | `Interstitial 2.78`, `Native 1.21`, `App Open 1.01`, `Banner 0.35` | Weighted from revenue/impressions |
| Requests / matched / impressions by format | Last 28d | AppLovin | Captured | Full format-level request and impression totals captured | See `Live Ad Format Capture` section |
| Ad viewer rate by country | Last 28d | AppLovin | Partial |  | BR/MX/TR/ID/US known |
| Rewarded completion rate | Last 28d | AppLovin / Firebase | Missing |  |  |
| Paywall view -> purchase CVR | Last 28d | Billing / Firebase | Missing |  |  |
| Trial start rate | Last 28d | Billing | Missing |  | Only if subscriptions still active |
| Trial -> paid CVR | Last 28d | Billing | Missing |  |  |

### D. Quality Data

| Metric | Required Window | Source | Status | Current Value | Notes |
| --- | --- | --- | --- | --- | --- |
| Crash-free users | Last 28d vs previous 28d | Play Console / Crashlytics | Captured | `92.9%` | From Firebase / GA Firebase overview card |
| Issue rate | Last 28d vs previous 28d | Play Console | Partial | `3.34%` | Trend `+0.84pp` |
| ANR rate | Last 28d vs previous 28d | Play Console | Partial | `0.09%` | Trend `-0.10pp` |
| Top crash groups | Last 28d | Play Console / Crashlytics | Captured | See `Live Crash Group Capture` section below | Version `19 (1.0.19)`, user-perceived issues |
| Top ANR groups | Last 28d | Play Console | Partial | `Input dispatching timed out` visible at low volume | Need fuller ANR-focused view if ANR becomes a priority |
| Device / OS concentration of issues | Last 28d | Play Console | Missing |  |  |
| Crash impact by country | Last 28d | Play Console | Missing |  |  |

### E. Ratings And Reviews

| Metric | Required Window | Source | Status | Current Value | Notes |
| --- | --- | --- | --- | --- | --- |
| Average rating | Last 28d vs previous 28d | Play Console | Partial | `4.48` | Trend `-0.06` |
| Review volume | Last 28d vs previous 28d | Play Console | Partial | Lifetime `373` reviews with written text, lifetime `1,511` raters | Need 28-day review count specifically |
| Main complaint themes | Last 50-100 recent reviews | Play Console | Partial | Early visible complaint: `too many ads`, `limited dark / black theme options` | Must still be summarized from a larger sample |
| Main positive themes | Last 50-100 recent reviews | Play Console | Partial | Early visible positives: `useful`, `very good`, `excellent`, `recommend` | Must still be summarized from a larger sample |
| Country-specific review issues | Last 50-100 reviews | Play Console | Partial | Recent visible reviews skew positive across `BR`, `TR`, `ES`; complaint sample seen in `EN/US-style` review about ads/themes | Expand sample before final conclusions |

### F. Listing Assets

| Asset / Input | Status | Notes |
| --- | --- | --- |
| Current title | Captured | `Widget Vault – Smart Widgets` |
| Current short description | Captured | `One app for all widgets: weather, photo, calendar, battery, clock and more` |
| Current full description | Captured | English full description extracted from Play Console listing editor |
| Icon | Partial | Present in default listing editor, `1/1` asset uploaded |
| Feature graphic | Partial | Present in default listing editor as `Ảnh đầu trang`, `1/1` asset uploaded |
| Screenshot set per key locale | Partial | Default `en-US` listing has `6/8` phone screenshots; no tablet/Chromebook/XR screenshots uploaded in current default listing |
| Experiment history | Missing | A/B tests if any |

## Live Ad Format Capture

Captured from the provided exported format CSV files:

- [inters.csv](/Users/remi/Downloads/inters.csv)
- [native.csv](/Users/remi/Downloads/native.csv)
- [open.csv](/Users/remi/Downloads/open.csv)
- [banner.csv](/Users/remi/Downloads/banner.csv)

### Window

- `30 days`
- Source format exports appear to be daily rows from AdMob / mediation reporting

### Overall Ads Snapshot

- Total ad revenue: `$43.97`
- Total impressions: `37,383`
- Total requests: `95,544`
- Total matched requests: `57,449`
- Total clicks: `1,698`
- Weighted eCPM: `~$1.18`
- Aggregate fill rate: `60.13%`
- Aggregate show rate: `65.07%`
- Aggregate CTR: `4.54%`

### Format-Level Performance

- `Native`
  - Revenue: `$24.90`
  - Revenue share: `56.63%`
  - Impressions: `20,608`
  - Impression share: `55.13%`
  - Requests: `37,367`
  - Matched requests: `33,109`
  - Fill rate: `88.60%`
  - Show rate: `62.24%`
  - Weighted eCPM: `~$1.21`
  - CTR: `4.93%`
  - Daily viewer rate: `6.85%`
  - ARPDAU: `~$0.0036`

- `Interstitial`
  - Revenue: `$13.79`
  - Revenue share: `31.36%`
  - Impressions: `4,962`
  - Impression share: `13.27%`
  - Requests: `18,036`
  - Matched requests: `8,016`
  - Fill rate: `44.44%`
  - Show rate: `61.90%`
  - Weighted eCPM: `~$2.78`
  - CTR: `7.05%`
  - Daily viewer rate: `0.83%`
  - ARPDAU: `~$0.0020`

- `Banner`
  - Revenue: `$3.50`
  - Revenue share: `7.96%`
  - Impressions: `10,058`
  - Impression share: `26.91%`
  - Requests: `32,079`
  - Matched requests: `11,474`
  - Fill rate: `35.77%`
  - Show rate: `87.66%`
  - Weighted eCPM: `~$0.35`
  - CTR: `1.39%`
  - Daily viewer rate: `37.16%`
  - ARPDAU: `~$0.0005`

- `App Open`
  - Revenue: `$1.78`
  - Revenue share: `4.05%`
  - Impressions: `1,755`
  - Impression share: `4.69%`
  - Requests: `8,062`
  - Matched requests: `4,850`
  - Fill rate: `60.16%`
  - Show rate: `36.19%`
  - Weighted eCPM: `~$1.01`
  - CTR: `10.94%`
  - Daily viewer rate: `1.75%`
  - ARPDAU: `~$0.0003`

### Initial Ad-Network Interpretation

- `Native` is the volume and revenue leader by a wide margin.
- `Interstitial` remains the most efficient format by eCPM.
- `Banner` has very broad user exposure but poor monetization efficiency.
- `App Open` contributes little and is not a near-term primary growth lever.
- `Banner` and `Interstitial` both have materially weaker fill than `Native`.
- `Banner` show rate is high after match, but that does not compensate for very weak yield.

## Live Store Conversion Capture

Captured from `Google Play Console -> reporting/acquisition/overview` and `reporting/acquisition/details`.

### Window

- `2026-04-21 -> 2026-05-18`

### Store Listing Conversion

- Store listing visitors: `15,055`, `+3.62%`
- Store listing acquisitions: `3,558`, `-2.23%`
- Visitor -> install conversion: `23.63%`, `-1.41%`

### Acquisition Source Mix

- Total acquisitions: `3,623`, `-5.65%`
- Browse acquisitions: `653`, `-19.68%`
- Store-listing acquisitions from:
  - Ads and referrals: `2,943`, `+1.06%`
  - Browse: `589`, `-15.74%`
  - Search: `26`, `-7.14%`

### Country-Level Store Conversion

- `Brazil`: `5,429` visitors, `1,379` acquisitions, `25.4%` CVR
- `Turkey`: `3,523` visitors, `818` acquisitions, `23.22%` CVR
- `Mexico`: `2,766` visitors, `739` acquisitions, `26.72%` CVR
- `Indonesia`: `551` visitors, `108` acquisitions, `19.6%` CVR
- `United States`: `187` visitors, `43` acquisitions, `22.99%` CVR
- `Philippines`: `126` visitors, `38` acquisitions, `30.16%` CVR

### Search-Term Signals

- Search acquisitions:
  - `Other`: `26`
- Discoverability terms:
  - `Other`: `501`
  - `widget`: `25`
  - `widgett-widget a`: `6`
  - `widgets`: `3`

## Live Ratings And Review Capture

Captured from `Google Play Console -> user-feedback/ratings` and `user-feedback/reviews`.

### Ratings Snapshot

- Lifetime Google Play rating count: `4,544`
- Default Google Play rating: `4.482`
- Average rating, last 28 days: `4.482`
- Lifetime raters shown: `1,511`
- Written-review count shown: `373`
- Latest version rating:
  - `1.0.19 (19)`: `101` ratings, average `4.515`

### Early Review Signal

Visible recent review sample in the current page is mostly positive.

Positive themes already visible:

- useful
- excellent
- very good
- recommend

Negative theme already visible:

- too many ads
- not enough dark / black theme options

## Live Google Analytics Capture

Captured by opening the Google Analytics property linked from Firebase.

### Engagement Overview

- Window: `2026-04-28 -> 2026-05-25`
- Active users: `4.5K`
- New users: `3.6K`
- Active users in last `7 days`: `1.4K`
- Active users in last `1 day`: `303`
- Crash-free users: `92.9%`
- Average engagement time per active user: `3m 54s`
- Engaged sessions per active user: `1.5`
- Average engagement time per engaged session: `1m 46s`

### Retention Insight

- `Day 1 retention`: `7.0%`
- `Day 7 retention`: `0.6%`
- `Day 30 retention`: not yet captured directly in this pass

### Top Screens And Pages

Window: `2026-04-28 -> 2026-05-25`

- Total views: `68,725`
- Total active users: `4,475`
- Views per active user: `15.36`
- Total event count: `130,650`
- Total revenue: `$4.04`

Top visible screens:

- `MainActivity`: `16,920` views, `2,583` active users, `6.55` views per user, `2m 39s`, `36,223` events, `$2.41`
- `SplashActivity`: `12,634` views, `4,412` active users, `2.86` views per user, `10s`, `16,239` events
- `OnboardActivity`: `10,457` views, `3,712` active users, `2.82` views per user, `34s`, `13,591` events, `$0.29`
- `AppLovinFullscreenActivity`: `8,493` views, `2,156` active users, `3.94` views per user, `1m 58s`, `16,506` events
- `AdActivity`: `8,070` views, `2,380` active users, `3.39` views per user, `36s`, `10,027` events, `$0.40`
- `LanguageActivity`: `3,939` views, `3,451` active users, `1.14` views per user, `11s`, `4,738` events, `$0.11`
- `CateFavoriteActivity`: `2,866` views, `2,584` active users, `1.11` views per user, `18s`, `3,501` events, `$0.06`
- `PremiumActivity`: `2,550` views, `1,043` active users, `2.44` views per user, `9s`, `2,927` events, `$0.02`
- `WidgetConfigureAct`: `1,619` views, `450` active users, `3.60` views per user, `49s`, `2,994` events, `$0.01`
- `CoinsActivity`: `776` views, `438` active users, `1.77` views per user, `5s`, `822` events

### 7-Day Country Activity Snapshot

Visible on GA home in the recent `7-day` view:

- `Brazil`: `549`
- `Turkey`: `255`
- `Mexico`: `212`
- `Indonesia`: `70`
- `Philippines`: `37`
- `United States`: `37`
- `Russia`: `36`

## Live Listing Asset Capture

Captured from `Google Play Console -> store listings -> default main store listing`.

### Listing Metadata

- Listing type: `Default Play Store listing`
- Locale: `English (United States) - en-US`
- Listing status: `Active`
- Last updated: `2026-01-16`

### Current Public-Facing Text

- App name:
  - `Widget Vault – Smart Widgets`

- Short description:
  - `One app for all widgets: weather, photo, calendar, battery, clock and more`

- Promo video:
  - `https://youtu.be/ZCcFAb2qH6s`

- Full description:

```text
Upgrade your Android experience with Widget Vault, the ultimate all-in-one widget app designed to help you create a smart, beautiful, and personalized home screen. Whether you want a stylish clock widget, a weather widget, or battery widgets, countdown widgets, notes widgets, transparent widgets, and more - Widget Vault brings everything together in one easy, powerful, customizable place.
Widget Vault also supports photo widgets that let you display your favorite memories in a cute or aesthetic frame. For productivity, the app includes simple calendar widgets, daily quote widgets, note widgets, and contact shortcuts - perfect for users who want both beauty and function.
With a large collection of ready-made widgets and a full Widget Editor, you can quickly create and customize widgets that match your style. Change colors, fonts, themes, layouts, backgrounds, borders, and more. Every widget can be personalized to make your home screen unique, clean, and functional.
No more switching between multiple apps - now you get all widgets in one app

⭐ Key Features

- Easy to use, clean UI, smooth performance
- All-in-one widget app
- Widget themes for android
- Aesthetic & minimal widget packs
- Custom widget editor
- Photo, clock, countdown, battery, quote, note, and calendar widgets
- Many uniquely designed widget templates are available for you to choose from
- Easy and quick to add widgets to your home screen
- Allows you custom home screen with Widgets: clock & weather widget, photo widget, calendar widget, battery widget, note widget...

🎨 All-in-One Widget Collection

Access a wide range of widgets including:
- Weather Widget
- Clock Widget
- Photo Widget
- Calendar Widget
- Battery Widget
- Countdown Widget
- Quote Widget
- Notes Widget
- Contact Widget

The app is optimized for users searching for widget needs such as:
- Aesthetic widget pack
- Widget all in one
- Customizable clock widget
- Photo widget android
- Simple battery widget
- Cute pastel widget
- Countdown day widget

🌼Beautiful Pre-designed Widgets
- Hundreds of aesthetic widgets in multiple themes, Includes photo widgets, weather widget, clock widgets, calendar widgets, battery widgets, quote widgets, countdown widgets...
- Multiple sizes and layouts for any home screen
- Fully editable templates: colors, fonts, backgrounds, transparency, layout
- Easily personalize every widget to match your style
- Easy to save and add widgets to your home screen

✔️Widget Editor – Create Your Own Style
- Customize any widget with fonts, colors, shapes, borders, and layouts
- Add photos, backgrounds, or transparent styles for a clean aesthetic
- Allows you to save your widget design and apply it instantly
- Build unique photo, clock, battery, calendar, or countdown widgets your way

🌦️ Smart & Useful Widgets

- Real-time weather forecast
- Stylish analog & digital clock widgets
- Personal photo albums for photo widgets
- Important dates with countdown widgets
- Daily motivation via quote widgets
- Fast access with contact widgets
- Quick notes right on your home screen
- Battery percentage and health with battery widgets
- All widgets are optimized for speed, stability, and low battery usage

🌟 Why Choose Widget Vault?

Widget Vault combines beauty and utility in one powerful widget app. Instead of having many separate apps, you only need one widget app to design, customize, and personalize your home screen. If you love Android widgets, aesthetic themes, or simply want your home screen to look clean and unique, Widget Vault is the perfect choice

📥 Download Widget Vault Today
Customize your widgets. Personalize your device.
Make your Android home screen smarter, cleaner, and more beautiful.

Widget Vault - All Widgets in One Place.
```

### Asset Inventory

- App icon: `uploaded`, `1/1`
- Feature graphic: `uploaded`, `1/1`
- Phone screenshots: `6/8`
- 7-inch tablet screenshots: `0`
- 10-inch tablet screenshots: `0`
- Chromebook screenshots: `0`
- Android XR screenshots: `0`
- XR videos: `0`

## Uninstall / Churn Note

In the current console pass, an exact `uninstall rate` metric was not surfaced on the captured Play Console routes.

The closest currently visible lifecycle-loss metric is:

- `Tỷ lệ người dùng ngừng sử dụng` / churn rate: `3.72%`
- change vs previous 28 days: `-0.29%`

Until the exact Play uninstall report is opened and captured, treat:

- `uninstall rate` as `still missing`
- `churn rate 3.72%` as a supporting retention-risk signal, not a direct substitute

## Live Crash Group Capture

Captured from `Google Play Console -> vitals/crashes`, filtered to:

- `Last 28 days`
- `Version 19 (1.0.19)`
- `User-perceived crashes and ANRs`

### Top Visible Issues

1. `com.widget.widgetvault.widgettheme.topwidgets.ui.main.Hilt_MainActivity.onDestroy`
   - `java.lang.IllegalStateException`
   - affected users: `114`
   - events: `132`
   - issue share shown: `6.3%`

2. `com.widget.widgetvault.widgettheme.topwidgets.widget.AbsAppWidgetProvider$onUpdateWidgetWithSize$1.invokeSuspend`
   - `java.lang.IllegalArgumentException`
   - affected users: `32`
   - events: `1,635`
   - issue share shown: `78.4%`

3. `com.wingoo.app.features.main.ui.home.home.HomeFragment$onShowIntersAndWithAction$1.invokeSuspend`
   - `java.lang.IllegalStateException`
   - affected users: `10`
   - events: `14`
   - issue share shown: `0.7%`

4. `com.wingoo.app.features.configure.select.page.PickWidgetPagerFragment$widgetAdapter$2$1$onClickWidget$1.invokeSuspend`
   - `java.lang.IllegalStateException`
   - affected users: `8`
   - events: `8`
   - issue share shown: `0.4%`

5. `com.android.server.appwidget.AppWidgetServiceImpl.updateAppWidgetInstanceLocked`
   - affected users: `2`
   - events: `262`
   - issue share shown: `12.6%`

### Additional Low-Volume Issues Seen

- `BaseFragment.renderLoading -> IllegalStateException`
- `Hilt_UpdateWidgetService.generatedComponent -> IllegalStateException`
- `android.graphics.BaseCanvas.throwIfCannotDraw -> RuntimeException`
- `okhttp3.Dns.lookup -> UnknownHostException`
- `Input dispatching timed out` ANR
- `WallpaperFragment onShowInterWithAction -> IllegalStateException`
- `OutOfMemoryError`

## Phase 1 Bottleneck Diagnosis Framework

After the checklist is filled, the app must be scored across five areas.

### 1. Acquisition

Symptoms:

- low impressions
- weak listing visitors
- low listing conversion
- weak country-level conversion

Likely first move if this is the main bottleneck:

- ASO / listing optimization
- country localization
- screenshot and copy testing

### 2. Activation And Retention

Symptoms:

- many first opens but weak D1 / D7
- low returning users
- low session depth
- high churn after first session

Likely first move if this is the main bottleneck:

- onboarding simplification
- reduce early ad pressure
- improve time-to-value
- improve first widget success flow

### 3. Monetization Yield

Symptoms:

- decent active user base but weak ARPDAU
- weak fill rate
- weak eCPM
- low viewer coverage by country

Likely first move if this is the main bottleneck:

- ad placement mix review
- improve preload / coverage
- country-level ad strategy
- format-level monetization tuning

### 4. Ad Pressure / UX Balance

Symptoms:

- good revenue per viewer but weak engagement or rating trend
- many ad surfaces stacked in core flows
- strong interstitial use on weak-intent actions

Likely first move if this is the main bottleneck:

- reduce banner load
- reduce low-intent interstitials
- shift pressure from forced ads to higher-intent or rewarded ads

### 5. App Quality

Symptoms:

- issue rate high enough to suppress sessions, revenue, and rating
- crash clusters on key flows
- country or device issue concentration

Likely first move if this is the main bottleneck:

- crash / ANR fixes before monetization changes

## Current Early Hypotheses

These are only hypotheses. They are not yet approved directions.

### Hypothesis A: Crash / Quality May Be Blocking Growth

Why this might be true:

- issue rate `3.34%` is high for a revenue-dependent utility app
- rating trend is negative
- quality problems can suppress sessions, retention, reviews, and revenue at the same time

What this would improve if confirmed:

- retention
- rating trend
- ad impressions
- long-term revenue stability

### Hypothesis B: Banner Pressure May Be Too High Relative To Revenue

Why this might be true:

- banner contributes only about `8%` of ad revenue
- home banner sits on the shell-level screen with broad exposure
- banners also exist on other feature screens

What this would improve if confirmed:

- engagement comfort
- session depth
- downstream interstitial / native value capture
- possibly rating trend

### Hypothesis C: Interstitial Strategy Is Strong But One Placement May Be Too Broad

Why this might be true:

- interstitial eCPM is the strongest monetization efficiency
- many interstitial placements are on high-intent actions
- bottom-navigation interstitial is broader and may be lower-quality UX

What this would improve if confirmed:

- smoother navigation
- lower disruption
- preserved interstitial yield on stronger placements

### Hypothesis D: Retention Is The Real Revenue Ceiling

Why this might be true:

- MAU exists, but DAU still looks modest
- visible retention band is weak
- revenue scale is limited if users do not come back often enough

What this would improve if confirmed:

- DAU
- impressions
- ARPDAU base expansion
- ability to scale ad revenue without increasing ad pressure

## Decision Rules For Choosing Phase 2 Direction

After the baseline is complete, choose the first direction using these rules.

### Choose `Quality First` if all are true

- issue rate remains materially high
- major crash groups affect core flows
- rating complaints mention bugs, freezes, or broken widgets

### Choose `Retention First` if all are true

- D1 / D7 are weak relative to installs
- DAU / returning-user ratio is poor
- early screens show heavy drop-off or low session depth

### Choose `Monetization Mix First` if all are true

- retention is acceptable enough
- quality is not the dominant blocker
- ad revenue per user is weak or banner pressure appears inefficient

### Choose `Store Conversion First` if all are true

- traffic exists but listing CVR is weak
- country-level store conversion is clearly underperforming
- in-app quality is not the main blocker

## Phase 1 Readiness Review

This section answers one practical question:

- do we already have enough evidence to prepare optimization options for lead review?

### Metrics That Are Sufficiently Complete

These are already strong enough to support option design:

- ad revenue mix by format
- ad delivery efficiency by format:
  - fill rate
  - show rate
  - eCPM
  - CTR
- country-level ad monetization snapshot
- store listing visitors, acquisitions, and overall listing CVR
- country-level store CVR for major markets
- D1 and D7 retention direction
- DAU / 7-day / 30-day active-user scale
- top screen engagement surfaces
- rating trend
- issue rate / ANR rate
- top visible crash groups
- live listing copy and asset inventory

### Metrics Still Missing But Not Blocking Initial Option Design

These are still useful, but they do not block lead review of optimization options:

- exact uninstall rate
- exact D30 retention value
- review-theme summary from a larger review sample
- source-specific search CVR and browse CVR
- device / country crash concentration
- full tablet / locale screenshot audit

### Conclusion

- `Yes`: the baseline is now sufficient to prepare clear optimization options for discussion with lead.
- `No`: the baseline is not yet strong enough to justify immediate implementation of one option without review.

## Crashlist Review

Crashlist has already been checked and is materially important to the decision.

### Why Crashlist Matters Here

- overall issue rate is `3.34%`, which is already above a bad-behavior threshold
- crash-free users are only `92.9%`
- the top issue list includes crashes on:
  - main activity lifecycle
  - widget update / widget rendering flow
  - interstitial-related navigation flow
  - widget selection flow
- these are not obscure background-only errors; they touch important user journeys

### Most Important Visible Crash Risks

1. `AbsAppWidgetProvider$onUpdateWidgetWithSize$1.invokeSuspend -> IllegalArgumentException`
   - This is the biggest visible issue by event share.
   - It likely hits real widget rendering / update behavior, which is core product value.
   - This is the strongest evidence that product quality is directly tied to retention and rating risk.

2. `Hilt_MainActivity.onDestroy -> IllegalStateException`
   - High affected-user count.
   - Touches the app shell / main lifecycle.
   - This can distort both user experience and measurement quality.

3. Interstitial-related `IllegalStateException` issues
   - Present in home flow and widget selection flow.
   - These strengthen the case that monetization flow and stability are connected, not separate.

### Crashlist Conclusion

- `Quality` is not a side concern in this app.
- Any monetization change that increases user pressure before the top crash groups are understood carries risk.
- Lead review should treat `quality-first` or `quality-plus-light-monetization-cleanup` as serious options, not optional cleanup work.

## Optimization Options For Lead Review

Do not implement any of these yet.

These are candidate Phase 2 directions for decision review only.

### Option 1: Quality First

- Summary:
  - Fix the highest-impact crash groups before monetization changes.

- Why this option exists:
  - issue rate `3.34%`
  - crash-free users only `92.9%`
  - visible top crashes affect core widget and main-app flows
  - rating trend is already negative

- What this option is trying to improve:
  - crash-free users
  - issue rate
  - retention
  - rating trend
  - long-term ad impressions and revenue stability

- Expected upside:
  - strongest protection against revenue erosion from poor UX
  - likely improves user trust and repeat usage

- Main risk:
  - slower short-term revenue experimentation
  - may not show immediate revenue lift in the first few days

- Best use case:
  - choose this if lead wants the safest foundation before monetization testing

### Option 2: Retention First

- Summary:
  - Reduce first-session friction and improve return behavior before trying to increase ad revenue pressure.

- Why this option exists:
  - D1 `7.0%`
  - D7 `0.6%`
  - churn signal `3.72%`
  - onboarding, splash, language, and category selection have huge exposure
  - current revenue ceiling is limited if users do not come back

- What this option is trying to improve:
  - D1
  - D7
  - returning users
  - DAU / MAU
  - impressions from a larger retained base

- Expected upside:
  - expands revenue base without forcing more ads
  - more durable long-term growth path

- Main risk:
  - requires more patience to measure
  - result attribution is weaker if tracking is not improved first

- Best use case:
  - choose this if lead believes weak retention is the real bottleneck behind every other metric

### Option 3: Monetization Cleanup First

- Summary:
  - keep the strongest ad surfaces, remove or reduce the weakest pressure points first

- Why this option exists:
  - banner revenue share only `7.96%`
  - banner eCPM only `~$0.35`
  - banner has broad exposure but weak yield
  - interstitial eCPM is strongest
  - native carries most total revenue

- What this option is trying to improve:
  - revenue quality
  - user comfort
  - session depth
  - rating protection
  - keep strong monetization while reducing weak monetization

- Most likely change pattern:
  - review / reduce `HOME_BANNER_ADS`
  - keep preview/detail native
  - keep high-intent interstitials
  - review bottom-nav interstitial frequency

- Expected upside:
  - fastest monetization experiment to run
  - easiest to compare before vs after

- Main risk:
  - if retention is already very weak, monetization cleanup alone may not create enough business lift
  - if crashes remain high, revenue movement may be confounded

- Best use case:
  - choose this if lead wants a low-cost, reversible monetization test before deeper product work

### Option 4: Store Conversion First

- Summary:
  - improve listing assets and country targeting to lift install conversion.

- Why this option exists:
  - overall listing CVR is only `23.63%` and trending down
  - some markets have low scale or weaker conversion quality
  - screenshot and asset coverage is incomplete beyond phone

- What this option is trying to improve:
  - visitors -> install conversion
  - traffic efficiency
  - install volume in stronger-value markets

- Expected upside:
  - cleaner top-of-funnel growth
  - can support higher scale in countries with good monetization

- Main risk:
  - poor retention or crash quality can waste new installs
  - ASO gains do not help much if first-session product experience remains weak

- Best use case:
  - choose this if lead wants acquisition work in parallel but not as the only first move

## Recommended Lead Discussion Order

Present the options in this order:

1. `Quality First`
2. `Retention First`
3. `Monetization Cleanup First`
4. `Store Conversion First`

### Why This Order

- quality risk is already high enough to distort every downstream metric
- retention is visibly weak enough to cap scale
- monetization cleanup is attractive, but should be reviewed in the context of quality and retention
- store conversion is useful, but least compelling as the sole first move right now

## Current Recommendation Status

- `Can we produce optimization options now?` Yes.
- `Can we responsibly implement one option right now without lead confirmation?` No.
- `Can we already rank the options?` Yes.

### Current Ranked Recommendation

1. `Quality First`
2. `Retention First`
3. `Monetization Cleanup First`
4. `Store Conversion First`

### Why Quality First Is Currently Ranked Highest

- issue rate is already dangerous
- crashlist touches core widget and app-shell flows
- poor stability can suppress:
  - retention
  - rating
  - sessions
  - ad exposure
  - measurement reliability

### Why Monetization Cleanup Is Not Ranked First Yet

- it is the easiest experiment
- but it does not address the most structurally dangerous problem
- crashlist evidence makes it unsafe to treat monetization as the only first lever

## Required Tracking Before Any Serious Optimization Cycle

Current tracking is not strong enough for reliable screen-level monetization diagnosis.

### Tracking To Add

- screen funnel events:
  - `home_open`
  - `special_open`
  - `preview_open`
  - `detail_open`
  - `customize_open`
  - `wallpaper_open`
- action events:
  - `widget_click`
  - `preview_to_customize_click`
  - `set_widget_click`
  - `set_widget_success`
  - `save_widget_click`
  - `save_widget_success`
  - `rewarded_unlock_click`
  - `rewarded_unlock_complete`
- ad exposure events:
  - `home_banner_impression`
  - `special_banner_impression`
  - `customize_banner_impression`
  - `native_preview_impression`
  - `native_detail_impression`
  - `interstitial_onboarding_exit_impression`
  - `interstitial_bottom_nav_impression`
  - `interstitial_preview_to_customize_impression`
  - `interstitial_customize_save_impression`

### Tracking Purpose

These events are needed to answer:

- which screens create revenue
- which screens create friction
- whether revenue changes came from better yield or worse UX
- whether banner removal reduces revenue or simply reallocates value to stronger surfaces

### Code / Implementation Audit To Perform

- verify which ad callbacks are available from current AppLovin integration
- map each event to:
  - existing callback
  - missing callback
  - estimated code effort
- define naming standard so the same event model can be reused across apps

## Post-Launch Tracking Matrix

This is the minimum reporting package that should accompany any approved optimization rollout.

### Primary KPIs

- total ad revenue
- ad revenue by format
- ARPDAU
- active users:
  - 1 day
  - 7 day
  - 30 day
- D1 retention
- D7 retention
- crash-free users
- issue rate
- rating trend

### Secondary KPIs

- listing visitors
- listing CVR
- views per active user
- engagement time per active user
- engaged sessions per active user
- top-screen revenue contribution
- country-level revenue movement for:
  - Brazil
  - Mexico
  - Turkey
  - Indonesia
  - United States

### Guardrail KPIs

- issue rate must not worsen materially
- rating trend must not deteriorate further
- D1 and D7 must not drop materially
- top crash groups must not spike
- banner or interstitial cleanup must not cause a large revenue loss without engagement gain

### Format-Specific KPIs For Ad Changes

- revenue by format
- eCPM by format
- fill rate by format
- show rate by format
- impressions by format
- impressions per DAU

### Funnel KPIs For Retention Changes

- onboarding exposure
- onboarding completion
- language screen completion
- category favorite completion
- first widget success
- return rate after first session

## Reporting Standard After Rollout

Every rollout report should answer these questions explicitly:

1. What changed?
2. What did not change?
3. What date did the rollout start?
4. What window is used for comparison?
5. Did the main KPI improve?
6. Did any guardrail KPI worsen?
7. Should the change be kept, reverted, or revised?

### Short Window Report

Use after `3 days` only for fast monetization or UI-pressure tests.

Report:

- total ad revenue
- revenue by format
- active users
- engagement time
- issue rate
- rating / review anomalies

### Standard Window Report

Use after `7 days` for most decisions.

Report:

- all primary KPIs
- format breakdown if ads changed
- top-screen movement if funnel changed
- country movement if listing / geo targeting changed

### Confidence Window Report

Use after `14 days` for retention-sensitive decisions.

Report:

- D1 and D7 confirmed movement
- stability trend
- rating trend
- whether the effect held after early novelty

## Phase 2 Strategy Output Template

After all baseline data is filled, this exact section should be completed.

### Selected Direction

- Primary direction: `TBD after baseline`
- Selected on: `TBD`
- Reason this was selected over alternatives: `TBD`

### Root Cause

- Main root cause: `TBD`
- Supporting evidence:
  - `TBD`
  - `TBD`
  - `TBD`

### Goal Of The Selected Direction

- Business goal: `TBD`
- User impact goal: `TBD`
- Metrics expected to improve: `TBD`

### What Will Be Changed

- Product changes: `TBD`
- Ad placement changes: `TBD`
- Store/listing changes: `TBD`
- Tracking changes: `TBD`
- Code changes: `TBD`

### Why This Is The Best First Move

- Why not ASO first: `TBD`
- Why not retention first: `TBD`
- Why not quality first: `TBD`
- Why not monetization first: `TBD`

## Experiment Design Standard

Every future optimization cycle should use this structure.

### Experiment Header

- Experiment name: `TBD`
- Owner: `TBD`
- Start date: `TBD`
- End date: `TBD`
- Markets included: `TBD`
- App version: `TBD`

### Experiment Scope

- One-line hypothesis: `TBD`
- What changes: `TBD`
- What does not change: `TBD`
- Required code/config work: `TBD`

### Success Metrics

- primary metric: `TBD`
- secondary metrics:
  - `TBD`
  - `TBD`
  - `TBD`
- guardrail metrics:
  - issue rate
  - rating trend
  - retention

### Decision Rule

- Keep if: `TBD`
- Revert if: `TBD`
- Revise if: `TBD`

## Standard Observation Windows

Use these default windows unless app scale requires longer.

- Baseline capture window: `Last 28 days vs previous 28 days`
- Short experiment window: `3 days`
  - use only for obvious monetization exposure changes such as banner off/on
- Standard experiment window: `7 days`
  - use for most in-app monetization or funnel changes
- Retention-sensitive window: `14 days`
  - use when onboarding or first-session changes need D7 visibility
- Quality-sensitive window: `14 days`
  - use when crash fixes or behavior changes may affect stability

## Target Metrics By Time Horizon

These are planning targets, not commitments. Final numbers should be tuned after the complete baseline is known.

### After 3 Days

Use only for fast-read experiments.

- no material drop in total ad revenue beyond an acceptable threshold decided before release
- no material drop in active users
- no negative spike in issue rate
- no obvious negative review wave

Suggested practical guardrails:

- total ad revenue: not worse than `-10%` unless engagement clearly improves
- issue rate: should not worsen beyond `+0.20pp`
- rating trend: should not show a visible new negative swing

### After 7 Days

Use for the first serious optimization read.

- primary experiment metric should show directional improvement
- guardrail metrics should remain stable or improve
- if monetization changed, engagement should not deteriorate materially

Suggested practical targets:

- `Quality First`
  - issue rate down materially from `3.34%`
  - crash-free users above current `92.9%`
- `Retention First`
  - D1 above current `7.0%`
  - D7 above current `0.6%`
  - active users and engagement moving up
- `Monetization Cleanup First`
  - revenue stable or improved
  - banner revenue loss offset by stronger session / retention behavior
- `Store Conversion First`
  - listing CVR above current `23.63%`

### After 14 Days

Use for decision confidence.

- improvement should remain visible after novelty effects
- D7-sensitive metrics should be readable
- rating and issue trends should remain acceptable

Suggested practical targets:

- issue rate clearly below current `3.34%`
- D1 and D7 direction sustained
- DAU / 7-day active users improving vs baseline
- rating trend stabilized or improving
- if monetization changed, ARPDAU stable to higher without guardrail damage

## Phase 1 Working Plan

### Step 1. Complete The Baseline

- fill every missing row in the checklist
- use exact date ranges
- mark `Not available` where data truly does not exist

### Step 2. Summarize Review Themes

- manually review recent Play reviews
- group into 3 to 5 complaint themes
- group into 3 to 5 positive themes

### Step 3. Confirm Tracking Gaps

- audit current Firebase + AppLovin callbacks
- list which events already exist and which must be added

### Step 4. Rank Bottlenecks

- assign each major problem a severity:
  - `Critical`
  - `High`
  - `Medium`
  - `Low`
- rank by business impact, not by convenience

### Step 5. Select The First Optimization Direction

- write one recommended Phase 2 direction
- explain why it wins against the other options

### Step 6. Define The First Rollout

- define exact change list
- define metric targets
- define rollback rules

## Phase 1 Decision Log

Use this section to record the final conclusion after the baseline is complete.

### Decision Summary

- Final selected direction: `Not decided yet`
- Date selected: `TBD`
- Chosen because: `TBD`

### Expected Improvement

- Primary business metric to improve: `TBD`
- User behavior metric to improve: `TBD`
- Quality / guardrail metric to protect: `TBD`

### Follow-Up Plan

- Next document: `PLAN_OPTIMIZE_WIDGETS_VAULT_PHASE_2.md`
- Phase 2 purpose: first live optimization cycle
- Planned start condition:
  - baseline completed
  - decision signed off
  - required tracking list finalized

## Notes For Reuse As Template

When reused for another app:

- keep the structure
- replace only app context, known facts, and tracked metrics
- do not skip the baseline phase
- do not choose a monetization direction before quality, retention, and store data are visible in one document
