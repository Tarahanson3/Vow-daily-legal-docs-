# VowDaily — Complete Pre-Launch To Do List

---

## SECTION 1 — RORK FIXES (finish these first)

- [ ] Push final clean build to TestFlight with ALL recent fixes included:
  - KJV Bible verses throughout (replacing NIV)
  - Photo/camera permission action sheet (Take a Photo vs Choose from Library)
  - Support form connected to GHL webhook
  - Onboarding flow — account creation moved to end
  - Privacy policy and terms URLs updated to clean vowdaily.app versions
  - Content rotation fix (400 templates in Supabase, no repeats)
  - Date night favorites and plans saving correctly to Supabase
  - Check-in again button saving previous and showing new form
  - Reflection notes and check-in notes showing in calendar
  - Calendar visual redesign (green completed days, gray missed, icons)
  - Date night suggestion tab layout fixed
  - Paywall loading popup removed
  - Log out button in Settings
  - {spouse_name} placeholder substitution working everywhere
  - onboarding_completed flag logic working correctly
  - Review prompt changed to 3-day streak trigger
  - Product IDs updated to com.vowdaily.premium.monthly and com.vowdaily.premium.annual

- [ ] Test the final TestFlight build end to end:
  - Full onboarding flow works
  - Prayer generates with spouse name
  - Action of the day shows correctly
  - Paywall shows correct pricing ($4.99 monthly, $39.99 annual)
  - Free trial label shows
  - Check-in feature works
  - Calendar shows green completed days correctly
  - Favorites and date night plans persist after closing app
  - Support form submits and lands in GHL
  - Privacy policy and terms links open correctly
  - Delete account works
  - Log out works

---

## SECTION 2 — GHL EMAIL SETUP

- [ ] Go to GHL → Settings → Email Services → LC Email → click Get Started
- [ ] Click Add Sending Domain → type vowdaily.app
- [ ] GHL gives you DNS records (SPF, DKIM, DMARC) — copy these
- [ ] Go to GoDaddy → vowdaily.app domain → DNS settings
- [ ] Add all DNS records GHL gave you (SPF, DKIM, DMARC)
- [ ] Come back to GHL LC Email → click Verify (wait up to 30 mins)
- [ ] Once verified create support@vowdaily.app as your mailbox
- [ ] TEST: Send an email from your personal Gmail to support@vowdaily.app
- [ ] Confirm it lands in GHL Conversations inbox
- [ ] Update your GHL workflow auto-reply From Email to support@vowdaily.app
  (currently using GHL default — change once domain email is verified)

---

## SECTION 3 — GITHUB AND VERCEL UPDATES

- [ ] Download the updated privacy-policy.html from this document
  (added unique user identifier to section 02 — Information We Collect)
- [ ] Go to github.com/Tarahanson3/Vow-daily-legal-docs-
- [ ] Upload updated privacy-policy.html to replace existing file
- [ ] Commit changes — Vercel redeploys automatically in 30 seconds
- [ ] Visit https://www.vowdaily.app/privacy-policy and confirm the
  new bullet "A unique user identifier" appears in section 02

---

## SECTION 4 — SUPABASE (if not already done)

- [ ] SQL Editor → run migration for onboarding_completed column:
  ALTER TABLE profiles ADD COLUMN IF NOT EXISTS onboarding_completed boolean DEFAULT false;
- [ ] SQL Editor → run migration for date night tables:
  (date_night_favorites and date_night_plans — run the SQL from our conversation)
- [ ] Confirm 400+ rows in daily_content table (Supabase → Table Editor → daily_content)
- [ ] Confirm both edge functions are deployed:
  Supabase → Edge Functions → confirm delete-account and generate-daily-content both show

---

## SECTION 5 — APP STORE CONNECT

### App listing (do before screenshots so you know what to say)

- [ ] Go to appstoreconnect.apple.com → VowDaily → 1.0 Prepare for Submission
- [ ] App Name: VowDaily
- [ ] Subtitle: Pray for your spouse daily (26 chars)
- [ ] Keywords (paste exactly, 99 chars):
  couples prayer,christian marriage,biblical marriage,marriage devotional,love language,date night,faith,pray together,marriage app,spouse
- [ ] Description: use the full description from the vowdaily-aso.md file
- [ ] Support URL: https://www.vowdaily.app
- [ ] Privacy Policy URL: https://www.vowdaily.app/privacy-policy
- [ ] Primary Category: Lifestyle
- [ ] Secondary Category: Health and Fitness
- [ ] Content Rating: 4+

### App icon

- [ ] App Store Connect → VowDaily → App Information → App Icon
- [ ] Upload 1024x1024 PNG of the two interlocking hearts with cross
- [ ] No transparency, no rounded corners (Apple adds those)
- [ ] Must be exactly 1024x1024 pixels

### Screenshots (do in Canva)

