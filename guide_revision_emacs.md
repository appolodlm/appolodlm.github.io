# Guide de Révision - Système 1 & Emacs

> Guide complet pour la Licence Informatique  
> Université de Nice Côte d'Azur - Semestre 2

---

## Table des Matières

1. [Code ASCII et Encodage](#code-ascii-et-encodage)
2. [Commandes Unix Essentielles](#commandes-unix-essentielles)
3. [Terminal Xterm](#terminal-xterm)
4. [Clients X Windows](#clients-x-windows)
5. [GNU Emacs - Guide Complet](#gnu-emacs-guide-complet)
6. [Dired - Gestionnaire de Fichiers](#dired-gestionnaire-de-fichiers)
7. [Raccourcis Essentiels](#raccourcis-essentiels)

---

## Code ASCII et Encodage

### Présentation
Le code ASCII (American Standard Code for Information Interchange) représente les 128 premiers caractères du code ISO-8859.

**Variantes importantes :**
- **ISO-8859-1** : Europe occidentale (langues latines)
- **ISO-8859-9** : Version récente avec €, ×, ÷

### Caractères de Contrôle (0-31)

| Code | Nom | Description | Code | Nom | Description |
|------|-----|-------------|------|-----|-------------|
| 000 | NUL | Null | 016 | DLE | Data Link Escape |
| 001 | SOH | Start of Heading | 017 | DC1 | Device Control 1 |
| 002 | STX | Start of Text | 018 | DC2 | Device Control 2 |
| 003 | ETX | End of Text | 019 | DC3 | Device Control 3 |
| 004 | EOT | End of Transmission | 020 | DC4 | Device Control 4 |
| 005 | ENQ | Enquiry | 021 | NAK | Negative Acknowledge |
| 006 | ACK | Acknowledge | 022 | SYC | Synchronous Idle |
| 007 | BEL | Bell (alerte sonore) | 023 | ETB | End of Trans. Block |
| 008 | BS | Backspace | 024 | CAN | Cancel |
| 009 | HT | Horizontal Tab | 025 | EM | End of Medium |
| 010 | LF | Line Feed | 026 | SUB | Substitute |
| 011 | VT | Vertical Tab | 027 | ESC | Escape |
| 012 | FF | Form Feed | 028 | FS | File Separator |
| 013 | CR | Carriage Return | 029 | GS | Group Separator |
| 014 | SO | Shift Out | 030 | RS | Record Separator |
| 015 | SI | Shift In | 031 | US | Unit Separator |

### Caractères Imprimables (32-126)

| Plage | Type | Exemples |
|-------|------|----------|
| 032-047 | Symboles | Espace ! " # $ % & ' ( ) * + , - . / |
| 048-057 | Chiffres | 0 1 2 3 4 5 6 7 8 9 |
| 058-064 | Symboles | : ; < = > ? @ |
| 065-090 | Majuscules | A B C ... X Y Z |
| 091-096 | Symboles | [ \\ ] ^ _ \` |
| 097-122 | Minuscules | a b c ... x y z |
| 123-126 | Symboles | { \| } ~ |
| 127 | DEL | Delete |

### Touche Ctrl et ASCII

**Principe :** La touche `Ctrl` retranche **64** à la valeur normale de la touche.

| Combinaison | Code | Caractère |
|-------------|------|-----------|
| Ctrl-@ | 0 | NUL |
| Ctrl-G | 7 | BEL |
| Ctrl-[ | 27 | ESC |
| Ctrl-\\ | 28 | FS |

---

## Commandes Unix Essentielles

### `date` - Afficher Date et Heure

```bash
date
# Exemple de sortie :
# lundi 1 février 2010, 11:48:26 (UTC+0100)
```

**UTC** : Temps Universel Coordonné

### `cal` - Calendrier

```bash
# Calendrier du mois courant
cal

# Calendrier d'un mois spécifique
cal 4 1972        # Avril 1972
cal 12 2025       # Décembre 2025
```

### `w` - Utilisateurs Connectés

```bash
w
# Affiche : qui, depuis où, depuis quand, et ce qu'ils font
```

**Colonnes :**
- **User** : nom d'utilisateur
- **tty** : terminal
- **from** : provenance de la connexion
- **login@** : heure de connexion
- **idle** : temps d'inactivité
- **JCPU/PCPU** : temps processeur
- **what** : commande en cours

### `ps` - Processus

```bash
ps x              # Liste vos processus
ps aux            # Tous les processus du système
```

**Colonnes importantes :**
- **PID** : ID du processus
- **TTY** : terminal associé
- **STAT** : état (S=sleep, R=running)
- **TIME** : temps CPU
- **CMD** : commande

---

## Terminal Xterm

### Menus Contextuels

| Combinaison | Fonction |
|-------------|----------|
| Ctrl + Clic gauche | Envoi de signaux au processus |
| Ctrl + Clic milieu | Modes (vidéo inverse, scrollbar, repliage) |
| Ctrl + Clic droit | Taille des caractères |

### Défilement

**Méthodes :**
- **Shift-PgUp / Shift-PgDown** : navigation clavier
- **Molette souris** : scroll standard
- **Barre de défilement** :
  - Clic gauche : avancer
  - Clic droit : reculer
  - Clic milieu : centrer

### Sélection et Copier-Coller

| Action | Méthode |
|--------|---------|
| **Début sélection** | Clic gauche |
| **Fin sélection** | Clic droit (ajustable) |
| **Sélection rapide** | Cliquer-glisser (bouton gauche) |
| **Sélectionner mot** | Double-clic |
| **Sélectionner ligne** | Triple-clic |
| **Coller** | Clic milieu |
| **Désélectionner** | Clic simple ailleurs |

---

## Clients X Windows

### `oclock` - Horloge

```bash
oclock -bg blue -fg white -hour red -minute yellow
oclock -transparent
oclock -geometry 200x200
```

**Options :**
- `-bg` : couleur fond
- `-fg` : couleur aiguilles
- `-minute` : couleur aiguille minutes
- `-hour` : couleur aiguille heures
- `-bd` : couleur bordure
- `-transparent` : horloge transparente
- `-geometry` : dimensions (largeurxhauteur)

### `xload` - Charge Système

```bash
xload -update 5 -jumpscroll 10 hostname
```

**Options :**
- `-update` : intervalle mise à jour (secondes)
- `-jumpscroll` : décalage en pixels
- Paramètre final : nom de la machine

### `info` - Documentation GNU

**Navigation :**

| Touche | Action |
|--------|--------|
| **Espace** | Défiler / page suivante |
| **Backspace** | Reculer / page précédente |
| **Tab** | Prochain lien |
| **Entrée** | Suivre le lien |
| **q** | Quitter |

---

## GNU Emacs - Guide Complet

### Notation des Raccourcis

| Notation | Signification |
|----------|---------------|
| `C-x` | Ctrl + x |
| `M-x` | Alt + x (ou Meta) |
| `S-x` | Shift + x |
| `C-M-x` | Ctrl + Alt + x |

### Structure d'un Cadre Emacs

1. **Barre de menus** : File, Edit, Options, Buffers, Tools, Help
2. **Barre d'outils** : icônes actions fréquentes
3. **Fenêtre(s)** : affichage tampon(s)
4. **Ligne de mode** : informations sur le tampon
5. **Zone d'écho / mini-tampon** : messages et saisie commandes

### Menus Contextuels

| Combinaison | Menu |
|-------------|------|
| Ctrl + Clic gauche | Liste des tampons |
| Ctrl + Clic milieu | Text Properties |
| Ctrl + Clic droit | Menu contextuel du mode |

### Types de Commandes

1. **Commande abrégée** : `C-d`, `C-x C-c`, `M-f`
2. **Commande textuelle** : `M-x nom-commande RET`
3. **Commande par menu** : menus déroulants
4. **Touche spécialisée** : F1, PgUp, etc.

### Arguments

- **Numérique** : `M-5 C-n` (répète 5 fois)
- **Universel** : `C-u` (modifie comportement)
  - Exemple : `M-q` réajuste, `C-u M-q` justifie

---

### 1. Quitter Emacs

| Raccourci | Action |
|-----------|--------|
| `C-z` | Iconifier / suspendre Emacs |
| `C-x C-c` | Quitter définitivement |

### 2. Fichiers

| Raccourci | Action |
|-----------|--------|
| `C-x C-f` | Ouvrir fichier |
| `C-x C-s` | Enregistrer fichier |
| `C-x s` | Enregistrer tous les fichiers |
| `C-x i` | Insérer contenu d'un fichier |
| `C-x C-v` | Remplacer par un autre fichier |
| `C-x C-w` | Enregistrer sous |
| `C-x C-q` | Basculer lecture seule |

### 3. Aide

| Raccourci | Action |
|-----------|--------|
| `C-h` ou `F1` | Système d'aide |
| `C-h t` | Tutoriel interactif |
| `C-h a` | Apropos (recherche commande) |
| `C-h k` | Décrire touche |
| `C-h f` | Décrire fonction |
| `C-h m` | Info mode actuel |
| `C-x 1` | Fermer fenêtre d'aide |
| `C-M-v` | Défiler fenêtre d'aide |

### 4. Récupération d'Erreurs

| Raccourci | Action |
|-----------|--------|
| `C-g` | Annuler commande |
| `M-x recover-session` | Récupérer après crash |
| `C-x u`, `C-_`, `C-/` | Annuler (undo) |
| `M-x revert-buffer` | Restaurer fichier |
| `C-l` | Redessiner écran |

### 5. Recherche Incrémentale

| Raccourci | Action |
|-----------|--------|
| `C-s` | Recherche avant |
| `C-r` | Recherche arrière |
| `C-M-s` | Recherche regexp avant |
| `C-M-r` | Recherche regexp arrière |
| `M-p` | Recherche précédente (historique) |
| `M-n` | Recherche suivante (historique) |
| `RET` | Sortir de la recherche |
| `DEL` | Annuler dernier caractère |
| `C-g` | Abandonner recherche |

**Astuce :** `C-s` ou `C-r` répété continue la recherche.

### 6. Déplacement

| Entité | Arrière | Avant |
|--------|---------|-------|
| **Caractère** | `C-b` | `C-f` |
| **Mot** | `M-b` | `M-f` |
| **Ligne** | `C-p` | `C-n` |
| **Phrase** | `M-a` | `M-e` |
| **Paragraphe** | `M-{` | `M-}` |
| **Page** | `C-x [` | `C-x ]` |
| **Sexp** | `C-M-b` | `C-M-f` |
| **Fonction** | `C-M-a` | `C-M-e` |

**Autres déplacements :**

| Raccourci | Action |
|-----------|--------|
| `C-a` | Début de ligne |
| `C-e` | Fin de ligne |
| `M-<` | Début du buffer |
| `M->` | Fin du buffer |
| `C-v` | Page suivante |
| `M-v` | Page précédente |
| `C-x <` | Défiler gauche |
| `C-x >` | Défiler droite |
| `C-l` | Centrer / haut / bas |
| `M-g g` | Aller à la ligne |
| `M-g c` | Aller au caractère |
| `M-m` | Retour à l'indentation |

### 7. Suppression (Killing)

| Entité | Arrière | Avant |
|--------|---------|-------|
| **Caractère** (delete) | `DEL` | `C-d` |
| **Mot** | `M-DEL` | `M-d` |
| **Ligne** (jusqu'à fin) | `M-0 C-k` | `C-k` |
| **Phrase** | `C-x DEL` | `M-k` |
| **Sexp** | `M-- C-M-k` | `C-M-k` |

**Autres commandes :**

| Raccourci | Action |
|-----------|--------|
| `C-w` | Couper région |
| `M-w` | Copier région |
| `M-z char` | Tuer jusqu'au caractère |
| `C-y` | Coller (yank) |
| `M-y` | Coller précédent |

### 8. Marquage

| Raccourci | Action |
|-----------|--------|
| `C-@` ou `C-SPC` | Placer marque |
| `C-x C-x` | Échanger point et marque |
| `M-@` | Marquer mot |
| `M-h` | Marquer paragraphe |
| `C-x C-p` | Marquer page |
| `C-M-@` | Marquer sexp |
| `C-M-h` | Marquer fonction |
| `C-x h` | Marquer tout le buffer |

### 9. Rechercher-Remplacer

| Raccourci | Action |
|-----------|--------|
| `M-%` | Rechercher-remplacer interactif |
| `M-x query-replace-regexp` | Avec expressions régulières |

**Réponses pendant query-replace :**

| Touche | Action |
|--------|--------|
| `SPC` ou `y` | Remplacer et continuer |
| `,` | Remplacer sans bouger |
| `DEL` ou `n` | Passer sans remplacer |
| `!` | Tout remplacer |
| `^` | Retour en arrière |
| `RET` | Quitter |
| `C-r` | Édition récursive (`C-M-c` pour sortir) |

### 10. Fenêtres Multiples

| Raccourci | Fenêtre | Frame |
|-----------|---------|-------|
| **Fermer autres** | `C-x 1` | `C-x 5 1` |
| **Diviser haut/bas** | `C-x 2` | `C-x 5 2` |
| **Fermer celle-ci** | `C-x 0` | `C-x 5 0` |
| **Diviser gauche/droite** | `C-x 3` | - |
| **Défiler autre** | `C-M-v` | - |
| **Changer fenêtre** | `C-x o` | `C-x 5 o` |
| **Buffer dans autre** | `C-x 4 b` | `C-x 5 b` |
| **Afficher buffer** | `C-x 4 C-o` | `C-x 5 C-o` |
| **Fichier dans autre** | `C-x 4 f` | `C-x 5 f` |
| **Lecture seule** | `C-x 4 r` | `C-x 5 r` |
| **Dired dans autre** | `C-x 4 d` | `C-x 5 d` |
| **Tag dans autre** | `C-x 4 .` | `C-x 5 .` |

**Redimensionner :**

| Raccourci | Action |
|-----------|--------|
| `C-x ^` | Agrandir verticalement |
| `C-x {` | Rétrécir horizontalement |
| `C-x }` | Élargir horizontalement |

### 11. Formatage

| Raccourci | Action |
|-----------|--------|
| `TAB` | Indenter ligne |
| `C-M-\` | Indenter région |
| `C-M-q` | Indenter sexp |
| `C-x TAB` | Indenter région (rigide) |
| `M-;` | Indenter pour commentaire |
| `C-o` | Nouvelle ligne après point |
| `C-M-o` | Déplacer reste de ligne |
| `C-x C-o` | Supprimer lignes vides |
| `M-^` | Joindre lignes |
| `M-\` | Supprimer espaces |
| `M-SPC` | Un seul espace |
| `M-q` | Remplir paragraphe |
| `C-x f` | Définir colonne de remplissage |
| `C-x .` | Définir préfixe de ligne |

### 12. Casse

| Raccourci | Action |
|-----------|--------|
| `M-u` | Mot en MAJUSCULES |
| `M-l` | mot en minuscules |
| `M-c` | Mot en Capitale |
| `C-x C-u` | RÉGION EN MAJUSCULES |
| `C-x C-l` | région en minuscules |

### 13. Minibuffer

| Raccourci | Action |
|-----------|--------|
| `TAB` | Compléter maximum |
| `SPC` | Compléter un mot |
| `RET` | Compléter et exécuter |
| `?` | Montrer complétions |
| `M-p` | Saisie précédente |
| `M-n` | Saisie suivante / défaut |
| `M-r` | Recherche regexp arrière |
| `M-s` | Recherche regexp avant |
| `C-g` | Abandonner |

**Astuce :** `C-x ESC ESC` édite et répète dernière commande du minibuffer.  
**Astuce :** `F10` active la barre de menus en mode texte.

### 14. Tampons (Buffers)

| Raccourci | Action |
|-----------|--------|
| `C-x b` | Changer de buffer |
| `C-x C-b` | Liste des buffers |
| `C-x k` | Tuer un buffer |

### 15. Transposition

| Raccourci | Action |
|-----------|--------|
| `C-t` | Transposer caractères |
| `M-t` | Transposer mots |
| `C-x C-t` | Transposer lignes |
| `C-M-t` | Transposer sexps |

### 16. Vérification Orthographique

| Raccourci | Action |
|-----------|--------|
| `M-$` | Vérifier mot courant |
| `M-x ispell-region` | Vérifier région |
| `M-x ispell-buffer` | Vérifier tout le buffer |
| `M-x flyspell-mode` | Vérification à la volée |

### 17. Tags

| Raccourci | Action |
|-----------|--------|
| `M-.` | Trouver une définition |
| `M-x visit-tags-table` | Charger fichier tags |
| `M-x tags-search` | Recherche dans tous les fichiers |
| `M-x tags-query-replace` | Remplacer dans tous les fichiers |
| `M-,` | Continuer recherche/remplacement |

### 18. Shells

| Raccourci | Action |
|-----------|--------|
| `M-!` | Commande shell |
| `M-&` | Commande shell asynchrone |
| `M-\|` | Commande shell sur région |
| `C-u M-\|` | Filtrer région par commande |
| `M-x shell` | Shell interactif |

### 19. Rectangles

| Raccourci | Action |
|-----------|--------|
| `C-x r r` | Copier rectangle dans registre |
| `C-x r k` | Couper rectangle |
| `C-x r y` | Coller rectangle |
| `C-x r o` | Ouvrir rectangle (décaler droite) |
| `C-x r c` | Vider rectangle |
| `C-x r t` | Préfixer chaque ligne |

### 20. Abréviations

| Raccourci | Action |
|-----------|--------|
| `C-x a g` | Ajouter abréviation globale |
| `C-x a l` | Ajouter abréviation locale |
| `C-x a i g` | Ajouter expansion globale |
| `C-x a i l` | Ajouter expansion locale |
| `C-x a e` | Développer abréviation |
| `M-/` | Complétion dynamique |

### 21. Divers

| Raccourci | Action |
|-----------|--------|
| `C-u num` | Argument numérique |
| `M--` | Argument négatif |
| `C-q char` | Insertion littérale |

### 22. Expressions Régulières

**Opérateurs de base :**

| Symbole | Signification |
|---------|---------------|
| `.` | N'importe quel caractère (sauf newline) |
| `*` | 0 ou plus répétitions |
| `+` | 1 ou plus répétitions |
| `?` | 0 ou 1 répétition |
| `\` | Échappement caractères spéciaux |
| `\c` | Échapper caractère c |
| `\\|` | Alternative (OU) |
| `\( ... \)` | Groupement |
| `\(?: ... \)` | Groupement non-capturant |
| `\(?NUM: ... \)` | Groupement numéroté |
| `\n` | Référence au groupe n |
| `\b` | Frontière de mot |
| `\B` | Pas frontière de mot |

**Ancres :**

| Entité | Début | Fin |
|--------|-------|-----|
| **Ligne** | `^` | `$` |
| **Mot** | `\<` | `\>` |
| **Symbole** | `\_<` | `\_>` |
| **Buffer** | `\'` | `\'` |

**Classes de caractères :**

| Classe | Correspond | Ne correspond pas |
|--------|------------|-------------------|
| **Ensemble explicite** | `[...]` | `[^...]` |
| **Syntaxe mot** | `\w` | `\W` |
| **Syntaxe c** | `\sc` | `\Sc` |
| **Catégorie c** | `\cc` | `\Cc` |

### 23. Jeux de Caractères Internationaux

| Raccourci | Action |
|-----------|--------|
| `C-x RET l` | Définir langue principale |
| `M-x list-input-methods` | Lister méthodes de saisie |
| `C-\` | Activer/désactiver méthode saisie |
| `C-x RET c` | Définir encodage pour commande |
| `M-x list-coding-systems` | Lister encodages |
| `M-x prefer-coding-system` | Choisir encodage préféré |

### 24. Info (Documentation)

| Raccourci | Action |
|-----------|--------|
| `C-h i` | Ouvrir Info |
| `C-h S` | Chercher fonction/variable dans Info |

**Navigation dans Info :**

| Touche | Action |
|--------|--------|
| `SPC` | Défiler / nœud suivant |
| `DEL` | Reculer / nœud précédent |
| `b` | Début du nœud |
| `n` | Nœud suivant |
| `p` | Nœud précédent |
| `u` | Monter |
| `m` | Sélectionner menu par nom |
| `1-9` | Sélectionner item n du menu |
| `f` | Suivre référence |
| `l` | Retour au dernier nœud |
| `d` | Répertoire |
| `t` | Sommet du fichier |
| `g` | Aller à nœud par nom |
| `h` | Tutoriel Info |
| `i` | Chercher dans les index |
| `s` | Recherche regexp |
| `q` | Quitter Info |

### 25. Registres

| Raccourci | Action |
|-----------|--------|
| `C-x r s` | Sauver région dans registre |
| `C-x r i` | Insérer contenu du registre |
| `C-x r SPC` | Sauver position dans registre |
| `C-x r j` | Sauter à position du registre |

### 26. Macros Clavier

| Raccourci | Action |
|-----------|--------|
| `C-x (` | Commencer enregistrement |
| `C-x )` | Terminer enregistrement |
| `C-x e` | Exécuter macro |
| `C-u C-x (` | Ajouter à la macro |
| `M-x name-last-kbd-macro` | Nommer la macro |
| `M-x insert-kbd-macro` | Insérer définition Lisp |

### 27. Emacs Lisp

| Raccourci | Action |
|-----------|--------|
| `C-x C-e` | Évaluer sexp avant point |
| `C-M-x` | Évaluer defun courante |
| `M-x eval-region` | Évaluer région |
| `M-:` | Évaluer expression |
| `M-x load-library` | Charger bibliothèque Lisp |

**Exemple de définition de raccourcis :**

```elisp
(global-set-key (kbd "C-c g") 'search-forward)
(global-set-key (kbd "M-#") 'query-replace-regexp)
```

**Écrire une commande :**

```elisp
(defun nom-commande (args)
  "documentation"
  (interactive "template")
  body)
```

**Exemple complet :**

```elisp
(defun this-line-to-top-of-window (line)
  "Repositionner ligne courante en haut.
Avec préfixe LINE, placer point sur LINE."
  (interactive "P")
  (recenter (if (null line)
                0
              (prefix-numeric-value line))))
```

### 28. Personnalisation

| Raccourci | Action |
|-----------|--------|
| `M-x customize` | Interface de personnalisation |

---

## Dired - Gestionnaire de Fichiers

### Entrer et Quitter

| Raccourci | Action |
|-----------|--------|
| `C-x d` | Lancer Dired |
| `C-x C-j` | Dired du répertoire du fichier courant (DX) |
| `q` | Quitter Dired |

### Déplacement

| Raccourci | Action |
|-----------|--------|
| `p` | Ligne précédente |
| `n` | Ligne suivante |
| `<` | Ligne de répertoire précédente |
| `>` | Ligne de répertoire suivante |
| `M-}` | Fichier marqué suivant |
| `M-{` | Fichier marqué précédent |
| `M-C-p` | Sous-répertoire précédent |
| `M-C-n` | Sous-répertoire suivant |
| `^` | Répertoire parent |
| `M-C-d` | Premier sous-répertoire enfant |

### Commandes Souris

| Action | Raccourci |
|--------|-----------|
| **Visiter fichier/répertoire** | Bouton 2 (clic milieu) |

### Actions Immédiates sur Fichiers

| Raccourci | Action |
|-----------|--------|
| `f` | Visiter fichier courant |
| `v` | Voir fichier (lecture seule) |
| `o` | Visiter dans autre fenêtre |
| `+` | Créer nouveau sous-répertoire |
| `=` | Comparer fichier avec celui à la marque |

### Marquer et Démarquer

| Raccourci | Action |
|-----------|--------|
| `m` | Marquer fichier/répertoire |
| `u` | Démarquer fichier |
| `M-delete` | Démarquer tous les marqués |
| `* .` | Marquer par extension |
| `* /` | Marquer tous les répertoires |
| `* @` | Marquer tous les liens symboliques |
| `* *` | Marquer tous les exécutables |
| `t` | Inverser marquage |
| `* s` | Marquer tous les fichiers du sous-rép |
| `* %` | Marquer par regexp |
| `* c` | Changer marques en autre caractère |
| `* (` | Marquer par expression Elisp (DX) |

### Modifier le Buffer Dired

| Raccourci | Action |
|-----------|--------|
| `i` | Insérer sous-répertoire |
| `k` | Retirer fichiers marqués de l'affichage |
| `C-u k` | Retirer sous-répertoire |
| `g` | Relire tous les répertoires (garde marques) |
| `s` | Basculer tri nom/date |
| `C-u s` | Éditer options ls |
| `C-_` | Undo (récupérer marques, lignes cachées) |
| `M-$` | Cacher tous les sous-répertoires |
| `$` | Cacher/montrer sous-répertoire |

### Commandes sur Fichiers Marqués

| Raccourci | Action |
|-----------|--------|
| `C` | Copier fichier(s) |
| `R` | Renommer / déplacer fichier(s) |
| `O` | Changer propriétaire |
| `G` | Changer groupe |
| `M` | Changer mode (permissions) |
| `P` | Imprimer fichier(s) |
| `% l` | Noms en minuscules |
| `% u` | Noms en MAJUSCULES |
| `D` | Supprimer fichiers marqués |
| `Z` | Compresser/décompresser |
| `I` | Lancer info sur fichier (DX) |
| `S` | Créer lien(s) symbolique(s) |
| `Y` | Créer lien(s) symbolique(s) relatif(s) |
| `H` | Créer lien(s) dur(s) |
| `A` | Rechercher regexp dans fichiers |
| `Q` | Query-replace regexp sur fichiers marqués |
| `B` | Byte-compiler fichier(s) |
| `L` | Charger fichier(s) |
| `!` | Commande shell sur fichier(s) |
| `&` | Commande shell asynchrone |

### Marquer pour Suppression

| Raccourci | Action |
|-----------|--------|
| `d` | Marquer pour suppression |
| `~` | Marquer fichiers backup (finissant par ~) |
| `#` | Marquer fichiers auto-save |
| `% &` | Marquer fichiers intermédiaires |
| `.` | Marquer backups numériques (.~1~, .~2~) |
| `x` | Exécuter suppressions |
| `% d` | Marquer par regexp pour suppression |

### Commandes avec Expressions Régulières

| Raccourci | Action |
|-----------|--------|
| `% m` | Marquer noms par regexp |
| `% C` | Copier par regexp |
| `% R` | Renommer par regexp |
| `% H` | Lien dur par regexp |
| `% S` | Lien symbolique par regexp |
| `% Y` | Lien symbolique relatif par regexp |
| `% d` | Marquer suppression par regexp |

### Dired et Find

| Commande | Action |
|----------|--------|
| `M-x find-name-dired` | Fichiers dont nom correspond |
| `M-x find-grep-dired` | Fichiers contenant motif |
| `M-x find-dired` | Fichiers basés sur sortie find |

### Aide Dired

| Raccourci | Action |
|-----------|--------|
| `h` | Aide Dired |
| `?` | Résumé et log d'erreurs |

---

## Raccourcis Essentiels

### Top 20 Emacs (Débutants)

| Rang | Raccourci | Action | Catégorie |
|------|-----------|--------|-----------|
| 1 | `C-x C-s` | Sauvegarder | Fichier |
| 2 | `C-x C-f` | Ouvrir fichier | Fichier |
| 3 | `C-x C-c` | Quitter Emacs | Système |
| 4 | `C-g` | Annuler commande | Récupération |
| 5 | `C-/` | Undo | Édition |
| 6 | `C-s` | Recherche avant | Recherche |
| 7 | `C-r` | Recherche arrière | Recherche |
| 8 | `C-x b` | Changer buffer | Buffer |
| 9 | `C-x k` | Tuer buffer | Buffer |
| 10 | `C-a` | Début de ligne | Déplacement |
| 11 | `C-e` | Fin de ligne | Déplacement |
| 12 | `M-<` | Début buffer | Déplacement |
| 13 | `M->` | Fin buffer | Déplacement |
| 14 | `C-SPC` | Placer marque | Marquage |
| 15 | `C-w` | Couper région | Édition |
| 16 | `M-w` | Copier région | Édition |
| 17 | `C-y` | Coller | Édition |
| 18 | `C-x 2` | Diviser fenêtre | Fenêtre |
| 19 | `C-x o` | Autre fenêtre | Fenêtre |
| 20 | `C-h k` | Aide sur touche | Aide |

### Top 10 Dired (Essentiels)

| Rang | Raccourci | Action |
|------|-----------|--------|
| 1 | `C-x d` | Ouvrir Dired |
| 2 | `q` | Quitter Dired |
| 3 | `f` | Visiter fichier |
| 4 | `m` | Marquer fichier |
| 5 | `u` | Démarquer |
| 6 | `d` | Marquer pour suppression |
| 7 | `x` | Exécuter suppressions |
| 8 | `C` | Copier |
| 9 | `R` | Renommer/Déplacer |
| 10 | `+` | Créer répertoire |

---

## Notes Pratiques

### Concepts Clés

**Emacs :**
- **Buffer** : zone de texte en mémoire
- **Window** : vue sur un buffer
- **Frame** : fenêtre système (cadre Emacs)
- **Point** : position du curseur
- **Mark** : autre position (forme une région)
- **Kill ring** : historique des coupes
- **Minibuffer** : ligne de commande d'Emacs

**Unix :**
- **TTY** : terminal (TeleTYpewriter)
- **PID** : Process IDentifier
- **Daemon** : processus en arrière-plan

### Stratégie d'Apprentissage

1. **Semaine 1** : Top 10 raccourcis Emacs
2. **Semaine 2** : Déplacement et édition de base
3. **Semaine 3** : Recherche et fenêtres multiples
4. **Semaine 4** : Dired et gestion de fichiers
5. **Ongoing** : Exploration progressive des fonctionnalités avancées

### Conseils

- **Pratiquez régulièrement** : muscle memory est essentiel
- **Utilisez C-h** : l'aide intégrée est votre amie
- **Personnalisez progressivement** : commencez simple
- **N'abandonnez pas** : courbe d'apprentissage initiale raide mais payante
- **Explorez les modes** : chaque type de fichier a ses raccourcis spécifiques

### Ressources Supplémentaires

- **Tutoriel intégré** : `C-h t` dans Emacs
- **Documentation GNU** : https://www.gnu.org/software/emacs
- **Info pages** : `info emacs` dans le terminal
- **Wiki EmacsWiki** : https://www.emacswiki.org

---

## Licence

Ce document est basé sur :
- Mémento Système 1 - Université de Nice Côte d'Azur
- GNU Emacs Reference Card (version 29) © 2024 FSF
- Dired Reference Card © 2024 FSF

Publié sous GNU General Public License version 3 ou ultérieure.

---

**Dernière mise à jour** : Janvier 2026

**Note** : Les commandes marquées (DX) nécessitent l'extension `dired-x`.
