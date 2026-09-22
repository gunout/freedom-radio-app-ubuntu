# FREEDOM 🎙️

> Lecteur radio desktop pour **Free Dom** — La Réunion  
> Interface sombre frameless, visualiseur audio animé, popups intégrés vers le site officiel.

---

## 📸 Aperçu

```
┌─────────────────────────────────────────────┐
│  [LOGO FREE DOM]   SITE      ─   ✕   ⌃      │
│  by gleaphe                                 │
│                                             │
│         ▁▃▅█▇▅▃▁▃▅█▇▅▃▁▃▅█▇▅▃▁              │
│              FREEDOM 1                      │
│              EN DIRECT                      │
│                                             │
│  ▶  ■   EN DIRECT        🔊 ────●─  ⌄       │
│                                             │
│  STATIONS                                   │
│  ┌─────────────────────────────────────┐    │
│  │ FREEDOM 1                           │    │
│  │ FREEDOM 2                           │    │
│  └─────────────────────────────────────┘    │
│  PRÊT                                       │
└─────────────────────────────────────────────┘
```

<img width="450" height="70" alt="freedom" src="https://github.com/user-attachments/assets/f62e549d-1516-411d-886f-57ea8ad4ffcd" />

<img width="450" height="340" alt="freedom 2" src="https://github.com/user-attachments/assets/c17b53f4-5f27-4c3b-bfe4-80adae984708" />

<img width="340" height="420" alt="freedom 3" src="https://github.com/user-attachments/assets/8ef2c0bc-a4d4-4d52-b8e3-b8c07c60e457" />

---

## ✨ Fonctionnalités

- 🎵 **Lecture des 2 flux Free Dom** en direct (Icecast / Streamakaci)
- 📊 **Visualiseur audio animé** qui réagit à l'état de lecture
- 🪟 **Interface frameless** avec coins arrondis, drag & resize à la souris
- 🎨 **Palette sombre** avec accent cyan, animations fluides
- 📻 **Basculement instantané** entre Free Dom 1 et Free Dom 2
- 🔇 **Contrôles complets** : play / pause / stop / mute / volume
- 🌐 **Popup intégré** vers les sections du site officiel `freedom.fr`
- 📐 **Repli de fenêtre** (mode mini) et **repli des contrôles**
- 🖼️ **Logo Free Dom** affiché dans le HUD

---

## 🖥️ Compatibilité

| Système | Statut |
|---------|--------|
| Linux (Debian / Ubuntu / Mint) | ✅ Testé |
| Linux (Fedora / Arch) | ✅ Compatible |
| macOS | ⚠️ Non testé (mpv requis) |
| Windows | ⚠️ Non testé (mpv requis) |

---

## 📦 Prérequis

### Système

Le lecteur repose sur **libmpv** (moteur audio/vidéo natif).

**Debian / Ubuntu / Linux Mint**
```bash
sudo apt update
sudo apt install -y libmpv2 mpv
```

**Fedora**
```bash
sudo dnf install mpv mpv-libs
```

**Arch / Manjaro**
```bash
sudo pacman -S mpv
```

**openSUSE**
```bash
sudo zypper install mpv libmpv1
```

### Python

- Python **3.10+**
- `pip` à jour

---

## 🚀 Installation

```bash
# 1. Cloner ou copier le dossier du projet
cd ~/Desktop/Freedom

# 2. (Optionnel) Créer un environnement virtuel
python3 -m venv venv
source venv/bin/activate

# 3. Installer les dépendances Python
pip install -r requirements.txt
```

### 📄 `requirements.txt`

```txt
PyQt6>=6.6.0
python-mpv>=1.0.5
```

---

## ▶️ Utilisation

```bash
python3 freedom.py
```

### Commandes rapides

| Action | Comment |
|--------|---------|
| **Lancer une station** | Double-clic sur **FREEDOM 1** ou **FREEDOM 2** |
| **Pause / Reprendre** | Bouton ▶ / ⏸ |
| **Arrêter** | Bouton ■ |
| **Volume** | Curseur horizontal ou bouton 🔊 |
| **Muet** | Bouton 🔊 (bascule en 🔇) |
| **Ouvrir le site** | Bouton **SITE** dans le HUD |
| **Replier les contrôles** | Bouton ⌄ à droite des contrôles |
| **Replier la fenêtre** | Bouton ⌃ dans le HUD (mode mini) |
| **Déplacer la fenêtre** | Clic-glisser n'importe où |
| **Redimensionner** | Glisser les bords / coins |
| **Fermer** | Bouton ✕ |