For each screenshot: take a real screen capture from TestFlight on your iPhone,
bring into Canva, set background to VowDaily green (#2d5a3d), add white
headline text at top, place phone screenshot in lower 65% of canvas.

Required sizes:
- 6.7 inch: 1290 x 2796px (iPhone 16 Pro Max)
- 6.5 inch: 1242 x 2688px (iPhone 11 Pro Max)
Make both sizes for each screenshot.

- [ ] Screenshot 1 — Today tab with prayer, verse, action card
  Headline: "Pray for your spouse. Every single day."

- [ ] Screenshot 2 — Love language quiz results screen
  Headline: "Tailored to how they love."

- [ ] Screenshot 3 — Calendar with green completed days and streak counter
  Headline: "Build the habit that changes everything."

- [ ] Screenshot 4 — Date night suggestion screen with 3 ideas
  Headline: "Never run out of date night ideas."

- [ ] Screenshot 5 — Check-in screen with 2-minute timer active
  Headline: "Two minutes to serve your spouse better."

- [ ] Screenshot 6 — Calendar detail card with past prayer and photo
  Headline: "Look back on the love you've built."

- [ ] Screenshot 7 — Green Scripture quote screen from onboarding
  Headline: "A cord of three strands is not quickly broken."

- [ ] Upload all screenshots to App Store Connect in both sizes

### Privacy nutrition labels

- [ ] App Store Connect → VowDaily → App Privacy → Get Started
- [ ] Declare Name: linked to identity, app functionality
- [ ] Declare Email Address: linked to identity, authentication
- [ ] Declare User ID / Identifiers: linked to identity, app functionality
- [ ] Declare Photos: linked to identity, app functionality (premium feature)
- [ ] Declare Other User Content (notes, reflections): linked to identity, app functionality
- [ ] Declare Product Interaction / Usage Data: linked to identity, app functionality
- [ ] For AI data (OpenRouter): declare data shared with third party for app functionality,
  NOT for tracking or advertising
- [ ] Save and confirm labels match your privacy policy at vowdaily.app/privacy-policy

### Subscriptions

- [ ] On the submission page find In-App Purchases and Subscriptions section
- [ ] Click + and add VowDaily Monthly
- [ ] Click + and add VowDaily Annual
- [ ] Confirm both appear before submitting

### Test account for Apple reviewers

- [ ] Create a test account inside VowDaily app using vowdailytestreviewer@gmail.com
- [ ] Complete full onboarding (use any fake spouse name like "Alex")
- [ ] Log at least 3 days of prayers so app doesn't look empty
- [ ] In App Store Connect → submission page → App Review Information → Demo Account
  enter: vowdailytestreviewer@gmail.com and the password you used
- [ ] In Review Notes write:
  "Please start the 7-day free trial on the paywall screen to access all premium
  features during review. The app requires a spouse name during onboarding —
  feel free to use any name. Support email: support@vowdaily.app"

---

## SECTION 6 — SUBMIT FOR REVIEW

- [ ] Double check everything above is complete
- [ ] Click Add for Review on the submission page
- [ ] Click Submit to App Review
- [ ] When asked: does app use IDFA? → No
- [ ] When asked: does app use encryption beyond standard HTTPS? → No
- [ ] Submit
- [ ] Watch your email for the next 48 hours for Apple's decision
- [ ] Check support@vowdaily.app in GHL in case Apple emails during review

---

## SECTION 7 — POST-LAUNCH ASO (do after app goes live)

- [ ] Ask every friend and family member who downloads to leave an honest review
  Goal: 20+ reviews in first 2 weeks
- [ ] Post personal founder story on Instagram, Facebook, TikTok
  ("I built this for my own marriage — here's why")
- [ ] Share in Christian marriage Facebook groups (check group rules first)
- [ ] Email your existing idea-to-app funnel list about the launch
- [ ] Reach out to 10-20 Christian marriage content creators on Instagram/TikTok
  Offer free premium access in exchange for an honest review video
- [ ] Email 10-20 local pastors personally offering VowDaily for their marriage ministry
- [ ] Create Pinterest pins with Scripture quotes in VowDaily green — pin 3-5x per week
- [ ] Submit Apple feature request for Valentine's Day and National Prayer Day
  appstoreconnect.apple.com → Promotions → Request a Feature
- [ ] Monitor keyword rankings monthly and swap underperforming keywords
- [ ] Respond to every App Store review
- [ ] Generate promo codes for influencers/creators once app is live
  App Store Connect → VowDaily → Subscriptions → Offer Codes
- [ ] Set up RevenueCat manual entitlement grants for anyone helping with launch content
- [ ] Set calendar reminder for January 7, 2027 to rotate Apple Sign In secret key
  (Apple OAuth secrets expire every 6 months)
- [ ] Enable Supabase backups before first real users sign up
  Supabase → Settings → Backups → Enable

---

## QUICK REFERENCE — KEY URLS AND CREDENTIALS

- App Store Connect: appstoreconnect.apple.com
- Apple Developer: developer.apple.com
- RevenueCat: app.revenuecat.com
- Supabase: supabase.com → VowDaily project
- GitHub legal repo: github.com/Tarahanson3/Vow-daily-legal-docs-
- Vercel project: vercel.com → Vow-daily-legal-docs project
- Live privacy policy: https://www.vowdaily.app/privacy-policy
- Live terms: https://www.vowdaily.app/terms-of-service
- Support email (once set up): support@vowdaily.app
- Bundle ID: com.vowdaily.app
- Team ID: XNZV9H4JD2
- RevenueCat entitlement: premium
- Monthly product ID: com.vowdaily.premium.monthly
- Annual product ID: com.vowdaily.premium.annual
