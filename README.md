# Speed Cloud

Speed Cloud is a Flutter Android application based on the same architecture as the original RunTrack Cloud project: email-based profiles, local storage, optional Supabase cloud synchronization, an internal PIN-protected admin panel, monthly history generation, route visualization, and a GitHub Actions APK build.

## Default friend demo account

| Field | Value |
|---|---|
| Email | ALIOUICI3@gmail.com |
| Display name | ali ouici |
| City | Irkutsk |
| Demo month | 2026-05 |
| Total distance | 190.4 km |
| Number of runs | 24 |
| Speed range | 6.5–7.7 km/h |
| Admin PIN | 2026 |

When this email logs in and the demo month is missing, the app automatically creates the default profile and 24 generated runs. You can also change all friend values inside the Admin tab after unlocking the app with PIN `2026`.

## Main features

- Login by email.
- Home dashboard with monthly distance, run count, average speed, city, and pace label.
- History screen grouped by month.
- Run detail screen with route visualization.
- Settings screen with local/cloud mode indicator.
- Supabase cloud configuration by Project URL and anon/publishable key.
- Hidden Admin tab unlocked with PIN `2026`.
- Admin generation for one target email and one selected month.
- Safe month replacement: other users and other months are preserved.
- GitHub Actions workflow for Android debug APK generation.

## Local run

```bash
flutter pub get
flutter run
```

## Build APK locally

```bash
flutter build apk --debug
```

The output APK will be:

```text
build/app/outputs/flutter-apk/app-debug.apk
```

## GitHub Actions build

1. Push this project to GitHub.
2. Open the repository Actions tab.
3. Run **Build Android APK** manually, or push to `main`.
4. Download the artifact named `speed-debug-apk`.

The workflow automatically creates the Android platform folder before building, so the repository can stay small and clean.

## Supabase setup

1. Create a Supabase project.
2. Open SQL Editor.
3. Run `docs/SUPABASE_SCHEMA.sql`.
4. Copy the Project URL. Use the base URL only, for example `https://project.supabase.co`.
5. Copy the anon/publishable key. Do not use the service_role key.
6. In the app, open Settings, paste the URL and key, and save.
7. Unlock Admin, generate history, then log in from another phone using the same email.

## Important security note

This is a classroom/demo application. The Admin PIN and anon-key flow are not production-grade authentication. A production version should add Supabase Auth, row-level security policies, admin roles, audit logs, and release signing.
