# Correction Exercice 1 : Hello world

Comme le veut la tradition tacite des dev : Toute nouveauté commence par un hello world !

Votre objectif sera donc de créer un workflow qui va démarrer un serveur Ubuntu, et afficher "Hello world !"

## Correction

1. Ajouter un fichier "hello-world.yml" dans le répertoire "workflows"

2. Insérez le code suivant dans le fichier "hello-world.yml"

```YAML
name: Hello World

on: push

jobs:
  hello_world_job:

    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Say Hello World !
        run: echo "Hello World !"
```
