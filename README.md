# 🔐 CipherGen

<div align="center">

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-None-4ade80?style=for-the-badge)
![100% Local](https://img.shields.io/badge/Network-Zero%20requests-a78bfa?style=for-the-badge)

**Crypto-random password generator — 100% local, zéro réseau**

[🚀 Demo live](#) · [📁 Code source](https://github.com/Maxime288/CipherGen/blob/main/ciphergen.html) · [🐛 Signaler un bug](https://github.com/Maxime288/CipherGen/issues)

</div>

---

## ✨ Fonctionnalités

- **🎲 Crypto-aléatoire** — utilise `crypto.getRandomValues()`, jamais `Math.random()`
- **📊 Analyse d'entropie en temps réel** — calcul en bits + estimation du temps de crackage
- **🎨 Coloration syntaxique** — majuscules, chiffres et caractères spéciaux colorés distinctement
- **🔤 4 jeux de caractères configurables** — minuscules, majuscules, chiffres, spéciaux
- **⚙️ Options avancées** — exclusion des caractères ambigus (`0O`, `1Il`), mode prononçable
- **📏 Longueur ajustable** — de 4 à 128 caractères via slider
- **📋 Copie en un clic** — dans le presse-papier via l'API Clipboard
- **🔒 Zéro réseau** — aucune requête externe, fonctionne hors-ligne
- **📦 Zéro dépendance** — un seul fichier HTML, aucun npm, aucun framework

---

## 🖥️ Aperçu

```
┌─────────────────────────────────────────┐
│  🔒 100% local — zéro réseau            │
│                                         │
│  Générateur de mots de passe            │
│                                         │
│  [k#9Pq!mZ2@vL...........] [⎘] [↻]    │
│                                         │
│  Entropie ████████████░░░░  134 bits    │
│  Fort  ⏱ des siècles                   │
│                                         │
│  [aZ] ON  [AZ] ON  [09] ON  [!@] ON    │
│                                         │
│  Longueur ─────────●────── 20           │
│                                         │
│  [✓ Exclure ambigus] [  Prononçable ]  │
│                                         │
│  ⚡ Générer un mot de passe             │
│                                         │
│  Pool: 89  │  Longueur: 20  │  10^39   │
└─────────────────────────────────────────┘
```

---

## 🚀 Utilisation

Aucune installation requise. Télécharge et ouvre directement dans ton navigateur :

```bash
git clone https://github.com/Maxime288/CipherGen.git
cd CipherGen
# Ouvrir ciphergen.html dans ton navigateur
```

Ou utilise directement la [demo live](#).

---

## 🔬 Sécurité & Technique

### Génération aléatoire

```js
function randomInt(max) {
  const arr = new Uint32Array(1);
  const limit = 0x100000000 - (0x100000000 % max);
  let val;
  do { crypto.getRandomValues(arr); val = arr[0]; } while (val >= limit);
  return val % max;
}
```

Le rejet modulo élimine le biais statistique — chaque caractère a une probabilité strictement égale d'être sélectionné.

### Calcul d'entropie

```
Entropie (bits) = longueur × log₂(taille_pool)
```

| Entropie | Force | Estimation crackage |
|----------|-------|---------------------|
| < 28 bits | Très faible | < 1 seconde |
| 28–36 bits | Faible | Quelques minutes |
| 36–60 bits | Moyen | Quelques heures |
| 60–100 bits | Fort | Des siècles |
| > 100 bits | Extrême | Temps cosmologique ∞ |

### Garantie de complexité

Lorsque plusieurs jeux de caractères sont activés, le générateur s'assure qu'au moins **un caractère de chaque type** est présent, puis mélange le tout avec un **Fisher-Yates shuffle** crypto-aléatoire.

---

## 🎛️ Options

| Option | Description |
|--------|-------------|
| **Minuscules** | `a–z` (26 caractères) |
| **Majuscules** | `A–Z` (26 caractères) |
| **Chiffres** | `0–9` (10 caractères) |
| **Spéciaux** | `!@#$%^&*…` (32 caractères) |
| **Exclure ambigus** | Retire `0`, `O`, `1`, `I`, `l` |
| **Prononçable** | Alternance consonnes/voyelles |

---

## 📁 Structure

```
CipherGen/
└── index.html   # Application complète (HTML + CSS + JS)
```

Fichier unique, autonome, sans dépendances.

---

## 🤝 Contribution

Les contributions sont les bienvenues !

```bash
# Fork le repo
# Crée une branche
git checkout -b feature/ma-fonctionnalite

# Commit
git commit -m "feat: description"

# Push & Pull Request
git push origin feature/ma-fonctionnalite
```

---

## 📜 Licence

MIT © [Maxime288](https://github.com/Maxime288)

---

<div align="center">

Fait avec ❤️ par [Maxime288](https://github.com/Maxime288) · Voir aussi [Urus-Cracker-Pro](https://github.com/Maxime288/Urus-Cracker-Pro)

</div>
