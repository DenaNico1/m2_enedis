# 🌿 GreenTech Solutions - Dashboard Énergétique

Application Streamlit d'analyse des données énergétiques ADEME et Enedis.

## 📋 Prérequis

- Docker Desktop installé
- Docker Compose
- 4 GB RAM minimum

## 🚀 Installation rapide

### Option 1 : Avec Docker (Recommandé)

```bash
# 1. Cloner le projet
git clone https://github.com/votre-username/greentech-project.git
cd greentech-project

# 2. Démarrer l'application
docker-compose up -d streamlit

# 3. Accéder à l'application
# Streamlit : http://localhost:8502
# API : http://localhost:8000 (optionnel)
```

### Option 2 : Sans Docker (Local)

```bash
# 1. Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Linux/Mac
# .\venv\Scripts\activate  # Windows

# 2. Installer les dépendances
pip install -r requirements.txt

# 3. Lancer Streamlit
streamlit run app.py
```

## 📁 Structure du projet

```
greentech-project/
├── app.py                 # Application principale
├── pages/                 # Pages Streamlit
│   ├── analysis.py       # Analyses ADEME
│   ├── enedis.py         # Analyses Enedis
│   └── about.py          # À propos
├── data/                  # Données CSV
├── models/                # Modèles ML
├── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

## 🛠️ Commandes utiles

### Avec Make

```bash
make build          # Construire les images
make streamlit      # Démarrer Streamlit
make logs           # Voir les logs
make down           # Tout arrêter
make clean          # Nettoyer
```

### Avec Docker Compose

```bash
docker-compose up -d streamlit       # Démarrer
docker-compose logs -f streamlit     # Logs en temps réel
docker-compose restart streamlit     # Redémarrer
docker-compose down                  # Arrêter
```

## 🔧 Développement

### Mode hot-reload

Décommentez dans `docker-compose.yml` :

```yaml
volumes:
  - ./pages:/app/pages
  - ./app.py:/app/app.py
```

Les modifications seront prises en compte automatiquement !

### Reconstruire après modifications

```bash
docker-compose up -d --build streamlit
```

## 📊 Accès aux services

| Service   | URL                        | Description          |
| --------- | -------------------------- | -------------------- |
| Streamlit | http://localhost:8502      | Interface principale |
| API       | http://localhost:8000      | API REST (optionnel) |
| Swagger   | http://localhost:8000/docs | Documentation API    |

## 🐛 Résolution de problèmes

### Port déjà utilisé

```bash
# Changer le port dans docker-compose.yml
ports:
  - "8503:8501"  # Utiliser 8503
```

### Logs pour déboguer

```bash
docker-compose logs -f streamlit
```

### Redémarrage complet

```bash
docker-compose down -v
docker-compose build --no-cache
docker-compose up -d streamlit
```

## 📦 Données requises

Placez vos fichiers CSV dans le dossier `data/` :

- `donnees_ademe_finales_nettoyees_69_final_pret.csv`
- `donnees_enedis_finales_69.csv`

## 👥 Contribution

1. Fork le projet
2. Créer une branche (`git checkout -b feature/amelioration`)
3. Commit (`git commit -m 'Ajout fonctionnalité'`)
4. Push (`git push origin feature/amelioration`)
5. Ouvrir une Pull Request

## 📝 License

MIT License

## 👨‍💻 Auteur

Modou Mboup - M2 Projet Énergétique 2025

---

**Note** : Pour toute question, ouvrir une issue sur GitHub.
