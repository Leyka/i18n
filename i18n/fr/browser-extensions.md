---
title: Extensions de navigateur
icon: material/puzzle-outline
description: Ces extensions de navigateur peuvent améliorer votre expérience de navigation et protéger votre vie privée.
cover: browser-extensions.webp
---

<small>Protège contre les menaces suivantes:</small>

- [:material-account-cash: Capitalisme de surveillance](basics/common-threats.md#surveillance-as-a-business-model){ .pg-brown }

De manière générale, nous recommandons de limiter le nombre d'extensions installées dans votre navigateur afin de réduire la surface d'attaque. Les raisons sont les suivantes: 
elles ont un accès étendu, reposent sur la confiance envers leurs développeurs, peuvent faciliter votre [identification](https://fr.wikipedia.org/wiki/Empreinte_digitale_d%27appareil) (_fingerprinting_), et [affaiblir](https://groups-google-com.translate.goog/a/chromium.org/g/chromium-extensions/c/0ei-UCHNm34/m/lDaXwQhzBAAJ?_x_tr_sl=en&_x_tr_tl=fr&_x_tr_hl=fr&_x_tr_pto=wapp) la séparation entre les sites web.

Cependant, certaines offrent des fonctionnalités qui peuvent compenser ces inconvénients dans certaines situations, notamment pour le [blocage de contenu](basics/common-threats.md#mass-surveillance-programs).

N’installez pas d’extensions dont vous n’avez pas un besoin immédiat, ou qui dupliquent des fonctions déjà présentes dans votre navigateur. Par exemple, les utilisateurs de [Brave](desktop-browsers.md#brave) n’ont pas besoin d’installer uBlock Origin, car Brave Shields fournit déjà cette fonctionnalité.

## Bloqueurs de contenu

### uBlock Origin

<div class="admonition recommendation" markdown>

![uBlock Origin logo](assets/img/browsers/ublock_origin.svg){ align=right }

**uBlock Origin** est un bloqueur de contenu populaire qui vous aide à bloquer les publicités, les traqueurs et les scripts de _fingerprinting_.

[:octicons-repo-16: Repository](https://github.com/gorhill/uBlock#readme){ .md-button .md-button--primary }
[:octicons-eye-16:](https://github.com/gorhill/uBlock/wiki/Privacy-policy){ .card-link title="Politique de confidentialité" }
[:octicons-info-16:](https://github.com/gorhill/uBlock/wiki){ .card-link title=Documentation}
[:octicons-code-16:](https://github.com/gorhill/uBlock){ .card-link title="Code source" }

<details class="downloads" markdown>
<summary>Téléchargements</summary>

- [:simple-firefoxbrowser: Firefox](https://addons.mozilla.org/firefox/addon/ublock-origin)
- [:simple-googlechrome: Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm)
- [:fontawesome-brands-edge: Edge](https://microsoftedge.microsoft.com/addons/detail/ublock-origin/odfafepnkmbhccpbejgmiehpchacaeak)

</details>

</div>

Nous vous conseillons de suivre la [documentation du développeur](https://github.com/gorhill/uBlock/wiki/Blocking-mode) et de choisir un des "modes" proposés. Des listes de filtres supplémentaires peuvent affecter les performances et [augmenter la surface d'attaque](https://portswigger.net/research/ublock-i-exfiltrate-exploiting-ad-blockers-with-css).

Voici quelques autres [listes de filtres](https://github.com/gorhill/uBlock/wiki/Dashboard:-Filter-lists) que vous pourriez envisager d’ajouter :

- [x] Cochez **Privacy** > **AdGuard URL Tracking Protection**
- Ajoutez [Actually Legitimate URL Shortener Tool](https://raw.githubusercontent.com/DandelionSprout/adfilt/master/LegitimateURLShortener.txt)

### uBlock Origin Lite

uBlock Origin dispose également d’une version "Lite" qui propose un ensemble de fonctionnalités très limitées par rapport à l’extension originale. Cependant, elle présente certains avantages distincts, et pourrait vous convenir si...

- ...vous ne souhaitez pas accorder d’accès complet en lecture/modification des données de site à une extension (même une fiable comme uBlock Origin)
- ...vous souhaitez un bloqueur de contenu plus léger en mémoire/CPU[^1]
- ...votre navigateur ne prend en charge que les extensions au format Manifest V3

<div class="admonition recommendation" markdown>

![uBlock Origin Lite logo](assets/img/browsers/ublock_origin_lite.svg){ align=right }

**uBlock Origin Lite** est une extension compatible avec Manifest V3. Contrairement à la version classique _uBlock Origin_, elle ne requiert pas d’autorisation générale pour lire/modifier les données des sites, ce qui réduit les risques d’[:material-bug-outline: Attaques passives](basics/common-threats.md#security-and-privacy){ .pg-orange } si une règle malveillante est introduite dans une liste.

[:octicons-repo-16: Dépôt](https://github.com/uBlockOrigin/uBOL-home#readme){ .md-button .md-button--primary }
[:octicons-eye-16:](https://github.com/uBlockOrigin/uBOL-home/wiki/Privacy-policy){ .card-link title="Politique de confidentialité" }
[:octicons-info-16:](https://github.com/uBlockOrigin/uBOL-home/wiki){ .card-link title=Documentation}
[:octicons-code-16:](https://github.com/gorhill/uBlock/tree/master/platform/mv3){ .card-link title="Code source" }

<details class="downloads" markdown>
<summary>Téléchargements</summary>

- [:simple-googlechrome: Chrome](https://chrome.google.com/webstore/detail/ublock-origin-lite/ddkjiahejlhfcafbddmgiahcphecmpfh)

</details>

</div>

Nous recommandons cette version de uBlock Origin uniquement si vous ne souhaitez jamais apporter de modifications à vos listes de filtres, car elle ne prend en charge que quelques listes pré-sélectionnées et n'offre aucune option de personnalisation supplémentaire, y compris la possibilité de sélectionner manuellement les éléments à bloquer. Ces restrictions sont dues aux limitations du design de Manifest V3.

Cette version propose trois niveaux de blocage : "Basique" fonctionne sans nécessiter de privilèges spéciaux pour afficher et modifier le contenu des sites, tandis que les niveaux "Optimal" et "Complet" nécessitent une permission étendue, mais offrent une meilleure expérience de filtrage avec des règles cosmétiques supplémentaires et des injections de script.

Si vous définissez le mode de filtrage par défaut sur "Optimal" ou "Complet", l'extension demandera un accès en lecture/écriture à **tous les sites** que vous visitez. Cependant, vous avez également la possibilité de modifier le paramètre à "Optimal" ou "Complet" sur une base de "**par site**" en ajustant le curseur dans le panneau contextuel de l'extension sur n'importe quel site donné. L'extension demandera donc un accès en lecture/écriture à ce site uniquement. 
Par conséquent, si vous souhaitez profiter de la configuration "sans autorisation" de uBlock Origin Lite, vous devriez probablement laisser le paramètre par défaut sur "Basique" et ne l'ajuster à un niveau supérieur que sur les sites où ce niveau n'est pas suffisant.

uBlock Origin Lite ne reçoit des mises à jour de la liste de blocage que lorsque l'extension est mise à jour depuis le store des extensions de votre navigateur, et non à la demande. Cela signifie que vous pourriez manquer de nouveaux menaces bloquées pendant des semaines jusqu'à ce qu'une nouvelle version complète de l'extension soit publiée.

### AdGuard

Nous recommandons [Safari](mobile-browsers.md#safari-ios) pour les utilisateurs iOS, qui n’est malheureusement pas compatible avec uBlock Origin. Heureusement, AdGuard fournit une alternative adéquate :

<div class="admonition recommendation" markdown>

![AdGuard logo](assets/img/browsers/adguard.svg){ align=right }

**AdGuard pour iOS** est une extension gratuite et open-source pour Safari qui utilise l’API native [Content Blocker](https://developer.apple.com/documentation/safariservices/creating_a_content_blocker).

[:octicons-home-16: Page d'accueil](https://adguard.com/en/adguard-ios/overview.html){ .md-button .md-button--primary }
[:octicons-eye-16:](https://adguard.com/privacy/ios.html){ .card-link title="Politique de confidentialité" }
[:octicons-info-16:](https://kb.adguard.com/ios){ .card-link title=Documentation}
[:octicons-code-16:](https://github.com/AdguardTeam/AdguardForiOS){ .card-link title="Code source" }

<details class="downloads" markdown>
<summary>Téléchargements</summary>

- [:simple-appstore: App Store](https://apps.apple.com/app/id1047223162)

</details>

</div>

Les listes de filtres supplémentaires ralentissent la navigation et peuvent augmenter votre surface d'attaque. N'appliquez donc que ce dont vous avez besoin. AdGuard pour iOS dispose de quelques fonctions payantes, mais le blocage standard du contenu de Safari est gratuit.

## Critères

- Ne doit pas dupliquer une fonctionnalité intégrée dans le navigateur ou dans le système d'exploitation.
- Doit avoir un impact direct sur la vie privée des utilisateurs, c'est-à-dire qu'il ne doit pas simplement fournir des informations.

[^1]: uBlock Origin Lite _en soi_ ne consommera aucune ressource, car il utilise des API récentes qui permettent au navigateur de traiter les filtres nativement, au lieu de faire tourner du JavaScript. Cela dit, cet avantage est [théorique](https://github.com/uBlockOrigin/uBOL-home/wiki/Frequently-asked-questions-%28FAQ%29#is-ubol-more-efficient-cpu--and-memory-wise-than-ubo), car il est possible que le code JavaScript d’uBlock Origin soit plus efficace que celui intégré au navigateur. Cela n'a pas encore fait l'objet de tests comparatifs.
