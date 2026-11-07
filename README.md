# Journal privé des mariages 2028

L’Atelier Fleurs & Sens — tableau de suivi des inscriptions.

Adresse à configurer : https://journalmariages2028.latelierfleursetsens.fr/

Le journal utilise le service Cloudflare et la base D1 existants. Les inscriptions, notes, statuts et confirmations d’envoi restent communs au formulaire et au journal. La connexion au compte de l’atelier reste obligatoire ; le service contrôle les droits avant de transmettre les inscriptions.

## 1. Créer le dépôt GitHub

Créer un dépôt public nommé `journal-mariages-2028` dans le compte `latelierfleursetsens-create`.

Décompresser le ZIP puis téléverser tout son contenu à la racine du dépôt : `index.html` doit se trouver au premier niveau, à côté des dossiers `assets` et `js`. Les fichiers `CNAME`, `robots.txt` et `README.md` sont également au premier niveau. Le fichier `.nojekyll` est fourni dans le ZIP.

Valider le téléversement avec Commit changes.

## 2. Activer GitHub Pages

Dans Settings → Pages, choisir Deploy from a branch, puis `main` et `/ (root)`, et enregistrer.

Dans Custom domain, utiliser exactement :

```text
journalmariages2028.latelierfleursetsens.fr
```

Le fichier CNAME contient déjà cette adresse. Si le champ Custom domain est déjà renseigné correctement, conserver cette valeur.

## 3. Relier le domaine dans Squarespace

Après l’enregistrement de l’adresse sur GitHub, ajouter un enregistrement DNS :

| Champ | Valeur |
|---|---|
| Type | CNAME |
| Nom | journalmariages2028 |
| Données | latelierfleursetsens-create.github.io |
| TTL | 4 h |

Attendre la validation DNS dans GitHub Pages, puis cocher Enforce HTTPS dès que la case est disponible.

## 4. Autoriser le journal dans Cloudflare

Dans le Worker `broad-pine-7f6catelier-fleurs-attente2028`, modifier la variable existante ALLOWED_ORIGINS :

```text
https://latelierfleursetsens-create.github.io,https://mariage2028.latelierfleursetsens.fr,https://journalmariages2028.latelierfleursetsens.fr
```

Enregistrer et déployer. PUBLIC_SITE_URL reste l’adresse du formulaire :

```text
https://mariage2028.latelierfleursetsens.fr/
```

Les liaisons DB et MAIL_SERVICE du Worker sont déjà configurées. Ce dossier contient uniquement l’interface du journal.

## 5. Connexion et vérification

Dans Firebase Authentication → Paramètres → Domaines autorisés, le domaine `journalmariages2028.latelierfleursetsens.fr` doit être présent. Cette étape a déjà été réalisée pendant la configuration.

Ouvrir l’adresse du journal, choisir la connexion Google et utiliser `latelierfleursetsens@gmail.com`.

Vérifier que les inscriptions existantes apparaissent. La création d’une autre base ou la réinscription des clientes est inutile.

Les liens « Revenir au formulaire » et « Voir le formulaire » ouvrent https://mariage2028.latelierfleursetsens.fr/.

Le tableau reste également disponible à https://mariage2028.latelierfleursetsens.fr/gestion.html pour les liens déjà utilisés.
