# Luftfeuchte Tracker

Ein einfacher Web‑Client zum Erfassen und Auswerten von Luftfeuchte‑Messungen mit Firebase Firestore und E‑Mail/Passwort‑Login.

## Inhalte
- `index.html`: Hauptanwendung mit Formular, Tabellenansicht, Login-Dialog (Firebase Auth) und Wetterintegration.
- `chart-popup.html`: Popup‑Seite mit Diagrammen (Chart.js).
- `server.js`: Einfache Node‑HTTP‑Variante (wird aktuell nicht verwendet, siehe Startanleitung).
- `package.json`: npm‑Konfiguration, Startskript mit http-server.

## Voraussetzungen
- Node.js (empfohlen) ODER Python (Alternative)
- Ein Firebase‑Projekt mit aktivierter Authentication (E‑Mail/Passwort) und Firestore

## Konfiguration (Firebase)
1. Öffne `index.html` und prüfe die Firebase‑Konfiguration in
   `firebaseConfig` (apiKey, authDomain, projectId, ...). Diese müssen zu deinem Projekt passen.
2. Firebase Console → Authentication → Sign-in method → E‑Mail/Passwort aktivieren.
3. Firebase Console → Authentication → Settings → Authorized domains → `localhost` hinzufügen.
4. Optional: Lege in Authentication → Users einen Test‑Benutzer (E‑Mail/Passwort) an.

## Start mit npm (empfohlen)
1. Abhängigkeiten sind bereits eingetragen (http-server als Dev‑Dependency). Falls nötig:
   ```bash
   npm i
   ```
2. Development‑Server starten:
   ```bash
   npm run start
   ```
3. Im Browser öffnen:
   - http://localhost:5173

Beim Start erscheint ein Login‑Dialog. Melde dich mit deinem in Firebase angelegten Benutzer an. Erst danach werden Daten geladen/geschrieben.

## Alternative: Start mit Python
Falls kein Node.js vorhanden ist:
```bash
python -m http.server 8000
```
Danach im Browser:
- http://localhost:8000/index.html

Hinweis: Für Firebase Auth ist der Betrieb über http(s) erforderlich (nicht file://). localhost ist in der Regel erlaubt, solange er in den Authorized Domains steht.

## Diagramm‑Popup
- Klicke in `index.html` auf die Überschrift "📊 Messungen".
- Erlaube Popups im Browser, damit `chart-popup.html` geöffnet werden kann.

## Häufige Probleme
- Port belegt (EADDRINUSE): Passe den Port im Startskript in `package.json` an, z. B. `http-server -p 5174`.
- Auth funktioniert nicht:
  - E‑Mail/Passwort in Firebase aktiviert?
  - `localhost` zu Authorized Domains hinzugefügt?
  - Stimmt die `firebaseConfig`?
- Leere Daten/Fehler beim Laden: Prüfe Firestore‑Regeln und ob die Sammlung `measurements` existiert.

## Skripte
- Start (http-server auf Port 5173):
  ```bash
  npm run start
  ```

## Lizenz
Siehe `package.json` (ISC).
