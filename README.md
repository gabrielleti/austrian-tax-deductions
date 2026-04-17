# austrian-tax-deductions

Ein Claude-Skill für österreichische Steuerabsetzungen — funktioniert in **Claude Code**, **Cowork**, **claude.ai** und **Mobile**.

Das Skill kennt sich aus mit:

- **ArbeitnehmerInnenveranlagung** (L1, L1k) — Werbungskosten, Sonderausgaben, Pendlerpauschale, Homeoffice, Familienbonus Plus, außergewöhnliche Belastungen
- **Selbständige Einkünfte** (E1, E1a) — Betriebsausgaben, Pauschalierungen, Kleinunternehmerregelung
- **Vermietung & Verpachtung** (E1b) — AfA, Instandhaltung/-setzung/Herstellung
- **Kapitalerträge** (E1kv) — KESt, Krypto (§ 27b EStG), ausländische Depots
- **FinanzOnline-Walkthroughs** — Schritt-für-Schritt mit Menüpfaden und Feldnamen

Inhaltlich gestützt auf [bmf.gv.at](https://www.bmf.gv.at), [arbeiterkammer.at](https://www.arbeiterkammer.at) und [ris.bka.gv.at](https://www.ris.bka.gv.at). Bei konkreten Beträgen prüft das Skill die Quellen live.

> ⚠️ **Keine Steuerberatung.** Dieses Skill hilft beim Recherchieren und Vorbereiten deiner Steuererklärung, ersetzt aber keine*n Steuerberater*in.

---

## Installation

### 1. Claude Code (lokal)

```bash
/plugin install https://github.com/gabrielleti/austrian-tax-deductions
```

Danach prüfen:

```bash
/plugin list
```

### 2. claude.ai (Web & Mobile)

1. Gepackte `.skill`-Datei herunterladen (aus dem neuesten [GitHub-Release](https://github.com/gabrielleti/austrian-tax-deductions/releases) oder selbst bauen, siehe unten).
2. In claude.ai in den Einstellungen **Skills → Upload** auswählen und `austrian-tax-deductions.skill` hochladen.
3. Auf Mobile ist das Skill automatisch verfügbar, sobald es im Account eingespielt ist.

### 3. Cowork (Remote-Agenten)

Wenn Cowork Plugin-Installs unterstützt:

```bash
/plugin install https://github.com/gabrielleti/austrian-tax-deductions
```

Alternativ die gleiche `.skill`-Datei wie bei claude.ai in Cowork hochladen.

---

## `.skill`-Datei selbst bauen

Voraussetzung: Du hast das `anthropic-skills:skill-creator`-Plugin installiert (es liefert das Package-Script mit).

```bash
cd ~/projects/austrian-tax-deductions
python -m scripts.package_skill skills/austrian-tax-deductions
```

Das Ergebnis `austrian-tax-deductions.skill` ist eine einzelne Datei, die du überall hochladen kannst.

Alternativ manuell: Der Skill-Ordner (`skills/austrian-tax-deductions/`) wird einfach in ein ZIP gepackt und zu `.skill` umbenannt.

---

## Repo-Struktur

```
austrian-tax-deductions/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── austrian-tax-deductions/
│       ├── SKILL.md
│       ├── references/
│       │   ├── dienstnehmer.md
│       │   ├── selbstaendig.md
│       │   ├── vermietung-kapital.md
│       │   ├── aussergewoehnliche-belastungen.md
│       │   ├── betraege-2026.md
│       │   ├── finanzonline-guides.md
│       │   ├── formulare-uebersicht.md
│       │   ├── fristen-rechtsmittel.md
│       │   └── quellen.md
│       └── assets/
│           └── checkliste-belege.md
├── evals/
│   └── evals.json                # Test-Prompts für den Skill-Creator-Eval-Loop
├── README.md
├── LICENSE
└── .gitignore
```

## Mitarbeiten / Updates

- **Beträge aktualisieren:** `skills/austrian-tax-deductions/references/betraege-2026.md` — bei Änderungen auch den `Letzter Abgleich`-Timestamp aktualisieren.
- **Neue FinanzOnline-Guides:** `skills/austrian-tax-deductions/references/finanzonline-guides.md` ergänzen.
- **Nach Änderungen:** neuen `.skill`-Build machen und in claude.ai/Cowork aktualisieren.

## Lizenz

MIT — siehe [LICENSE](LICENSE). Steuerinformationen sind Zusammenfassungen öffentlicher Quellen und keine rechtsverbindliche Auskunft.
