AURA ARMAN TOUR - login/admin update
====================================

Files:
- TOP-UP.html: public browsing retained; likely order/payment/top-up actions redirect to login.html if no Firebase user.
- login.html: Firebase email/password sign-in using firebase.js.
- firebase.js: shared Firebase module copied from the user's supplied firebase (2).js.
- admin.html: Firebase config unified to aura-arman-tour; adds Site / API Controls.

Important:
1. Existing admin.html previously used the separate Firebase project ishan-top-971e0. It is now pointed to aura-arman-tour to match firebase.js. If existing orders/categories are only in the old project, they will not appear until migrated or the intended project is confirmed.
2. Login requires accounts to exist in Firebase Authentication. This page does not create accounts.
3. Public viewing is intentionally allowed. Firebase security rules must still prevent unauthenticated writes; client-side click interception alone is not security.
4. Site controls save to Firestore siteSettings/general. To make those values affect the public UI, TOP-UP.html must be wired to read that document; this update preserves existing public page content and doesn't blindly replace its branding/links.
5. API usage requires a valid provider usage endpoint. It cannot reveal provider limits unless the provider returns that data. Avoid saving secret provider keys in public client code.
6. Weekly/monthly product names are left as the existing catalog labels to avoid changing product pricing/categories without an explicit mapping.
