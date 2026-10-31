# Lana KI - oeffentlicher Projektstand

Revision: 4 | Zustand vom: 2026-10-30T05:28:02.697794+00:00

Diese Datei ist eine **maschinell redigierte** Fassung des internen
Projektzustands. Alle Kennungen (Tenant-, Konto-, App-, Abonnement-IDs,
Adressen, Fingerprints) sind durch Platzhalter ersetzt. Die Auflösung
liegt ausschliesslich privat. Sie wird aus
`config/lana-master-state.json` erzeugt - nicht von Hand bearbeiten.

Nachweisarten: `LIVE_VERIFIED` eigener aktueller Test | `DOCUMENTED`
in einer Quelle beschrieben | `USER_SPECIFIED` vom Betreiber festgelegt |
`UNVERIFIED` / `NEEDS_TEST` ungeprueft | `CONFLICT` widersprechende Quellen.

`DOCUMENTED` ist nicht `IMPLEMENTED` ist nicht `TESTED` ist nicht `PASS`.

## Entscheidungen

### D-PRODUCT

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Lana KI und Carpuncle Cloud sind ein gemeinsames Produkt. Bestehende Komponenten, Accounts und Apps weiterverwenden; keine parallelen Ersatzprodukte erfinden.

### D-CLOUD

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Cloud-only ist das dokumentierte Ziel; eigene Cloudserver sind damit vereinbar. Lokaler PC darf keine notwendige Produktionsgrundlage sein.

### D-GATEWAY

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Zentraler MCP-Einstieg: https://gateway.lana-ki.de/mcp. OAuth-Callback ist gesondert anhand der Implementierung zu prüfen; /mcp ist nicht automatisch Callback.

### D-TENANTS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Laut übergebenem Chat ist Tenant B <TENANT_B> (<TENANT_B_DOMAIN>) Haupttenant; A <TENANT_A> (<TENANT_A_DOMAIN>) Zweittenant. Keine neue Kontoanlage daraus ableiten.

## Verbindliche Regeln

### R-PATHS

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Genau zehn bestehende Hauptordner verwenden: .agents, .claude, .ssh, audit, config, docs, env, exports, scripts, skills. Keine neuen Hauptordner; keine Ausgaben in Downloads.

### R-CONTEXT

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Vor Antworten Projektkontext lesen, relevante Originalquellen und erreichbare Chats abgleichen; neue Ziele/Probleme/Ergebnisse mit Herkunft einpflegen.

### R-CLOSE

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Gelöste Probleme aus aktuellen Masterlisten physisch entfernen; Abschlussbeleg in audit behalten. Keine durchgestrichenen Altprobleme in aktiven Übersichten.

### R-WORK

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Vor Änderungen Work-ID und betroffene Ressourcen beanspruchen; keine widersprüchlichen Paralleländerungen.

### R-TOOLS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- PowerShell 7 über C:/Carpuncle Cloud/Tools/pwsh/pwsh.exe verwenden; Skripte als vollständige Dateien prüfen. VS Code und Ollama laut geliefertem Projektkontext ausgeschlossen.

### R-DOMAIN

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Die in der Chatquelle ausdrücklich ausgeschlossene falsche onmicrosoft-Domain nicht als Konfigurationswert verwenden; gültige Tenantzuordnung aus D-TENANTS prüfen.

### R-PRIVATE

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Keine Secret-Werte, privaten Schlüssel oder privaten Persona-Inhalte in gemeinsamen Kontext kopieren. Nur Fundort und Status aufnehmen.

### R-PC-OPTIONAL

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Direkter Nutzerbeleg vom 29.10.: alle Services einschließlich PC und Android koppeln; drei Server müssen nutzbar bleiben, wenn der lokale PC ausgeschaltet ist. PC nicht zur notwendigen Betriebsbrücke machen.

## Belegte Fakten

### F-TOOLS

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-30
- Am 29.10. auf drei Servern geprüft: Node 22.23.4, npm 10.9.9, Wrangler 4.155.0, PowerShell 7.6.9; Werkzeuglauf ist keine Gateway- oder Game-Abnahme.

### F-ENV

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-30
- Am 29.10. ReadOnly bei discord.env, oauth.env und slack.env entfernt; Schreibzugriff geprüft, Inhalts-Hashes unverändert. Kein weiterhin offenes Attributproblem aus alten Chats übernehmen.

### F-SSH

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- MEMORY-Altstand berichtet für 29.10. Mesh-Erfolg in sechs Richtungen. Schlüsselkommentare lokaler m2m-Dateien stimmen nicht notwendig mit serverseitigem Material überein. In diesem Abgleich kein erneuter Mesh-Lauf.

### F-ENTRA

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Berichtet: bestehende Entra-App Lana, Client <ENTRA_APP_CLIENT>, Object <ENTRA_APP_OBJECT> in Tenant B. Key Vault <AZURE_KEYVAULT> in <AZURE_RESOURCE_GROUP>, Subscription <AZURE_SUBSCRIPTION>; Access-Policy-Modell berichtet.

