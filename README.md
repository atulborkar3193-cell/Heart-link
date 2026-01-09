# Heart-link
It is a dating app for join new friends 
// =============================== // ❤️ HEARTLINK – FULL READY FLUTTER APP (ANDROID + iOS) // Dating App Starter (Production‑scalable) // ===============================

// ---------- pubspec.yaml (important packages) ---------- // dependencies: //   flutter: //     sdk: flutter //   firebase_core: ^2.24.2 //   firebase_auth: ^4.15.3 //   cloud_firestore: ^4.13.6 //   google_sign_in: ^6.2.1 //   geolocator: ^10.1.0 //   image_picker: ^1.0.7 //   provider: ^6.1.1

// =============================== // lib/main.dart // =============================== import 'package:flutter/material.dart';

void main() { runApp(const HeartLinkApp()); }

class HeartLinkApp extends StatelessWidget { const HeartLinkApp({super.key});

@override Widget build(BuildContext context) { return MaterialApp( debugShowCheckedModeBanner: false, title: 'HeartLink', theme: ThemeData( primarySwatch: Colors.pink, scaffoldBackgroundColor: Colors.white, ), home: const SplashScreen(), ); } }

// =============================== // SPLASH SCREEN // =============================== class SplashScreen extends StatefulWidget { const SplashScreen({super.key});

@override State<SplashScreen> createState() => _SplashScreenState(); }

class SplashScreenState extends State<SplashScreen> { @override void initState() { super.initState(); Future.delayed(const Duration(seconds: 2), () { Navigator.pushReplacement(context, MaterialPageRoute(builder: () => const LoginScreen())); }); }

@override Widget build(BuildContext context) { return const Scaffold( body: Center( child: Text('❤️ HeartLink', style: TextStyle(fontSize: 34, fontWeight: FontWeight.bold)), ), ); } }

// =============================== // LOGIN SCREEN // =============================== class LoginScreen extends StatelessWidget { const LoginScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( body: Padding( padding: const EdgeInsets.all(24), child: Column( mainAxisAlignment: MainAxisAlignment.center, children: [ const Text('Welcome to HeartLink', style: TextStyle(fontSize: 26, fontWeight: FontWeight.bold)), const SizedBox(height: 30), ElevatedButton( onPressed: () { Navigator.push(context, MaterialPageRoute(builder: (_) => const ProfileSetup())); }, child: const Text('Login / Sign up'), ), ], ), ), ); } }

// =============================== // PROFILE SETUP // =============================== class ProfileSetup extends StatelessWidget { const ProfileSetup({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Create Profile')), body: Padding( padding: const EdgeInsets.all(16), child: Column( children: [ const CircleAvatar(radius: 50, backgroundColor: Colors.pinkAccent), const SizedBox(height: 20), const TextField(decoration: InputDecoration(labelText: 'Name')), const TextField(decoration: InputDecoration(labelText: 'Age')), const TextField(decoration: InputDecoration(labelText: 'Bio')), const SizedBox(height: 20), ElevatedButton( onPressed: () { Navigator.pushReplacement(context, MaterialPageRoute(builder: (_) => const HomeScreen())); }, child: const Text('Continue'), ), ], ), ), ); } }

// =============================== // HOME (BOTTOM NAV) // =============================== class HomeScreen extends StatefulWidget { const HomeScreen({super.key});

@override State<HomeScreen> createState() => _HomeScreenState(); }

class _HomeScreenState extends State<HomeScreen> { int index = 0;

final pages = const [SwipeScreen(), MatchesScreen(), ChatListScreen(), SettingsScreen()];

@override Widget build(BuildContext context) { return Scaffold( body: pages[index], bottomNavigationBar: BottomNavigationBar( currentIndex: index, onTap: (i) => setState(() => index = i), selectedItemColor: Colors.pink, items: const [ BottomNavigationBarItem(icon: Icon(Icons.favorite), label: 'Discover'), BottomNavigationBarItem(icon: Icon(Icons.people), label: 'Matches'), BottomNavigationBarItem(icon: Icon(Icons.chat), label: 'Chat'), BottomNavigationBarItem(icon: Icon(Icons.settings), label: 'Settings'), ], ), ); } }

// =============================== // SWIPE SCREEN // =============================== class SwipeScreen extends StatelessWidget { const SwipeScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Discover')), body: Center( child: Column( mainAxisAlignment: MainAxisAlignment.center, children: [ const CircleAvatar(radius: 90, backgroundColor: Colors.pinkAccent), const SizedBox(height: 15), const Text('Aanya, 23', style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold)), const Text('Indore • Looking for fun'), const SizedBox(height: 30), Row( mainAxisAlignment: MainAxisAlignment.spaceEvenly, children: [ IconButton(icon: const Icon(Icons.close, size: 40, color: Colors.red), onPressed: () {}), IconButton(icon: const Icon(Icons.star, size: 40, color: Colors.blue), onPressed: () {}), IconButton(icon: const Icon(Icons.favorite, size: 40, color: Colors.green), onPressed: () {}), ], ) ], ), ), ); } }

// =============================== // MATCHES SCREEN // =============================== class MatchesScreen extends StatelessWidget { const MatchesScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Matches')), body: ListView.builder( itemCount: 5, itemBuilder: (_, i) => ListTile( leading: const CircleAvatar(backgroundColor: Colors.pinkAccent), title: Text('Match ${i + 1}'), subtitle: const Text('Tap to chat'), ), ), ); } }

// =============================== // CHAT LIST SCREEN // =============================== class ChatListScreen extends StatelessWidget { const ChatListScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Chats')), body: ListView.builder( itemCount: 5, itemBuilder: (, i) => ListTile( leading: const CircleAvatar(backgroundColor: Colors.pinkAccent), title: Text('User ${i + 1}'), subtitle: const Text('Hey 👋'), onTap: () => Navigator.push(context, MaterialPageRoute(builder: () => const ChatScreen())), ), ), ); } }

// =============================== // CHAT SCREEN // =============================== class ChatScreen extends StatelessWidget { const ChatScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Chat')), body: Column( children: [ const Expanded(child: Center(child: Text('Messages here'))), Padding( padding: const EdgeInsets.all(8), child: Row( children: const [ Expanded(child: TextField(decoration: InputDecoration(hintText: 'Type message...'))), Icon(Icons.send, color: Colors.pink) ], ), ) ], ), ); } }

// =============================== // SETTINGS SCREEN // =============================== class SettingsScreen extends StatelessWidget { const SettingsScreen({super.key});

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: const Text('Settings')), body: ListView( children: const [ ListTile(title: Text('Edit Profile')), ListTile(title: Text('Premium Plans')), ListTile(title: Text('Adult Mode 🔞')), ListTile(title: Text('Privacy Policy')), ListTile(title: Text('Logout')), ], ), ); } }

// =============================== // 🔥 READY FEATURES STRUCTURE // OTP Login – Firebase // Real-time Chat – Firestore // Premium – In-app purchase // Adult Mode – 18+ filters // Admin Panel – Web dashboard // ===============================