---

## 📁 Structure du projet

```
Freedom/
├── freedom.py          # Application principale
├── logo.png            # Logo Free Dom (optionnel — fallback texte)
├── requirements.txt    # Dépendances Python
└── README.md           # Ce fichier
```

---

## 🔧 Personnalisation

### Ajouter / modifier une station

Dans `freedom.py`, en haut du fichier :

```python
STATIONS = [
    ("FREEDOM 1", "https://freedomice.streamakaci.com/freedom.mp3"),
    ("FREEDOM 2", "https://freedomice.streamakaci.com/freedom2.mp3"),
    # Ajoute ici d'autres flux
]
```

### Modifier les liens du site officiel

```python
SITE_LINKS = {
    "site":     ("Site Freedom.fr",  "https://freedom.fr/"),
    "actu":     ("Actualité",        "https://freedom.fr/"),
    "radio1":   ("Radio Free Dom 1", "https://freedom.fr/free-dom-1/"),
    "radio2":   ("Radio Free Dom 2", "https://freedom.fr/free-dom-2/"),
    # ...
}
```

### Changer le logo

Remplace `logo.png` à la racine du projet.  
Si le fichier est absent, un **fallback texte** "FREE DOM" s'affiche automatiquement.

### Changer les couleurs

En haut de `freedom.py` :

```python
BG          = "rgba(12, 12, 14, 240)"   # Fond principal
ACCENT      = "#00e5ff"                 # Cyan
TEXT        = "#f5f5f7"                 # Texte clair
```

---

## 🐛 Dépannage

### `cannot load library 'libmpv.so.1'`

→ `libmpv` n'est pas installé. Voir la section **Prérequis système**.

### Pas de son au changement de station

→ Le correctif est déjà intégré (`stop` + reset + délai 200 ms).  
→ Teste les flux isolément :
```bash
mpv https://freedomice.streamakaci.com/freedom.mp3
mpv https://freedomice.streamakaci.com/freedom2.mp3
```

### Warnings D-Bus au démarrage

```
qt.qpa.theme.gnome: dbus reply error: ... portal.Settings
```

→ **Inoffensif.** Pour les supprimer :
```bash
sudo apt install xdg-desktop-portal xdg-desktop-portal-gtk
```

### Le logo ne s'affiche pas

→ Vérifie que `logo.png` existe à la racine :
```bash
file ~/Desktop/Freedom/logo.png
# Doit renvoyer : PNG image data, ...
```

---

## 🎨 Design

| Élément | Valeur |
|---------|--------|
| Fond | `rgba(12, 12, 14, 240)` |
| Accent | `#00e5ff` (cyan) |
| Texte principal | `#f5f5f7` |
| Texte secondaire | `rgba(245, 245, 247, 100)` |
| Rayon des coins | `14px` (fenêtre), `12px` (carte) |
| Police | Inter 9pt |

---

## 📡 Flux radio

| Station | URL |
|---------|-----|
| Free Dom 1 | `https://freedomice.streamakaci.com/freedom.mp3` |
| Free Dom 2 | `https://freedomice.streamakaci.com/freedom2.mp3` |

---

## 🌐 Site officiel

- **Accueil** : <https://freedom.fr/>
- **Free Dom 1** : <https://freedom.fr/free-dom-1/>
- **Free Dom 2** : <https://freedom.fr/free-dom-2/>
- **Freedom Club** : <https://freedom.fr/category/freedom-club/>

---

## 📜 Licence

Projet personnel — usage privé.  
Les flux radio et le logo **Free Dom** appartiennent à leurs propriétaires respectifs.

---

## 👤 Auteur

**gleaphe**  
Projet desktop pour l'écoute des radios Free Dom à La Réunion.

---

## 🙏 Remerciements

- [mpv](https://mpv.io/) — moteur de lecture
- [PyQt6](https://www.riverbankcomputing.com/software/pyqt/) — framework UI
- [Streamakaci](https://www.streamakaci.com/) — hébergement des flux
- **Free Dom** — La Réunion
