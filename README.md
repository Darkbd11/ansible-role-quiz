# ansible-role-BoulayeLeBg

Rôle Ansible pour déployer l'application Node.js **quiz-ansible** depuis GitLab, sur tout système Linux conteneurisé de type **Debian/Ubuntu** ou **RedHat/Rocky Linux**.

## Prérequis

- Ansible >= 2.12
- Accès Internet sur les machines cibles (pour télécharger Node.js et cloner le dépôt)
- Privilèges `root` ou `sudo` sur les machines cibles

## Compatibilité

| Distribution      | Versions            |
|-------------------|---------------------|
| Ubuntu            | 20.04, 22.04, 24.04 |
| Debian            | 11 (Bullseye), 12 (Bookworm) |
| Rocky Linux / RHEL | 8, 9               |

## Variables

### Defaults (surchargeables)

| Variable                       | Valeur par défaut                                          | Description                        |
|--------------------------------|------------------------------------------------------------|------------------------------------|
| `quiz_repo`                    | `https://gitlab.com/ftutorials-labs/quiz-ansible.git`     | URL du dépôt Git                   |
| `quiz_repo_branch`             | `main`                                                     | Branche à cloner                   |
| `quiz_app_dir`                 | `/opt/quiz-ansible`                                        | Répertoire d'installation          |
| `quiz_app_port`                | `3000`                                                     | Port d'écoute de l'application     |
| `quiz_node_setup_url_debian`   | `https://deb.nodesource.com/setup_20.x`                   | URL setup Node.js (Debian/Ubuntu)  |
| `quiz_node_setup_url_redhat`   | `https://rpm.nodesource.com/setup_20.x`                   | URL setup Node.js (RedHat/Rocky)   |

## Utilisation

```yaml
- name: Deploiement de quiz-ansible
  hosts: all
  become: true
  roles:
    - ansible-role-BoulayeLeBg
```

## Structure du rôle

```
ansible-role-BoulayeLeBg/
├── defaults/
│   └── main.yaml       # Variables par défaut
├── handlers/
│   └── main.yaml       # Handlers
├── meta/
│   └── main.yaml       # Métadonnées Galaxy
├── tasks/
│   ├── main.yaml       # Point d'entrée
│   ├── debian.yaml     # Tâches Debian/Ubuntu
│   └── redhat.yaml     # Tâches RedHat/Rocky
├── vars/
│   └── main.yaml       # Variables internes
└── README.md
```

## Auteur

**BoulayeLeBg** - Exercice 32 Ansible
