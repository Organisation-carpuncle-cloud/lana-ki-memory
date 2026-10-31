# Lana KI - oeffentlicher Projektstand

Revision: 6 | Zustand vom: 2026-10-31T18:51:55.633566+00:00

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

### R-SECRETS-ENV-ONLY

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-31
- Passwoerter, Tokens und Zugangsdaten werden ausschliesslich im Ordner env des Projekts gespeichert. Einzige zugelassene Ausnahme ist die Speicherung im Geraet selbst, etwa der Kennwortspeicher der FRITZ!Box fuer deren eigene Dienste. Nirgendwo sonst: nicht in docs, nicht in scripts, nicht in Notizen, nicht in Chats, nicht in Screenshots von Anmeldedialogen. Ein in einem Screenshot sichtbares Kennwort gilt als offengelegt und loest Rotation aus.

### R-NO-VENV

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-31
- Virtuelle Python-Umgebungen sind im Projekt verboten. Kein .venv, kein venv, keine __pycache__-Ordner. Abhaengigkeiten werden ueber requirements.txt beschrieben und bei Bedarf ausserhalb des Projekts installiert. Gleiches Prinzip gilt fuer eingecheckte Fremdbestaende: sie gehoeren nicht in skills.

### R-NAMING

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-31
- Verbindliche Namensgebung. Benutzerkonto auf jedem Server und Geraet ist carpu; das ist der Betreiber selbst. Geraetenamen sind ausschliesslich carpuncle-pc, carpuncle-vps, carpuncle-cloud, carpuncle-server und carpuncle-pixel. Keine abweichenden Schreibweisen erfinden und keine neuen Geraetenamen einfuehren. Bei Abweichung in einer Quelle gilt diese Liste.

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

### F-SHADOWDRIVE

- Nachweis: `USER_SPECIFIED` | Stand: 2026-10-31
- ShadowDrive ist als WebDAV-Online-Speicher direkt an der FRITZ!Box des Heimnetzes angebunden, mit aktivem Abgleich zwischen lokalem Speicher und Online-Speicher. Der Zugang laeuft damit nicht ueber das MCP-Gateway. Die Netzwerkfreigabe Online-Speicher ist dieser Weg; dort abgelegte Sicherungen gelangen ueber den Abgleich zu ShadowDrive. Zugangsdaten liegen im Kennwortspeicher der FRITZ!Box, nicht im Projekt.

### F-AGENT365-PLATTFORMEN

- Nachweis: `DOCUMENTED` | Stand: 2026-10-31
- Microsoft Agent 365 Connected Platforms unterstuetzt genau sieben Quellplattformen: Amazon Bedrock, Google Vertex AI, Salesforce Agentforce, Databricks Genie, Anthropic Claude Managed Agents, Oracle Generative AI Agents und Snowflake Cortex. Fuer Oracle und Snowflake ist Observability angekuendigt, aber noch nicht verfuegbar. Nicht unterstuetzt sind OpenAI/ChatGPT, xAI/Grok, Cloudflare Workers AI, Hugging Face, Notion und Perplexity. Verbindungen sind read-only und synchronisieren nur manuell.

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

### P-FREMDBESTAND-SKILLS

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-31
- Der Ordner skills ist von 15 auf 42 Unterordner gewachsen. Mehrere davon sind Arbeitsverzeichnisse statt Skills, mehrere tragen Namen mit Leerzeichen oder Sonderzeichen und werden dadurch von keinem Agenten geladen, und fuenf Namen der Form lana-ki-agent, lana-ki-agent-komplett, lana-ki-agent-npm, lana-ki-hub und lana-ki-main sind mutmassliche Dubletten. Inventar mit Hashvergleich steht aus; keine pauschale Verschiebung.

### P-NODE-MODULES-STAMM

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-31
- Im Projektstamm liegt node_modules mit 8.289 Dateien und rund 340 MB, dazu package.json mit den Abhaengigkeiten des Agent-Client-Protocol-SDK. Das ist ein elfter Hauptordner und verletzt die Zehn-Ordner-Regel. Reproduzierbar aus package-lock.json. Entscheidung offen, wohin die ACP-Arbeit gehoert; nicht eigenmaechtig verschoben, weil ein laufender Bezug moeglich ist.

### P-KONTEN-REGISTER

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-31
- Das Konten-Register weicht vom tatsaechlichen ENV-Bestand ab. ovhcloud.env gilt dort als fehlend, vorhanden ist ovh.env mit vier Schluesseln. Die vorhandenen microsoft.env mit 17 und azure.env mit sieben Schluesseln fehlen im Register. Der Eintrag Google.env ist gross geschrieben, die Datei heisst google.env; auf den Linux-Knoten waeren das zwei verschiedene Dateien. Tatsaechlich fehlen m365-carpu1986.env, m365-root.env und google-admin.env.

### P-AGENT365-VORAUSSETZUNG

- Nachweis: `DOCUMENTED` | Stand: 2026-10-31
- Agent-Telemetrie in Agent 365 setzt Microsoft 365 E7 oder G7 beziehungsweise eine Agent-365-Lizenz voraus; mit den uebrigen Enterprise-Plaenen gibt es nur Inventar und Basisgovernance ohne Activity-Daten. Die Observability-Datensammlung laeuft zusaetzlich ueber das Frontier-Preview-Programm. Jede Verbindung verlangt einen schluesselbasierten Zugang, der in Microsoft 365 hinterlegt wird; Workload Identity Federation wird nicht unterstuetzt. Der Telemetrieabruf kann beim Quellanbieter Abfragekosten ausloesen, etwa BigQuery oder S3. Eigener Lizenzstand nicht geprueft.

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

### C-TENANT-DRITTER

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-31
- Der Microsoft-365-Connector dieser Claude-Sitzung meldet als angemeldetes Konto einen onmicrosoft-Tenant, der weder als Haupttenant B noch als Zweittenant A im Projektzustand gefuehrt wird und auch nicht die ausdruecklich ausgeschlossene Domain ist. Damit existiert mindestens ein weiterer Tenant oder ein weiteres Konto im Umlauf. Vor jeder Admin-Center-Arbeit klaeren, in welchem Tenant gearbeitet wird; Einstellungen aus unterschiedlichen Tenants nicht vermischen. Keine neue Kontoanlage daraus ableiten.

### C-SECRETS-AGENT365

- Nachweis: `LIVE_VERIFIED` | Stand: 2026-10-31
- Die Regel R-SECRETS-ENV-ONLY erlaubt Zugangsdaten nur im Ordner env und im Kennwortspeicher eines Geraets fuer dessen eigene Dienste. Eine Agent-365-Plattformverbindung verlangt dagegen, einen Anbieterschluessel in Microsoft 365 zu hinterlegen. Das ist weder env noch ein Geraetespeicher. Vor dem Anlegen einer Verbindung entscheiden, ob Microsoft 365 als zusaetzlicher zugelassener Speicherort gelten soll, und die Regel dann entsprechend ergaenzen statt sie stillschweigend zu brechen.

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

