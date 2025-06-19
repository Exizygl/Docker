# 🐳 Docker - Gestion des Conteneurs

## ✅ Comprendre le cycle de vie d’un conteneur

Un conteneur Docker passe par plusieurs états :
- **Création** : à partir d’une image (`docker create` ou `docker run`)
- **Démarrage** : le conteneur passe en "exécution" (`docker start`)
- **Arrêt** : le conteneur s'arrête (`docker stop` ou `docker kill`)
- **Reprise** : un conteneur arrêté peut être relancé (`docker start`)
- **Suppression** : suppression définitive (`docker rm`)

---

## ✅ Maîtriser les commandes de base

### 🔹 `docker run`
Lancer un conteneur depuis une image :
```bash
docker run -d -p 8080:80 nginx
```
- `-d` : exécution en arrière-plan (détaché)
- `-p` : mapping de ports entre l'hôte et le conteneur

### 🔹 `docker start` / `docker stop`
- Démarrer un conteneur arrêté :
  ```bash
  docker start [nom ou ID]
  ```
- Arrêter un conteneur en cours :
  ```bash
  docker stop [nom ou ID]
  ```

### 🔹 `docker ps`
Lister les conteneurs :
```bash
docker ps      # Conteneurs en cours
docker ps -a   # Tous les conteneurs (actifs + arrêtés)
```

### 🔹 `docker logs`
Voir les logs (sortie standard) du conteneur :
```bash
docker logs [nom ou ID]
```

### 🔹 `docker exec`
Exécuter une commande à l’intérieur du conteneur :
```bash
docker exec -it [nom ou ID] bash
```
- `-it` : mode interactif + terminal
- `bash` : lance un shell Bash (si disponible dans le conteneur)

---

## ✅ Comprendre le mapping des ports

### 🔁 Qu’est-ce que le port mapping ?
Le mapping de ports permet d’exposer un port du conteneur sur un port de la machine hôte.

### 📌 Syntaxe :
```bash
docker run -p [port_hôte]:[port_conteneur] image
```
- `port_hôte` : port accessible sur ta machine
- `port_conteneur` : port utilisé à l'intérieur du conteneur

### 🧪 Exemple :
```bash
docker run -d -p 8080:80 nginx
```
- Nginx écoute sur le port 80 dans le conteneur.
- Accessible sur ta machine via `http://localhost:8080`.

### ⚠️ Attention :
- Un port hôte ne peut pas être utilisé par plusieurs conteneurs en même temps.

### 🔎 Vérifier le mapping :
```bash
docker ps
```
Colonne `PORTS` :
```
0.0.0.0:8080->80/tcp
```

---