### F-GCP

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Berichtet: Organisation <GCP_ORG_NAME> / <GCP_ORG_ID>; Projekt <GCP_PROJECT_ID>; Dienstkonto-ID <GCP_SERVICE_ACCOUNT_UID> ist keine OAuth-Webclient-ID.

### F-WORLDS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Python- und Node-Welten bleiben getrennt. Aria/Thomas V0.1 ist vom UE5-/Streaming-Meilenstein getrennt; API-Vertrag ist ein Entwurf, kein Betriebsnachweis.

### F-PERMISSIONS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Permissions.xlsx ist ein uneinheitlich aufgebauter Operationskatalog, kein Nachweis zugeteilter Kontorechte.

### F-MASTER-SYNC

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-30
- Lokaler Skill lana-ki-master-sync eingerichtet; vier Masteransichten versioniert erzeugt, Originale in audit gesichert; elf Verhaltenstests und Skill-Validator bestanden. Kein universeller Zugriff auf andere KI-Dienste.

### F-REPO-WIF

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Chat vom 29.10. berichtet vorhandenes Repo <GITHUB_REPO>, vorbereiteten GitHub-OIDC-Workflow und Draft-PR 3. Claude-seitige Regel und End-to-End-Prüfung damals offen. Nicht mit alten gesperrten GitHub-Identitäten gleichsetzen; hier nicht frisch am Repository abgefragt.

### F-DOC-CONTROL

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-30
- Am 30.10. liefert Document Control keine verbundenen Dokumentsitzungen. Sechs benannte Pages sind über Pages lesbar; dies ist ein unabhängiger Zugriffspfad.

## Offene Probleme

### P-LOGIN

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- AADSTS530004 beim Invitation-Acceptance-Pfad berichtet. Konkreten Tenant-, Conditional-Access- und Gerätepfad prüfen; erfolgreicher Login als Abnahme fehlt.

### P-GATEWAY

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Gateway/MCP-End-to-End-Abnahme offen. Historisch 1033/fehlender Connector berichtet; Worker-Löschung und kontoweiter Ausschluss nicht unabhängig belegt. Routing, Auth, initialize, tools/list und Leseaufruf zusammen prüfen.

### P-WEBDAV

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Shadow-WebDAV W01–W07 aus Erstprüfung offen; außerdem unterschiedliche Shadow-Variablennamen. Vor produktiver Verwendung korrigieren und funktional prüfen.

### P-IMPORTER

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Gelieferte große Agent-ZIPs sind alte Fassungen; Importer-Logging/Quelllöschung und aktives Installationsverhalten bleiben problematisch. Korrigiertes Paket anhand Bytes und Tests abnehmen.

### P-PLUGIN

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Plugin 0.3.2: Validator/Graph-Platzhalter und unvollständige Auth-Zielprüfung. 21 Parser-PASS ersetzen keine Funktionstests.

### P-PIXEL

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Pixel-Zugang historisch mit TLS-/Tunnelproblem; erfolgreiche End-to-End-Abnahme weiterhin nicht in diesem Quellenbestand nachgewiesen. SSH und Passkey getrennt prüfen.

### P-SECRETS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Historischer Secret-Expositionsbericht und sensible Credentials-Datei vorhanden; Gültigkeit, abgeschlossene Rotation und Store-Migration nicht belegt. Keine Werte in Kontext übernehmen.

### P-AI-EVIDENCE

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- MEMORY nennt Workers-AI-Tests; die beiden verlinkten Berichte waren am angegebenen reports-Pfad nicht vorhanden. Originalbelege suchen, keine automatische Wiederholung kostenpflichtiger Tests.

### P-SCRIPT-VARIANTS

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Zwei neu gelieferte Download-Reparaturskripte unterscheiden sich von den erfolgreich verwendeten Fassungen: Serverinstaller schreibt ohne Apply und kann Wrangler-Verweis ersetzen; ENV-Skript kann fehlende/nicht beschreibbare Dateien mit Erfolg übergehen. Syntaxprüfungen bestanden, keine Ausführung. Alte Reparaturabschlüsse bleiben geschlossen.

### P-WEBHOOK-ORIGIN

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Chat vom 29.10. berichtet webhook.lana-ki.app ohne DNS-Ziel und ungeklärten n8n-Origin. Kein Neuaufbau oder DNS auf Verdacht; tatsächlichen Dienst/Port und Konto zuerst prüfen.

## Geplante Schritte

### PLAN-IDENTITY

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Bestehende Entra-App zuerst read-only inventarisieren: SignInAudience, RedirectUris, IdentifierUris, RequiredResourceAccess. Cross-Tenant Access/Sync, Rollen und Alias-/Loginmatrix abnehmen.

### PLAN-GOOGLE

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Vorhandenen Google-OAuth-Webclient prüfen/fertigstellen und Provider-Anbindung in Tenant B planen. Dienstkonto und Webclient strikt trennen; Secretwerte nur im vorgesehenen Store.

### PLAN-CALLBACK

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Vor Änderungen an Redirect-URIs den vorgesehenen /oauth/callback und die tatsächlich implementierte Gateway-Verarbeitung prüfen.

