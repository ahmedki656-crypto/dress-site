# Inventory Dresses Web Viewer

This project is a simple web page to display your dresses inventory stored in Firebase Firestore.

## Features

- Real-time updates: Shows dresses currently in stock (`status` field = `"in_stock"`).
- Search/filter dresses by Model, Color, or Size.
- Clean and responsive UI for mobile and desktop.

## How to use

1. Make sure you have a Firebase project with Firestore set up.
2. Upload your dresses data in a collection named `dresses`. Each dress document must have at least the fields:
   - `model` (string)
   - `color` (string)
   - `size` (string)
   - `status` (string), set `"in_stock"` for available dresses.
3. Update the Firebase config object in `index.html` with your Firebase credentials.
4. Deploy this `index.html` file to a static web hosting service (e.g., GitHub Pages).
5. Open the hosted page on any device (mobile, desktop) to see the live inventory.
6. Use the search box to filter dresses instantly.

## Notes

- The page automatically updates whenever the Firestore data changes.
- Make sure Firestore security rules allow reading from `dresses` collection for your use case.
- Customize the UI styles in `index.html` as you wish.

---

## Firebase Rules (example)

```json
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /dresses/{dressId} {
      allow read: if true;  // Adjust this for your security needs
      allow write: if false; // No writes from this web page
    }
  }
}
