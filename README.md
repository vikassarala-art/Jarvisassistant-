# Vicky — Your Jarvis-style Assistant (Android)

## ఇది ఏం చేస్తుంది
- App open చేసి "Start Listening" నొక్కితే, ఇది వినడం మొదలుపెడుతుంది.
- మీరు **"Jarvis"** అని పలికితే, "Hello Vicky, how can I help you?" అని మాట్లాడుతుంది.
- తర్వాత మీరు చెప్పిన command ప్రకారం:
  - "open instagram" → Instagram ఓపెన్ అవుతుంది
  - "open whatsapp" → WhatsApp ఓపెన్ అవుతుంది
  - "camera" → Camera ఓపెన్ అవుతుంది
  - "call" → Dialer ఓపెన్ అవుతుంది (నంబర్ చెప్తే direct call చేస్తుంది)
  - "youtube" → YouTube ఓపెన్ అవుతుంది

## ఎలా build చేయాలి
1. [Android Studio](https://developer.android.com/studio) install చేసుకోండి (ఉచితం).
2. ఈ folder మొత్తాన్ని unzip చేసి, Android Studio లో "Open" చేయండి.
3. Gradle sync అయ్యేదాకా వేచి ఉండండి (కొన్ని నిమిషాలు పట్టొచ్చు, ఇంటర్నెట్ కావాలి).
4. మీ ఫోన్‌ని USB డీబగ్గింగ్ ఆన్ చేసి కనెక్ట్ చేయండి, లేదా Emulator వాడండి.
5. Run (▶) బటన్ నొక్కండి — App మీ ఫోన్‌లో install అవుతుంది.
6. App తెరిచినప్పుడు మైక్రోఫోన్ permission అడిగితే "Allow" చేయండి.

## కొత్తగా ఏం మారింది — Background లో వినడం
ఇప్పుడు "Start Listening" నొక్కగానే ఒక **Foreground Service** మొదలవుతుంది —
మీరు App మూసేసినా, వేరే యాప్ వాడుతున్నా, ఫోన్ లాక్ చేసినా వినడం ఆగదు.
స్క్రీన్ పైన ఎప్పుడూ ఒక చిన్న notification ("Vicky is listening...") కనిపిస్తూ ఉంటుంది —
ఇది Android నియమం, తీసేయలేం (ఇది లేకపోతే OS service ని చంపేస్తుంది).
ఆపాలంటే "Stop Vicky" నొక్కండి.

## తెలుసుకోవాల్సినవి (Real-world Limitations)
- Android లో నిజమైన "always-on offline wake word" కోసం ప్రత్యేక engine (ఉదా. Picovoice
  Porcupine) వాడాలి. ఇక్కడ వాడింది Android SpeechRecognizer — ఇది పదే పదే restart
  అవుతూ వింటుంది, కాబట్టి battery కొంచెం ఎక్కువ వాడుతుంది, మరియు Xiaomi/Vivo/Oppo లాంటి
  ఫోన్లలో battery optimization వల్ల service మధ్యలో ఆగిపోవచ్చు — Settings లో ఈ App కి
  "No battery restriction" / "Allow background activity" ఇవ్వాల్సి రావొచ్చు.
- "call" command కోసం CALL_PHONE permission allow చేయాలి.
- Instagram/WhatsApp/YouTube commands పనిచేయాలంటే ఆ apps ఫోన్‌లో already install అయ్యుండాలి.
- Android 13+ లో notification permission కూడా allow చేయాలి (App అడుగుతుంది).

## తర్వాత ఏం add చేయొచ్చు
- నిజమైన offline wake-word engine (Porcupine) — తక్కువ battery, ఎక్కువ accuracy
- ఇంకా commands: "send message to X", "open maps", "play music"
- Custom app icon, launcher name

Doubts ఉంటే చెప్పండి — code modify చేసి ఇస్తాను.
