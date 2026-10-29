# RoV Esports Equipment Tracker

A mobile-first (H5) tracker for the team's shared equipment: phones, laptops, chargers, cables, hubs and docking stations.

- **Stock**: every item with available / total units, by category.
- **On loan**: what each project has borrowed, the PIC (person in charge), and when it's due back. Overdue loans are flagged.
- **Log**: an append-only history of every item added, lent, returned, edited or removed, and who did it.

Live: https://rovesports-equipment.web.app

## Stack

A single static page (`public/index.html`) on Firebase Hosting, with Firestore for data and Firebase Auth (Google sign-in). The Firebase config is loaded from Hosting's reserved `/__/firebase/init.json`, so no keys live in this repo.

## Access

`firestore.rules` lets in any verified **@garena.com** Google account. To let in another address (for example a personal Gmail), add a document to the `allowlist` collection in the Firebase console whose **document ID is the email address in lowercase**. No fields are needed.

## Categories

| Category | Includes |
|---|---|
| Phone | Smartphones, test devices |
| Tablet | iPad, Android tablets |
| Laptop | MacBook, Dell, Windows laptops |
| Charger | Power adapters and charging bricks |
| Cable | USB-C, Lightning, HDMI and other cables |
| Hub & Dock | Dongles, USB-C hubs, docking stations, port adapters |
| Other | Anything else |

## Deploy

```bash
firebase deploy --only hosting,firestore
```

Local preview (needs `firebase login`):

```bash
firebase serve --only hosting
```
