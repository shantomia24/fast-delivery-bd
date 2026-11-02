# ফাস্ট ডেলিভারি — Flutter Android Starter

এটি প্রাথমিক কোড/প্রোটোটাইপ। এখনই সম্পূর্ণ production-ready courier platform নয়।

## এই সংস্করণে আছে
- বাংলা Android অ্যাপের প্রাথমিক হোম স্ক্রিন
- পার্সেল বুকিং ফর্ম
- প্রেরক/প্রাপক, ঠিকানা, ওজন ও পেমেন্ট পদ্ধতির ইনপুট
- অর্ডার ডাটা মডেল
- Firestore-এ অর্ডার তৈরি/অ্যাসাইন/স্ট্যাটাস আপডেটের সার্ভিস
- প্রাথমিক Firestore Security Rules

## কম্পিউটার দিয়ে চালানোর ধাপ
1. Flutter SDK ও Android Studio ইনস্টল করুন।
2. নতুন Flutter project তৈরি করে এই ZIP-এর `lib`, `pubspec.yaml` ফাইল কপি করুন।
3. `flutter pub get` চালান।
4. Firebase Console-এ project তৈরি করুন এবং Android app যোগ করুন।
5. `flutterfire configure` চালিয়ে `firebase_options.dart` তৈরি করুন।
6. `lib/main.dart`-এ Firebase initialize করার import ও লাইন uncomment করুন।
7. Firebase Authentication-এ Phone বা Email/Password sign-in চালু করুন।
8. Firestore Database তৈরি করে `firestore.rules` প্রকাশ করুন।
9. `BookingScreen`-এর `_submit()`-এ authentication যুক্ত হওয়ার পর `OrderService().createOrder(order)` চালু করুন।
10. `flutter run` দিয়ে পরীক্ষা করুন।

## গুরুত্বপূর্ণ নিরাপত্তা
- Firebase service account key, API secret বা bKash/Nagad/Rocket merchant secret কখনো অ্যাপে লিখবেন না।
- Admin role ব্যবহারকারী নিজে তৈরি করতে পারবে না; নিরাপদ backend/Cloud Function দিয়ে admin নিয়োগ করতে হবে।
- Payment provider-এর অনুমোদিত merchant account ও server-side verification প্রয়োজন।
- প্রকৃত distance, weight-based charge এবং live GPS tracking এখনো যুক্ত হয়নি।
- production ব্যবহারের আগে security rules, validation, phone verification, abuse protection ও privacy policy পরীক্ষা করতে হবে।

## Firestore collection প্রস্তাব
- `users`
- `riders`
- `orders`
- `payments`
- `delivery_rates`
- `delivery_tracking`

## অর্ডারের status প্রস্তাব
`pending`, `confirmed`, `assigned`, `picked_up`, `in_transit`, `delivered`, `cancelled`, `failed`
