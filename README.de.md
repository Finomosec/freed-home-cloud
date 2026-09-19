[English](README.md) · [Deutsch](README.de.md)

# Freed Home Cloud

> *„Das sind meine Daten, und ich behalte sie für mich!"*

Eine modulare, selbstgehostete Home-Cloud — frei von Google, Microsoft und den
übrigen Hyperscalern. Privacy first, verschlüsselt, mehrbenutzerfähig und darauf
ausgelegt, auf Hardware zu laufen, die bei dir zuhause steht.

> **Status: Konzept.** Hier liegt noch kein nutzbarer Code. Dieses Repository
> hält die Vision, die Architektur-Notizen und die offenen Fragen fest, während
> das Design ausgearbeitet wird. Der Name ist reserviert; die Entwicklung startet
> von hier aus.

## Warum

Jedes Jahr landet mehr vom privaten Leben auf Servern, die uns weder gehören
noch von uns kontrolliert werden: Dokumente, Fotos, Kalender, Passwörter,
Gespräche. Wer sich davon heute lösen will, muss ein Dutzend einzelner
Self-Hosting-Projekte zusammenstückeln — jedes mit eigenem Login, eigener
Update-Strategie und eigener Backup-Lücke. Das ist ein Vollzeit-Hobby, kein
Produkt.

Freed Home Cloud will genau diese Hürde beseitigen: ein zusammenhängendes
System, ein Login, eine Backup-Strategie, ein Ort, an dem alles auffindbar ist.

**Leitwerte:** Freiheit · Souveränität · die Kontrolle zurückholen ·
Eigenverantwortung · lokal · Unabhängigkeit.

## Was daraus werden soll

Eine modulare Plattform, deren Komponenten sich je nach Bedarf zuschalten
lassen:

- **Portalseite** — ein Dashboard, das jeden Dienst auffindbar macht
- **Single Sign-On** — lokal gehostet, ein Login für alle Komponenten
- **Multi-User** — gebaut für Familien und kleine Gruppen, nicht nur für einen Admin
- **Verschlüsselter Speicher** — Daten liegen verschlüsselt auf lokalen Platten
- **Mehrstufige Backups** — Snapshots, lokale Spiegelung, Redundanz an anderem Ort

## Geplante Module

Die Dienste, für die sich der Betrieb überhaupt lohnt — pro Haushalt zuschaltbar:

- **Dateien, Kalender und Kontakte** — der Kern des digitalen Alltags, synchron auf allen Geräten
- **Musik-Streaming** — die eigene Sammlung, zuhause und unterwegs
- **Passwort-Manager** — Zugangsdaten bleiben auf der eigenen Hardware
- **Geräte-Sync** — laufender Dateiabgleich zwischen PCs, Handys und Tablets
- **PDF-Werkzeugkasten** — zusammenführen, teilen, signieren und wandeln, ohne Upload zu Fremden
- **Werbeblocker** — netzweit auf DNS-Ebene, für jedes Gerät im Haus
- **Metriken und Monitoring** — sehen, was das System tut und wann es Aufmerksamkeit braucht
- **E-Mail** — das eigene Postfach, auf Wunsch unter eigener Domain
- **Lokale KI-Assistenz** — ein Modell auf der eigenen Hardware, für Support und Automatisierung

Wo es bereits ein gutes Open-Source-Projekt gibt, wird es integriert statt neu
erfunden.

## Der schwierige Teil: verteiltes Backup

Das meiste davon ist Integrationsarbeit. Ein Baustein ist jedoch tatsächlich
ungelöst und bildet den Forschungskern des Projekts:

**Die eigenen, verschlüsselten Daten redundant auf den Rechnern anderer Nutzer
ablegen — und sie zuverlässig verfügbar halten, obwohl das ganz normale Heim-PCs
sind, die offline gehen, wann immer ihre Besitzer es wollen.**

Die Skizze: Daten werden in verschlüsselte, anonymisierte Chunks zerlegt und
softwaregesteuert verteilt; Erasure Coding hält den Speicher-Overhead im Rahmen;
und jeder Client misst, wie gut ein Chunk noch repliziert ist, und seedet ihn
nach, sobald die Redundanz unter einen Schwellwert fällt — das System heilt sich
also selbst, ohne zentralen Koordinator.

Die offenen Fragen sind genau die interessanten: Wie misst ein Client zuverlässig
die netzweite Verfügbarkeit eines Chunks zwischen flüchtigen Nodes? Wie vermeidet
man Über- und Unterreplikation sowie Thundering-Herd-Effekte? Wie weist man nach,
dass ein fremder Node wirklich noch hält, was er behauptet? Und wie erzwingt man
Fairness?

### Stand der Technik

Neuland ist das nicht, und etwas anderes zu behaupten wäre unredlich.
[Tahoe-LAFS](https://tahoe-lafs.org/), [Storj](https://www.storj.io/) und
[Sia](https://sia.tech/) verteilen alle verschlüsselte, erasure-codierte Daten —
stützen sich dabei aber auf dauerhaft erreichbare Profi- oder Bezahl-Nodes und
zentrale Repair-Services. Die Projekte, die es mit unzuverlässiger
Consumer-Hardware versucht haben — Symform, CrashPlans Friend-to-Friend-Backup,
BuddyBackup — wurden allesamt eingestellt. Genau diese Lücke ist die Arbeit wert.

## Roadmap (grob)

1. **Fundament** — Portal, SSO, Multi-User, verschlüsselter Speicher, ein erster
   Satz integrierter Dienste, vernünftige Update- und Monitoring-Strategie
2. **Backup** — mehrstufige lokale Backups, danach die verteilte Redundanzschicht
3. **Assistenz** — lokale KI für Support und Selbstreparatur des Systems

## Zum Namen

„Freed" im Sinne von *befreit* — es geht darum, die eigenen Daten aus den großen
Clouds herauszuholen. Dieses Projekt steht in **keiner Verbindung zu**
[FreedomBox](https://freedombox.org/), Freenet oder ähnlich benannten Projekten.

## Mitmachen

Für Code-Beiträge ist es zu früh. Ideen, Kritik und Hinweise auf vergleichbare
Ansätze sind sehr willkommen — am besten als Issue.

## Lizenz

[GNU AGPL-3.0](LICENSE) — wer eine modifizierte Version als Dienst betreibt, muss
dessen Nutzern den Quellcode zugänglich machen. Für Software, deren ganzer Zweck
darin besteht, Menschen die Kontrolle über ihre eigenen Systeme zu geben, ist das
der passende Standard.
