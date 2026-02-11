# Correction Exercice 3 : Trigger Event

- Créer un workflow qui se délenche lorsqu'une issue est crée

```YAML
name: Nouvelle Issue

on:
  issues:
    types: [opened]

jobs:
  new_issue:
    runs-on: ubuntu-latest
    steps:
      - name: validation
        run: echo "Issue créée"
```

---

- Créer un worflow qui se lance lorsqu'une PR est merged

```YAML
name: Merged PR

on:
  pull_request:
    types:
      - closed

jobs:
  if_merge:
    runs-on: ubuntu-latest
    if: ${{github.event.pull_request.merged == true}}
    steps:
      - name: Merged
        run: echo "PR merged avec succès"
```

---

- Créer un workflow qui s'exécute lorsque le précédent a été utilisé

```YAML
name: "Workflow Suivant"

on:
  workflow_run:
    workflows: [Merged PR]
    types: [completed]

jobs:
  next_workflow:
    runs-on: ubuntu-latest
    steps:
      - name: "Validation du WF suivant"
        run : echo "Workflow éxécuté"
```

---

- Créez un workflow contenant deux jobs. Le premier devra être lancé manuellement tandis que le second sera exécuté une fois le précédent terminé.

```YAML
name : Workflow Needs

on: workflow_dispatch

jobs:
  job_first:
    runs-on: ubuntu-latest
    steps:
      - name: "1er job"
        run: echo "1er job ok"
  second_job:
    runs-on: ubuntu-latest
    needs: [job_first]
    steps:
      - name: "2eme job"
        run: echo "2eme job ok"
```
