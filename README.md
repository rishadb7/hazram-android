# HAZRAM Android App — MVP source

A native Android starter application for perfume-business operations.

## Included in this first MVP
- Dashboard: sales, expenses, estimated net profit and stock units
- Product catalogue with size, SKU, selling price, unit cost and opening stock
- Sales entry with Retail/Wholesale channel, payment method and automatic stock deduction
- GST rate per sale, GST-inclusive or GST-exclusive price handling, and taxable value/GST amount tracking
- Profit & loss calculated on taxable sales excluding collected GST
- Expense entry with category
- All-time profit & loss summary and inventory valuation
- Local Room database; core entry screens work offline

## Architecture
- Kotlin + Jetpack Compose UI
- MVVM ViewModel
- Room persistence (SQLite)
- Single local database: `hazram.db`

## Build an APK without a computer (phone-only route)
This repository includes a GitHub Actions workflow at `.github/workflows/build-apk.yml`.

1. On your Android phone, open https://github.com and create a free account or sign in.
2. Create a **new public repository** named `hazram-android` (public is simplest for GitHub Actions on a free account). Do not add a README or license during repository creation.
3. Download and extract the HAZRAM source ZIP on your phone.
4. In the new GitHub repository, use **Add file → Upload files** and upload the *contents* of the `HAZRAM` folder (including the hidden `.github` folder). If the GitHub mobile page does not show hidden files, use the browser's desktop-site option or GitHub's web editor to create `.github/workflows/build-apk.yml` using the copy in this project.
5. Commit the files to the `main` branch.
6. Open the repository's **Actions** tab. Select **Build HAZRAM APK** and tap **Run workflow** if it has not started automatically.
7. When the workflow finishes successfully, open that run, scroll to **Artifacts**, and download `HAZRAM-debug-APK`.
8. Extract the downloaded artifact ZIP and tap `app-debug.apk` to install. Android may ask you to allow installs from that browser or file manager; only allow it for the app you trust.

The cloud build requires internet access and GitHub Actions to be enabled for the repository. The APK is a debug build for testing, not a Play Store release.

## Build APK with Android Studio
Open this folder in Android Studio (Ladybug or newer), allow Gradle sync, then choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**. The debug APK will be generated at:
`app/build/outputs/apk/debug/app-debug.apk`

Command line (with Android SDK and Gradle installed):
`gradle assembleDebug`

## Important MVP limitations
This is an initial local-only build. It does not yet include cloud backup, multi-user access, invoice/PDF export, date-filtered reports, returns/refunds, GSTIN-configured statutory tax invoices and GSTR-ready exports, purchase orders, stock adjustment history, or secure login. GST rate is entered per sale and must be confirmed against the product HSN classification and current Indian GST rules; the app does not yet validate HSN rates or generate statutory GST invoices/GSTR filings. Net profit is calculated on taxable sales excluding GST, minus recorded product cost and expenses. Add those capabilities before using it as a statutory accounting system.