### PLAN-FILES

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Verstreute Projektdateien inventarisieren, Inhalts-/Hashvergleich und Verbraucher prüfen, anschließend kontrolliert in vorhandene zehn Bereiche einsortieren. Bisher keine pauschale Verschiebung erfolgt.

### PLAN-SOURCES

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Historische Originale sind indexiert, aber nicht jede Aussage strukturiert übernommen. Bei Themenbearbeitung relevante Quellen vollständig erschließen und Prüftiefe nachtragen.

### PLAN-PLATFORMS

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-30
- Jede weitere KI-Plattform braucht tatsächlichen Projektzugriff und geladenen Einstieg. Plattformtext bereitstellen; keine automatische Aktivierung aller Chats behaupten.

### PLAN-FLEET-DIRECT

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Drei unabhängige Serverzugänge und bestehende Cloud-Dienste inventarisieren/koppeln; Windows/Android als zusätzliche Clients. Ein offline gemeldeter Remote-Connector ist nicht gleichbedeutend mit fehlendem SSH-Zugang. Keine neuen Konten allein wegen fehlendem Connector.

### PLAN-WIF

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Berichteten GitHub-OIDC-Stand und tatsächliche Claude-Föderationsregel getrennt prüfen; Draft-PR ist kein produktiver End-to-End-Nachweis. Webhook/n8n bleibt getrennte Aufgabe.

## Ungeloeste Konflikte

### C-MODELS

- Nachweis: `CONFLICT` | Stand: 2026-10-30
- Cloud-only/Server-first lässt sich vereinbaren; Produktionsregel EXTERNAL_AI_SERVICE=NONE und externe Modellnutzung müssen getrennt nach Test/Produktion geklärt werden.

### C-GCP-PRIMARY

- Nachweis: `CONFLICT` | Stand: 2026-10-30
- Neu eingefügter Skill-Erfolgstext nennt <GCP_PRIMARY_PROJECT_ID> / <GCP_PRIMARY_PROJECT_NUMBER> als primäres Projekt. Bisheriger Kontext nennt <GCP_PROJECT_ID>. Rollen/Zweck und Primärentscheidung nicht still zusammenführen.

### C-CF-ACCOUNTS

- Nachweis: `CONFLICT` | Stand: 2026-10-30
- Ähnlich benannte Google-Identitäten und unterschiedlich erreichbare Cloudflare-Konten getrennt halten. Policy-Löschung nicht mit App-Löschung gleichsetzen; konkrete Ressourcenbelege fehlen teilweise.

### C-STORES

- Nachweis: `CONFLICT` | Stand: 2026-10-30
- Autoritativen Store je Datenklasse/Secret und Verbraucher festlegen. Alte lokale Notizbuch-/ENV-/Cloud-/Backup-Regeln sind nicht als abgeschlossene Migration belegt.

### C-GEMINI-SPLIT

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Eingefügter Gemini-Umbau stammt vom früheren Rohbestand: würde aktuelle Globale-Ablage entfernen, Master/Skill überschreiben und Revision/Sperre umgehen. Erster extrahierter PowerShell-Block syntaktisch unvollständig. Nicht auf die bestehende Installation anwenden; cloudseitiger Gemini-Stand nicht unabhängig verifiziert.

## Quellenlage

### SRC-REGISTER

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Vollständige bekannte Quellenpfade, Dateihashes, ältere Chatverweise und archivierte Masterfassungen stehen in docs/Lana-Quellenregister.json. Quellen sind kein automatischer Aktivierungsnachweis.

### SRC-CHAT

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Nutzerauftrag 30.10.: gemeinsamen Skill bauen, Dokumente synchron pflegen, aktive Probleme bereinigen, feste Ablage nutzen. Gelieferte Zusammenfassung ergänzt Microsoft/Google-Kontext; nicht frisch live abgefragt.

### SRC-CLAIM

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Extern eingefügter Text behauptet bereits aktiven lana-ki-master-sync. Bei lokaler Prüfung existierte davor kein solcher Skill in Projekt-/Codex-Skillpfaden. Diese lokale Einrichtung ist getrennt davon nachzuweisen.

### SRC-PAGES-ENV-20261030

- Nachweis: `DOCUMENTED` | Stand: 2026-10-30
- Sechs Pages und fünf verfügbare jüngere Chatrunden gelesen; 19 genannte Dateien erfasst, zwei eingefügte Texte bytegleich. Fünf Dokumententwürfe enthalten ältere/konfligierende Stände. Pages nur gelesen, lokale Masterpflege aktualisiert. Kein vollständiger Zugriff auf alle historischen Anhänge.

## Abgeschlossen

Diese Punkte sind erledigt und gelten nicht mehr als offen.
Belege liegen im privaten Auditprotokoll.

- `P-ENV-READONLY` (LIVE_VERIFIED)
- `P-NPM-WRANGLER` (LIVE_VERIFIED)

## Grenzen dieser Fassung

- Kein Betriebsnachweis. Ein Eintrag beschreibt den Kenntnisstand,
  nicht einen laufenden Dienst.
- Keine Secret-Werte, keine Zugangsdaten, keine Kennungen.
- Wer eine Kennung braucht, fragt den Betreiber; sie steht nicht hier.

