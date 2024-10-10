
![Logo](https://i.ibb.co/B683C8d/ublog-logo.png)
# µ-billet : 10 octobre 2024 

Dans ce point-tech, nous avons abordé des sujets  autour des frameworks, de l’hébergement, et de l’amélioration des outils de développement.

1.  **Framework « One » : React WEB + NATIVE simplifié**
2.  **Retour d'expérience : Migration de Vercel à Cloudflare et de NodeJS à Bun**
3.  **Discussion sur les solutions d’hébergement**
4.  **VSCode et directives LLM : Test & avis sur Cursor**

----------

## 1. Le framework « One » : Successeur de Tamagui 

Lors d'un précédent point-tech, nous avions présenté **Tamagui**, qui montrait certaines lacunes :

-   Structure trop complexe avec NextJS + Expo.
-   NextJS avait un routing `app directory`, mais pas encore Expo.
-   Le Css-in-JS n'était pas entièrement finalisé.

![enter image description here](https://i.ibb.co/843wPg3/Frame.png)L'évolution de tamagui et maintenant le framework **One** corrige ces lacunes et le développement **web et natif en React**. est maintenant unifié.

Ses principaux atouts :

-   **Structure** : Intègre Vite, typage, routing et un boilerplate complet.
-   **UI intégrée** : Simplifie la conception d'interfaces natives.

Un outil prometteur à tester pour de prochaines applications.

**Côté Expo** :  
La nouvelle directive **`use-dom`** facilite l’utilisation du DOM dans des environnements React Native. Ce n’est pas une bonne pratique, mais elle permet de gagner du temps pour intégrer une page complète d'éléments React.

**"Désaccords"** : Nate Wienert, figure de la communauté React, critique publiquement l'investissement massif de Vercel dans le rendu côté serveur, qu'il juge souvent inutile. Un débat intéressant a eu lieu entre Guillermo Rauch (CEO de Vercel) et Nate Wienert (One), qui frôle le drama. 🫶

----------

## 2. Retour d'expérience : Migration d'un projet

Présentation d'une migration réalisée cette semaine :

**NodeJS 20 -> Bun**

-   **Amélioration des performances** : Bun a montré une nette supériorité en termes de vitesse par rapport à NodeJS.
D'habitude, les benchmarks sont "surcoté", mais là c'est le cas !
(Très bonne DX)

**Vercel -> Cloudflare**

-   **Coûts divisés par 4** : Cloudflare s’avère bien plus économique (si le pricing reste stable).
-   **Contrôle accru** : Cette migration réduit la dépendance totale à Vercel, dont les tarifs sont 5 fois plus élevés que la S3 d'AWS.
-   Le déploiement, le stockage des bases de données (R1) et le stockage média (D2) ont également été migrés.
- **Build avec CI/CD** : Fichiers customs pour gérer des actions de déploiement.

**Eslint & Prettier -> Biome**

-   **Échec** : Malgré les avantages de **BiomeJS**, son intégration est encore incomplète. Plusieurs librairies CSS restent incompatibles avec son parser. Une nouvelle tentative sera prévue dans les prochains mois.

----------

## 3. Discussion sur les solutions d’hébergement

Cette migration a ouvert une discussion plus large sur les solutions d’hébergement :

-   Contrôle des données
-   Politique de tarification
-   Impact environnemental : Un build Vercel est effectué à Washington, une région qui dépend beaucoup du gaz et du charbon, générant 11 fois plus de pollution par kWh (CO₂eq/kWh).  
    [Electricity Map](https://app.electricitymaps.com/map?lang=fr)
**Octopus** a été présenté comme alternative à AWS et l'équipe gère majoritairement manuellement les déploiements sur divers projets.
----------

## 4. Cursor et autres forks de VSCode

Nous avons testé **Cursor**, un fork de **VSCode** intégrant des modèles de langage (LLM) pour automatiser l’écriture de code. Les fichiers `.cursorrules` sont de plus en plus présents dans les projets, orientant l'IA pour produire du code plus optimisé.

### Exemples de directives (prompts) :

Ces directives visent à minimiser ce que vous jugez indésirable. Exemple :

<small> <b>Utilisation de TypeScript</b> </small> <small> - Utilisez TypeScript pour tout le code ; - Préférez les interfaces aux types. Évitez les enums, utilisez des maps à la place. Utilisez des composants fonctionnels avec des interfaces TypeScript. </small> <small> <b>Syntaxe et formatage</b> </small> <small> - Utilisez le mot-clé "function" pour les fonctions pures. - Évitez les accolades inutiles dans les conditions ; privilégiez une syntaxe concise pour les instructions simples. - Utilisez du JSX déclaratif. </small>

----------

**Discussions** : Nous avons débattu des tarifs, soulignant l’inefficacité relative de Github Copilot face à l'efficacité de Claude.

**Alternatives** :
- Continu : Extension VS-Code
- Jetbrains semble aussi développer des solutions.
