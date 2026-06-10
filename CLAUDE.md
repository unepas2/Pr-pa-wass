# CADRE — autodiagnostic de gouvernance IA (V0)
- Un seul fichier `index.html` (HTML + CSS + JS inline), sans framework ni build ; seule dépendance : Google Fonts « Plus Jakarta Sans » (400/600/800). Statique Cloudflare Pages, mobile-first.
- Tout en français, vouvoiement, zéro jargon ; questions, recommandations et mentions = textes fournis, jamais reformulés ; ne jamais inventer de contenu juridique.
- Aucune donnée envoyée à un serveur, sauf l'email (consentement explicite, case non pré-cochée) ; l'email n'est JAMAIS stocké en localStorage.
- localStorage, clé `cadre.diagnostic.v1` : réponses par id de question, question courante, dates.
- Mention obligatoire (résultats + impression) : « Cet autodiagnostic est un outil de sensibilisation. Il ne constitue ni un conseil juridique ni un audit de conformité. »
- Design « dossier officiel » : encre #1C2B3A, papier #FBFAF7, vert #0F6E56, ambre #B97514, rouge #A32D2D ; tampon incliné −3° (cercle intérieur pointillé, animation d'impact + compteur) ; boutons 8 px, cartes 12 px, options ≥ 56 px ; micro-interactions 150–550 ms, tampon/compteur/barres animés une seule fois, tout est coupé par prefers-reduced-motion.
- Accessibilité AA : navigation clavier, focus visibles, labels, contrastes, prefers-reduced-motion.
- Barème : question 0–20 ; axe = total des 3 questions / 60 × 100 arrondi ; global = moyenne des 5 axes arrondie ; seuils ≥ 65 vert, 45–64 ambre, < 45 rouge ; priorités = 3 axes les plus faibles, égalité départagée par D > R > A > C > E.
- Navigation par hash : accueil (/), #diagnostic, #resultats, #mentions, #confidentialite.
