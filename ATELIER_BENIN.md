# Atelier collecte — Cour des comptes du Bénin

## Fonctionnement
16 questions, choix des organismes issus du registre Excel transmis le 6 octobre 2026, accès enquêteur et accès superviseur distincts. Le tableau de bord relit la base toutes les 10 secondes lorsque la page reste ouverte. Le formulaire fonctionne en ligne ; aucun mode hors connexion n’est prévu.

## Mise en service durable
1. Disposer d’une base PostgreSQL dédiée à l’atelier.
2. Installer les dépendances : python -m pip install -r requirements.txt
3. Configurer les secrets dans Streamlit Community Cloud, dans les paramètres de l’application. Ne jamais publier les secrets dans GitHub.
4. Déployer le fichier streamlit_app.py depuis ce dépôt.
5. Effectuer un entretien test depuis un téléphone, puis vérifier sa réception dans la supervision.

Secrets nécessaires (valeurs à remplacer ; ne pas publier ces valeurs réelles) :
```toml
DATABASE_URL = "CONNEXION_POSTGRESQL_AVEC_TLS"
COLLECTOR_PASSWORD = "CODE_ENQUETEUR_A_CHOISIR"
SUPERVISOR_PASSWORD = "CODE_SUPERVISEUR_DIFFERENT_A_CHOISIR"
CAMPAIGN_ID = "ATELIER-BENIN-2026-10-07"
```

Pour un exercice provisoire sur Codespaces seulement : omettre DATABASE_URL et utiliser STORAGE_MODE = "codespaces_atelier". Les réponses seront dans la machine Codespaces ; les exporter avant sa suppression. Ne pas utiliser ce mode pour la conservation sur Community Cloud.

## Usage en classe
Partager le lien et le code enquêteur. Réserver le code superviseur au formateur. Les participants choisissent l’organisme et un identifiant E01 à E14, répondent et enregistrent. Après confirmation, cliquer sur Commencer un nouvel entretien. Les réponses sont datées automatiquement en UTC et séparées par campagne. Un double envoi du même formulaire conserve le même reçu et ne crée pas deux lignes. Plusieurs entretiens sur le même organisme sont signalés au superviseur pour vérification.

## Limites et interprétation
Le registre comporte 262 fiches de référence, dont des organismes historiques à actualiser. Leur assujettissement et le N de campagne doivent être validés par la Cour. Aucun taux de couverture ni score de conformité n’est inventé. Les entretiens de formation doivent être distingués des enquêtes officielles. Ne pas saisir de nom personnel, de dossier confidentiel ou de constat sensible dans cet atelier. Les codes partagés servent au prototype pédagogique ; une utilisation institutionnelle exige une authentification individuelle et des droits gérés par la Cour.

## Fichiers
- enquete_benin.py : questionnaire, stockage et supervision.
- streamlit_app.py : lancement de cette application.
- app_gdp_original.py : copie conservée du modèle GDP initial.

## Validation effectuée
Tests : lancement, accès enquêteur, sélection d’un organisme réel, enregistrement, double envoi, séparation des campagnes, supervision et génération Excel. Le stockage PostgreSQL externe et la publication ne sont pas encore validés tant que la connexion n’est pas configurée.
