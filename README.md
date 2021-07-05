# Présentation RadarTech

## Vision d'ensemble

RadarTech est un outil de d'exploitation de questionnaires. Il permet la soumission de questionnaires aux milliers d'agents concernés via un site web dédié, puis de la production d'une page avec les résultats obtenus. La DINUM ne souhaite pas recourir à des outils de sondage classique car elle vise une accessibilité maximale et une expérience utilisateur propre à ce site, tant pour les questions que pour la présentation des résultats.

## Articulation

Ce projet s'articule en plusieurs dépôts : 
* [RadarTech](https://github.com/etalab/radar-tech): présentant le projet et sa documentation
* [RadarTech Front](https://github.com/etalab/radar-tech-frontend): contenant le Frontend de l'application
* [RadarTech Backend](https://github.com/etalab/radar-tech-backend): contenant le Backend de l'application
* [RadarTech Form](https://github.com/etalab/radar-tech-form): contenant les questionnaires

Le **Frontend** étant la partie présentée directement à l'utilisateur, l'interface utilisateur.

Le **Backend** étant la partie immergée de l'application, véritable cheffe d'orchestre des interactions avec la base de données (création des questionnaires, stockage & récupération des informations reccueillies à partir des différents questionnaires, création d'un utilisateur, authentification d'un utilisateur, ...).

## Suivi

### Avancement

[Avancement du projet à suivre ici](https://github.com/etalab/radar-tech/projects/1)

### Archive des points, rendez-vous, conversations (ordre chronologique)

* [23 nov. 2020](https://github.com/etalab/radar-tech/blob/main/documents/23-11-2020.md): Premier backlog
* [25 nov. 2020](https://github.com/etalab/radar-tech/blob/main/documents/25-11-2020.md): Lancement du projet, deadlines
* [22 dec. 2020](https://github.com/etalab/radar-tech/blob/main/documents/22-12-2020.md): Point avec Bastien pré-fêtes de fin d'année
* [23 fev. 2021](https://github.com/etalab/radar-tech/blob/main/documents/23-02-2021-design.md): Point avec Bastien re: design
* [2 mars 2021](https://github.com/etalab/radar-tech/blob/main/documents/02-03-2021-etalab.md): Feedback Etalab
* [17 juin 2021](https://github.com/etalab/radar-tech/blob/main/documents/17-06-2021.md): Point

## Documentation questionnaire
### Structure type

Pour créer un nouveau questionnaire métier, il faut suivre cette structure type :

```
{
  "key": 1,
  "metier": "designer",
  "metier_str": "Designers",
  "metier_icon": "icon-design.jpeg",
  "description": "One who creates and often executes plans for a project or structure ; One that creates and manufactures a new product style or design especially : one who designs and manufactures high-fashion clothing ",
  "questionnaire": {
    "title": "Questions profession designer",
    "description": "",
    "key": "designers",
    "pages": [
      {
        "name": "page1",
        "title": "Qui sont ces designer ?",
        "elements": [
          {
            "type": "radiogroup",
            "name": "demo_genre",
            "title": "À quel genre vous identifiez-vous ?",
            "isRequired": true,
            "choices": [
              "Homme",
              "Femme",
              "Non-binaire, genderqueer, ou gender non-conforming"
            ]
          },
          {
            "type": "dropdown",
            "name": "demo_age",
            "title": "Dans quelle tranche d’âge vous situez vous ?",
            "choices": [
              "15-19",
              "20-24",
              "25-29",
              "30-34",
              "35-39",
              "40-44",
              "45-49",
              "50-54",
              "55-59",
              "60-64",
              "65+"
            ]
          },
          {
            "type": "dropdown",
            "name": "demo_titre",
            "title": "Quels termes décrivent le mieux votre position au sein de l'administration ?",
            "choices": [
              "Ingénieur informatique",
              "Développeur informatique",
              "Développeur web",
              "Développeur front-end",
              "Développeur back-end",
              "Développeur mobile",
              "Designer",
              "Datascientist",
              "Technicien de maintenance",
              "Chef·fe de projet",
              "Chef de produit",
              "Manager",
              "Cadre",
              "DevOps",
              "SRE",
              "Administrateur",
              "Expert en sécurité informatique",
              "Consultant",
              "Scrum-master",
              "Commerciale",
              "Directeur"
            ]
          },
          {
            "type": "dropdown",
            "name": "demo_fonctions",
            "title": "Quelles fonctions remplissez-vous dans votre administration ?",
            "choices": [
              "Développement informatique",
              "Support informatique",
              "Design de service",
              "Web design",
              "Maintenance",
              "Administration réseau",
              "Administration de base de données",
              "Sécurité des réseaux"
            ]
          },
          {
            "type": "radiogroup",
            "name": "demo_administration",
            "title": "De quelle administration dépendez-vous ?",
            "choices": ["Ministère", "Branche", "Administration"],
            "colCount": 3
          },
          {
            "type": "radiogroup",
            "name": "demo_status",
            "title": "Sous quel statut ?",
            "choices": ["CDI", "CDD", "Freelance", "Autre"],
            "colCount": 4
          },
          {
            "type": "radiogroup",
            "name": "demo_rythme",
            "title": "À quel rythme ?",
            "choices": ["À plein-temps", "À mi-temps"],
            "colCount": 2
          },
          {
            "type": "radiogroup",
            "name": "travail_activite",
            "title": "Avez-vous une autre activité en parallèle ?",
            "choices": ["Oui", "Non"],
            "colCount": 2
          },
          {
            "type": "checkbox",
            "name": "travail_activite_autre",
            "title": "Précisez:",
            "visibleIf": "{travail_activite}= 'Oui'",
            "choices": ["Freelance", "CDI", "CDD"],
            "hasOther": true
          },
          {
            "type": "radiogroup",
            "name": "demo_entree_admin",
            "title": "Comment avez-vous obtenu votre poste au sein de l’administration ?",
            "choices": [
              "Concours",
              "Détachement",
              "Candidature",
              "Appel d'offre"
            ],
            "colCount": 2
          }
        ]
      },
      {
        "name": "page2",
        "elements": [
          {
            "type": "text",
            "name": "email",
            "title": "Votre adresse email",
            "isRequired": true,
            "validators": [
              {
                "type": "email"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

Ensuite, il faut enregistrer le fichier en `<metier>.json`.

### Importer dans RadarTech

#### Backend

Il faut créer le modèle dans la DB pour chaque fichier de la forme `<metier>.json` nouvellement créé (cf. [Créer le modèle](Creer-le-modele)).

#### Frontend

Il faut placer les fichiers de la forme `<metier>.json` nouvellement créés dans le dossier `pages-métiers`.

**Attention** : Il ne faut pas oublier de rajouter les images de présentation indiquées ici `"metier_icon": "<icon-metier>.jpeg",` dans le dossier `static` sous le même nom que dans le JSON `<icon-metier>.jpeg`.

## Documentation déploiement

Pour déployer RadarTech, il faut commencer par déployer le Backend puis le Frontend.

### Créer le modèle

```
git clone https://github.com/etalab/radar-tech-backend.git
cd radar-tech-backend/scripts
node createSchema <chemin_metier_json>
```

### Créer l'application Dokku (Backend)

```
dokku apps:create <nom_application>
```

#### Ajouter les variables d'environnement

```
dokku config:set <nom_application> API_URL=http://<nom_application>.app.etalab.studio
dokku config:set <nom_application> ACCESS_TOKEN_TYPE='Bearer'
dokku config:set <nom_application> ACCESS_TOKEN_ALGORITHM='HS256'
dokku config:set <nom_application> ACCESS_TOKEN_SECRET='<token_secret>'
dokku config:set <nom_application> SIB_API_KEY=<sendinblue_api_key>
```

`<token_secret>` correspond à la clé secrète utilisée pour générer les token

#### Créer la base de données

```
dokku mongo:create <mongo_service_name>
dokku mongo:link <mongo_service_name> <nom_application>
```

Le résultat retourné correspond à l'adresse de connexion à la DB, au format :

`mongodb://<service_name>:2652096c746158e0fd896ff2b7416877@<service_user>:27017/<nom_db>`

La commande `mongo:link` va automatiquement ajouter l'URL vers Mongo en variable d'environnement.

A ce stade, il doit y avoir au moins ces 6 variables d'environnement.

Pour vérifier, il est possible de les lister :

```
dokku config:show <nom_application>

ACCESS_TOKEN_ALGORITHM:  HS256
ACCESS_TOKEN_SECRET:     <token_secret>
ACCESS_TOKEN_TYPE:       Bearer
API_URL:                 http://<nom_application>.app.etalab.studio
MONGO_URL:               mongodb://<mongo_service_name>:<number_generated_by_dokku_service>@dokku-mongo-<mongo_service_name>:27017/<nom_db>
SIB_API_KEY:             <sendinblue_api_key>
```

### Tester

```
cd ..
npm install
npm run dev
```

### Créer un token

En amont, il faut créer un utilisateur manuellement (à améliorer).

Il n'y a pas d'interface d'administration, donc la création de l'utilisateur est semi-automatisée.

#### Créer le salt et hash d'un mot de passe

```
cd script
node createHashAndSalt.js <nom_utilisateur> <mot_de_passe>
```

Le salt et le mot de passe hashé sont affichés dans la console

#### Créer un utilisateur dans la base de données

```
dokku mongo:connect <nom_db>
> db.users.insert({ username: 'frontend-app', role: 'frontend', password: '51407e040228a336a4db37684ce7ee9aee73c457a988b0493cb62930f0dfcf59', salt: '1c66ebc09fcf320a9189215c94bd93d8' })
```
Le nom de la DB est indiqué à la fin de l'url de connexion :

`mongodb://<service_name>:2652096c746158e0fd896ff2b7416877@<service_user>:27017/<nom_db>`

#### Générer un token semi-manuellement

Une route est dédiée à la génération du token

##### Exemple avec CURL

```
curl --location --request POST 'http://<nom_application>.app.etalab.studio/token' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "<nom_utilisateur>",
    "password": "<mot_de_passe>"
}'
```

##### Exemple avec Node.js Request

```
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'http://<nom_application>.app.etalab.studio/token',
  'headers': {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({"username":"frontend","password":"<mot_de_passe>"})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```

### Lancer l'application

Un nouveau schéma a été généré, la branche doit être créée avec ces modifications.

```
git remote add dokku dokku@<ip_serveur>:<nom_application>
git checkout -B deploy
git add src/
git commit -m "generate schema"
git push dokku deploy:master
```

**Remarque** : Sur ma machine, il est nécessaire de d'abord Husky installer en local grâce à la commande :

`npm install husky`

Maintenant que le Backend est déployé, il faut déployer le Frontend.

### Récupérer le projet

```
git clone https://github.com/etalab/radar-tech-frontend.git
cd radar-tech-frontend
git checkout test/deployApp
```

### Ajouter le fichier décrivant les questionnaires

```
cd ..
mv <metier>.json radar-tech-frontend/pages-metiers/<metier>.json
```

### Tester

Ajouter les variables d'environnement dans un fichier `.env.development` à la racine du projet contenant :

```
GATSBY_API_URL=<url_backend>
GATSBY_API_TOKEN=<token_backend>
```

Puis installer les dépendances et lancer l'application en locale

```
sudo npm install -g gatsby-cli
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
npm install
gatsby develop
```

### Créer l'application Dokku (Frontend)

```
dokku apps:create <nom_application>
```

#### Ajouter les variables d'environnement

Le token pour accéder à l'API a été généré en amont. (cf. [Créer un token](#Creer-un-token))

Créer un fichier .env.production et ajouter les variables suivantes :

```
dokku config:set GATSBY_API_URL=<url_backend>
dokku config:set GATSBY_API_TOKEN=<token_backend>
```

### Lancer l'application

**Attention** : Comme on utilise 2 buildpacks, il faut utiliser le .buildpacks à la racine du projet, pour cela on s'assure qu'il n'y ait pas de buildpack set sur Dokku à l'aide de la commande :

`dokku buildpacks:clear <nom_application>`

ou directement se passer du .buildpacks en faisant :

```
dokku buildpacks:add --index 1 radar-tech-front https://github.com/heroku/heroku-buildpack-nodejs.git#v175
dokku buildpacks:add --index 2 radar-tech-front https://github.com/heroku/heroku-buildpack-static.git
```

- Créer une nouvelle branche de déploiement
- Ajouter les nouveaux questionnaires au format JSON
- Forcer l'ajout du fichier de configuration
- Pousser la nouvelle branche sur le dépôt distant Dokku

**Attention** : Il ne faut pas pousser cette branche sur le dépôt d'origine, elle contient le fichier d'environnement

```
git remote add dokku dokku@<ip_serveur>:<nom_application>
git checkout -b deploy
git add pages-metiers/
git add src/pages/resultats.tsx
git commit -m "add metiers"
git push dokku deploy:master
```
