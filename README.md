# Naveroshop : guide de publication

Ce site est une boutique simple. Les clients choisissent des produits, remplissent leurs coordonnées et envoient leur commande par WhatsApp. Aucun paiement en ligne, aucune base de données, aucun abonnement requis.

## 1. Télécharger et décompresser
Téléchargez le fichier ZIP, puis décompressez-le. Vous obtenez un dossier `naveroshop`.

## 2. Créer un dépôt GitHub
1. Connectez-vous sur https://github.com (créez un compte gratuit si besoin).
2. Cliquez sur le bouton **+** puis **New repository**.
3. Nommez le dépôt `naveroshop`, laissez-le en **Public** ou **Private**, puis cliquez sur **Create repository**.

## 3. Envoyer les fichiers sur GitHub
Sur la page du dépôt vide, cliquez sur **uploading an existing file**, glissez **tout le contenu** du dossier `naveroshop` (les fichiers et sous-dossiers, pas le dossier lui-même) puis cliquez sur **Commit changes**.

## 4. Connecter GitHub à Vercel
1. Allez sur https://vercel.com et créez un compte gratuit avec votre compte GitHub.
2. Cliquez sur **Add New… → Project**, puis **Import** à côté de votre dépôt `naveroshop`.
3. Vercel détecte automatiquement Vite. Vérifiez : Build Command `npm run build`, Output Directory `dist`, Install Command `npm install`.

## 5. Déployer
Cliquez sur **Deploy**. Après une minute environ, Vercel vous donne une adresse du type `naveroshop.vercel.app`. Ce sous-domaine gratuit suffit pour commencer, sans acheter de nom de domaine.

## 6. Numéro WhatsApp
Le numéro de commande est déjà configuré dans `src/config.js` (`33652327610`). Pour le changer, modifiez `WHATSAPP_NUMBER` : indicatif pays, sans `+` ni espaces. Enregistrez sur GitHub (**Edit** puis **Commit changes**) : Vercel redéploie automatiquement.

## 7. Ajouter un produit
Ouvrez `src/data/products.js` et copiez un bloc `{ ... }` existant. Modifiez `id` (unique, sans espaces), `name`, `description`, `price`, `oldPrice` (`null` si aucun), `category`, `photos`, `available` et `stock`. Mettez `stock: null` si vous ne voulez pas limiter les quantités.

## 8. Modifier les prix et les photos
- **Prix** : changez le champ `price` (en DH) du produit.
- **Photos** : ajoutez vos images dans le dossier `public/images/` (par exemple `byphasse.jpg`), puis dans `photos` écrivez `'/images/byphasse.jpg'`. Remplacez `placeholder.svg` tant que la photo n'est pas prête.
- **Nom de la boutique** : modifiez `SHOP.name` dans `src/config.js`.

## Tester en local (optionnel)
Si vous avez Node.js installé : `npm install`, puis `npm run dev`, puis ouvrez l'adresse affichée.

## Notes
- Les prix barrés ne s'affichent que si vous renseignez `oldPrice`.
- Le panier est conservé sur l'appareil du client, même après actualisation de la page.
- Le bouton WhatsApp flottant n'apparaît que lorsque le numéro est configuré.
- La section « Questions fréquentes » se modifie dans `src/App.jsx` (variables `faq` en français et en arabe).

## Ajouter des avis clients
Ouvrez `src/data/reviews.js` et ajoutez vos avis dans la liste `reviews`, uniquement avec de vrais avis et l'accord du client. La section « Avis clients » apparaît dès qu'il y a au moins un avis. Tant qu'elle est vide, elle reste cachée.

## Aperçu quand on partage le lien (WhatsApp, Facebook, Instagram)
Dans `index.html`, remplacez `VOTRE-SITE.vercel.app` par l'adresse réelle de votre site (celle que Vercel vous donne, par exemple `naveroshop.vercel.app`) dans les lignes `og:image` et `twitter:image`. Une fois le site déployé, faites un nouveau déploiement avec GitHub.

Les applications gardent parfois l'ancien aperçu en mémoire. Si l'image n'apparaît pas tout de suite, attendez quelques minutes ou envoyez le lien à nouveau.

Pour vérifier l'aperçu, vous pouvez coller votre lien dans WhatsApp, ou utiliser l'outil gratuit « Facebook Sharing Debugger ».
