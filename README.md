🇺🇸 Tampermonkey userscript: Bypass the "9+" limit! Forces the YouTube bell to show the exact unread count by extracting it from the tab title. 

🇫🇷 Script Tampermonkey : Contournez la limite "9+" ! Affiche le nombre exact de notifications sur la cloche YouTube en le récupérant depuis le titre de l'onglet. Script by csrrrr aka Cyrilplayerone 🚀


# 🔔 YouTube Exact Notification Badge (Bypass 9+ Limit)

**Created by Cyrilplayerone**

[![Install with Tampermonkey]

___________________________________________________________________________


// ==UserScript==
// @name         YouTube Exact Notification Badge (Bypass 9+ Limit)
// @namespace    yt-exact-bell-badge
// @version      1.0
// @description  Forces the YouTube notification bell to show the exact number of unread notifications instead of "9+" by extracting it from the tab title.
// @author       Cyrilplayerone
// @match        *://*.youtube.com/*
// @grant        none
// @run-at       document-idle
// @license      MIT
// ==/UserScript==

(function () {
    'use strict';

    function forceUpdateBell() {
        // Extract the exact notification count from the document title (e.g., "(37) YouTube")
        const m = document.title.match(/^\((\d+)\)\s+/);
        if (!m) return;
        
        const count = m[1];
        
        // Target the YouTube bell badge
        const badges = document.querySelectorAll('.yt-spec-icon-badge-shape__badge');
        
        badges.forEach(badge => {
            if (badge.textContent !== count) {
                badge.textContent = count;
            }
        });
    }

    // Run every 500ms to prevent YouTube's dynamic frontend from reverting to "9+"
    setInterval(forceUpdateBell, 500);

})();


___________________________________________________________________________


### 🇺🇸 English Description

Tired of seeing **"9+"** on your YouTube notification bell when you actually have 37 unread notifications? 

YouTube truncates the notification badge visually, but ironically, it still displays the *exact* count in the browser's tab title (e.g., `"(37) YouTube"`). 
This lightweight Tampermonkey userscript acts as a clever bridge: it dynamically extracts the real number from the tab title and forces the bell icon to display the exact count. No API keys required, no heavy background processes!

#### ✨ Features:
* **🚀 Bypasses the "9+" Limit:** See your true notification count at a glance.
* **⚡ Ultra-Lightweight:** Only a few lines of vanilla JavaScript. No performance impact.
* **🛡️ Bulletproof:** Uses a seamless 500ms interval to ensure YouTube's dynamic page loading (SPA) doesn't overwrite your exact count.
* **🔌 Plug & Play:** Install it via Tampermonkey and forget about it.

#### 🛠️ Installation:
1. Install the [Tampermonkey](https://www.tampermonkey.net/) extension for your browser.
2. Ensure "User scripts" are allowed/enabled in your browser's extension settings.
3. Add this script and refresh YouTube if necessary!

---

### 🇫🇷 Description en Français

Fatigué de voir **"9+"** sur la cloche de notifs YouTube alors que vous avez en réalité 37 notifications en attente ?

YouTube bloque visuellement le compteur de la cloche, mais ironiquement, il continue d'afficher le nombre *exact* dans le titre de l'onglet du navigateur (ex: `"(37) YouTube"`). 
Ce script Tampermonkey ultra-léger utilise une astuce simple : il récupère le vrai nombre depuis le titre de la page et force l'icône de la cloche à afficher ce compte exact. Pas besoin de clés API, pas de processus lourds en arrière-plan !

#### ✨ Fonctionnalités :
* **🚀 Fini la limite "9+" :** Voyez votre vrai nombre de notifications en un clin d'œil.
* **⚡ Ultra-léger :** Quelques lignes de JavaScript pur. Aucun impact sur les performances.
* **🛡️ Indestructible :** Utilise une boucle invisible de 500ms pour empêcher YouTube d'écraser le vrai nombre lors du rechargement dynamique de la page.
* **🔌 Plug & Play :** Installez-le via Tampermonkey et n'y pensez plus.

#### 🛠️ Installation :
1. Installez l'extension [Tampermonkey](https://www.tampermonkey.net/) sur votre navigateur.
2. Assurez-vous que l'exécution des scripts utilisateur est autorisée dans les paramètres de l'extension.
3. Ajoutez ce script et rafraîchissez YouTube si nécessaire ! 
