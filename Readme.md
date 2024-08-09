
# Projet de Test - Serveur de Chat Multiclient avec Boost.Beast

Ce projet est un exemple de serveur de chat multiclient développé en C++ utilisant la bibliothèque `Boost.Beast`. L'objectif de ce projet est de comprendre comment fonctionne `Boost.Beast` pour gérer les connexions WebSocket, les échanges de messages, et la gestion de multiples clients.

## Installation des Dépendances

Ce projet utilise `Boost.Beast`, qui fait partie de la bibliothèque `Boost`. Pour gérer les dépendances, nous avons utilisé `vcpkg`, un gestionnaire de paquets pour C++.

### Étapes d'installation avec `vcpkg`

1. **Installer `vcpkg`** (si ce n'est pas déjà fait) :

    ```bash
    git clone https://github.com/microsoft/vcpkg.git
    cd vcpkg
    ./bootstrap-vcpkg.sh  # Sur Linux/Mac
    .ootstrap-vcpkg.bat  # Sur Windows
    ```

2. **Installer Boost.Beast** via `vcpkg` :

    ```bash
    ./vcpkg install boost-beast
    ```

3. **Configurer votre projet CMake pour utiliser `vcpkg`** :

    Dans votre fichier `CMakeLists.txt`, ajoutez la ligne suivante pour indiquer à CMake d'utiliser `vcpkg` :

    ```cmake
    set(CMAKE_TOOLCHAIN_FILE "${CMAKE_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake")
    ```

## Compilation du Projet

Pour compiler le projet, suivez les étapes suivantes :

1. **Cloner le projet** ou copier les fichiers sources sur votre machine.
2. **Créer un répertoire de build** :

    ```bash
    mkdir build
    cd build
    ```

3. **Exécuter CMake** pour configurer le projet :

    ```bash
    cmake ..
    ```

4. **Compiler le projet** :

    ```bash
    make
    ```

## Exécution du Serveur

Pour démarrer le serveur de chat multiclient, utilisez la ligne de commande suivante :

```bash
./beastChatServer <address> <port> <doc_root> <threads>
```

### Paramètres

- `<address>` : Adresse IP à laquelle le serveur doit être lié (par exemple, `0.0.0.0` pour écouter sur toutes les interfaces).
- `<port>` : Port sur lequel le serveur écoutera (par exemple, `8080`).
- `<doc_root>` : Répertoire racine des documents (utilisé pour servir des fichiers statiques, par exemple `.` pour le répertoire courant).
- `<threads>` : Nombre de threads à utiliser pour gérer les connexions.

### Exemple d'utilisation

```bash
./beastChatServer 0.0.0.0 8080 . 5
```

Cette commande démarre le serveur sur toutes les interfaces réseau (`0.0.0.0`), écoute sur le port `8080`, sert les fichiers du répertoire courant, et utilise 5 threads pour gérer les connexions.

## Test du Serveur de Chat

Pour tester le serveur de chat, vous pouvez ouvrir plusieurs navigateurs et les connecter à l'URL suivante :

```
http://127.0.0.1:8080/chat_client.html
```

### Étapes pour le Test

1. **Démarrer le serveur** en utilisant la commande ci-dessus.
2. **Ouvrir un navigateur web** (comme Chrome, Firefox, etc.).
3. **Naviguer vers l'URL** `http://127.0.0.1:8080/chat_client.html`.
4. **Ouvrir plusieurs onglets ou fenêtres de navigateurs** avec la même URL pour simuler plusieurs clients.
5. **Envoyer des messages** depuis différents navigateurs. Vous devriez voir les messages apparaître dans tous les navigateurs connectés, ce qui simule un chat en temps réel entre plusieurs clients.

### Remarque

Le fichier `chat_client.html` doit être placé dans le répertoire spécifié par `<doc_root>` lorsque vous avez démarré le serveur. Ce fichier HTML contient le code nécessaire pour établir une connexion WebSocket avec le serveur et permettre l'envoi et la réception de messages.

## Conclusion

Ce projet est un exemple simple qui montre comment utiliser `Boost.Beast` pour créer un serveur de chat multiclient en C++. Il est conçu pour vous aider à comprendre les concepts de base et à explorer les fonctionnalités offertes par `Boost.Beast`. N'hésitez pas à expérimenter et à étendre ce projet pour en apprendre davantage.

## Ressources

- [Documentation de Boost.Beast](https://www.boost.org/doc/libs/release/libs/beast/doc/html/index.html)
- [vcpkg GitHub](https://github.com/microsoft/vcpkg)
