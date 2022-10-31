# Ansible Role IntelliJ IDEA
This is an Ansible role that installs IntelliJ IDEA on Linux. It uses the tarball from the official website so this role is not dependent on any package manager.  
It can take a list of plugin IDs which it will automatically install.  

Tested on Fedora 36 with IntelliJ 2022.3, should work on any Linux distribution that the IntelliJ IDEA tarball supports.  

## Requirements

### Base requirements
None  

### Installing plugins
Plugins are installer per-user, so you will need to give `intellij_idea_user`, this defaults to `{{ ansible_user_id }}`.  

## Variables
| Variable | Default | Description |
|----------|---------|-------------|
| `intellij_idea_edition` | `IC` | Default version of IntelliJ IDEA to download. Valid options are: `[IC, UC]` |
| `intellij_idea_version` | `2022.2.3` | Default version of IntelliJ IDEA to download |
| `intellij_idea_url` | See [defaults/main.yml](./defaults/main.yml) | Base URL for the IntelliJ IDEA tarball |
| `intellij_idea_user` | `{{ ansible_user_id }}` | User to install plugins for. |

## Installing plugins
To install plugins for IntelliJ IDEA, define the `intellij_idea_plugins` variable.  
```yaml
intellij_idea_plugins:
  - 10233 # Discord Integration
  - 17718 # GitHub Copilot
```

You can get this ID by going to the plugin homepage from IntelliJ IDEA's Plugins tab and copying the number from the URL it opens.  