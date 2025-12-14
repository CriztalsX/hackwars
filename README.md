# 🎮 HACK WARS

Ett multiplayer hacker-spel där du skyddar ditt konto och försöker hacka andra spelare!

## 🚀 Spela Nu

Spelet är live på: https://criztalsx.github.io/hackwars/

## ✨ Features

- **Multiplayer i realtid** - Spela mot andra spelare live
- **Tjäna Creds** - Klicka för att tjäna eller köp passiv inkomst
- **Hack andra spelare** - Samla ledtrådar och gissa lösenord
- **Köp Försvar** - Skydda dig med 2FA, VPN, Honeypot, Counter-Hack och mer
- **Operator Panel** - Admin-panel för spelhantering
- **Anti-Cheat System** - Automatisk detektion av fusk

## 🎯 Hur Man Spelar

1. **Skapa ett konto** - Välj användarnamn och lösenord (max 8 tecken, a-z och 0-9)
2. **Tjäna Creds** - Klicka på "TJÄNA CREDS" knappen eller köp upgrades för passiv inkomst
3. **Scanna Nätverk** - Hitta andra spelare att attackera
4. **Samla Ledtrådar** - Betala för ledtrådar om andras lösenord
5. **Hacka!** - Gissa rätt lösenord och stjäl alla deras creds
6. **Köp Försvar** - Skydda dig själv med olika försvar

## 🔧 Installation för GitHub Pages

### Steg 1: Ladda upp till GitHub

1. Skapa ett nytt repository på GitHub
2. Ladda upp alla filer från detta repo
3. Gå till **Settings** > **Pages**
4. Under "Source", välj **main** branch
5. Klicka **Save**

### Steg 2: Firebase Setup

Spelet använder Firebase för multiplayer. Du behöver din egen Firebase-konfiguration:

1. Gå till [Firebase Console](https://console.firebase.google.com/)
2. Skapa ett nytt projekt eller använd ett befintligt
3. Lägg till en **Web App**
4. Kopiera Firebase-konfigurationen
5. Öppna `index.html` och ersätt Firebase-konfigurationen (rad ~943-951) med din egen:

```javascript
const firebaseConfig = {
    apiKey: "DIN-API-KEY",
    authDomain: "DITT-PROJECT.firebaseapp.com",
    databaseURL: "https://DITT-PROJECT.firebaseio.com",
    projectId: "DITT-PROJECT",
    storageBucket: "DITT-PROJECT.appspot.com",
    messagingSenderId: "DIN-SENDER-ID",
    appId: "DITT-APP-ID"
};
```

### Steg 3: Firebase Realtime Database Setup

1. I Firebase Console, gå till **Realtime Database**
2. Klicka **Create Database**
3. Välj en location (välj närmaste region)
4. Starta i **Test mode** (kan ändras senare)
5. Gå till **Rules** och använd dessa regler för produktion:

```json
{
  "rules": {
    "users": {
      "$username": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

**OBS:** För bättre säkerhet, lägg till validering och begränsa skrivåtkomst!

## 🎮 Operator Panel

Operator-panelen är skyddad med ett lösenord. Standard-lösenordet finns i koden (rad ~2637).

**Funktioner:**
- Se alla användare och deras stats
- Radera användare
- Återställ alla lösenord
- Ge alla användare creds
- Rensa korrupta konton

## 🔒 Säkerhet

- **Anti-Cheat:** Automatisk detektion av fusk (spam, omöjliga vinster)
- **Rate Limiting:** Max 1000 creds/sek från klick, 50k creds/min totalt
- **Failed Hack Lockout:** 5 misslyckade hack-försök = 24h lockout
- **Input Validering:** Alla inputs valideras

## 🛠️ Teknisk Stack

- **Frontend:** Vanilla JavaScript (ES6+)
- **Database:** Firebase Realtime Database
- **Styling:** Custom CSS med monospace font
- **Hosting:** GitHub Pages

## 📱 Kompatibilitet

- ✅ Desktop browsers (Chrome, Firefox, Safari, Edge)
- ✅ Mobile browsers
- ✅ Fungerar utan server (static hosting)

## 🎨 Anpassning

### Ändra Färger

Sök efter färgkoder i CSS:
- `#000` - Svart bakgrund
- `#fff` - Vit text/borders
- `#0f0` - Grön (success)
- `#f00` - Röd (errors/danger)

### Justera Spelbalans

Justera värden i koden:
- **Starting Creds:** Rad ~1599 (`creds: 100`)
- **Upgrade Costs:** Rad ~1467-1515
- **Defense Costs:** Rad ~1461-1465
- **Clue Gathering Costs:** Rad ~2243-2251
- **Anti-Cheat Limits:** Rad ~1001-1024

## 🐛 Felsökning

**Problem: Multiplayer fungerar inte**
- Kontrollera att Firebase-konfigurationen är korrekt
- Verifiera att Realtime Database är aktiverad
- Kolla Database Rules (måste tillåta read/write)

**Problem: "Undefined" användare skapas**
- Rensa dessa med Operator Panel > "RENSA KORRUPTA KONTON"

**Problem: Spelare ser inte varandra**
- Alla måste använda samma Firebase-databas
- Kolla att databaseURL är korrekt

## 📄 Licens

Detta projekt är open source och fritt att använda!

## 🤝 Contributing

Pull requests välkomna! För större ändringar, öppna en issue först.

## 🎯 Roadmap

- [ ] Leaderboard med tidsfilter
- [ ] Achievements system
- [ ] Chat mellan spelare
- [ ] Mer försvar och attacktyper
- [ ] Mobile app version

---

**Skapat med ❤️ för hacker-communities**

Lycka till och hacka väl! 💀🔓
