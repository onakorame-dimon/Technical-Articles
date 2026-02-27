# VAGRANT CHEATSHEET 


## 📦 Vagrant Box Management

| Command                 | Purpose                                      |
| ----------------------- | -------------------------------------------- |
| `vagrant box add`       | Adds a box to your local box repository      |
| `vagrant box list`      | Lists all boxes in your local box repository |
| `vagrant box outdated`  | Checks if boxes are outdated                 |
| `vagrant box update`    | Updates a box to a new version               |
| `vagrant box repackage` | Repackages a box with new name and metadata  |
| `vagrant box prune`     | Removes outdated boxes                       |
| `vagrant box remove`    | Removes a box from local repository          |

---

## 📁 Location of VM Boxes

| OS               | Path                                 |
| ---------------- | ------------------------------------ |
| Mac OS X / Linux | `~/.vagrant.d/boxes`                 |
| Windows          | `C:/Users/USERNAME/.vagrant.d/boxes` |

---

## 🚀 Core Vagrant Commands

| Command              | Purpose                                  |
| -------------------- | ---------------------------------------- |
| `vagrant init`       | Initializes a new Vagrant environment    |
| `vagrant up`         | Creates and configures the guest machine |
| `vagrant ssh`        | Logs into the guest machine via SSH      |
| `vagrant ssh-config` | Outputs SSH configuration for the VM     |

---

## 🔄 Life Cycle Management

| Command           | Purpose                                    |
| ----------------- | ------------------------------------------ |
| `vagrant halt`    | Gracefully stops the guest machine         |
| `vagrant suspend` | Suspends the machine without shutting down |
| `vagrant resume`  | Resumes a suspended machine                |
| `vagrant reload`  | Restarts the guest machine                 |
| `vagrant destroy` | Stops and deletes the VM and its data      |

---

## ℹ️ Information & Utilities

| Command                    | Purpose                              |
| -------------------------- | ------------------------------------ |
| `vagrant status`           | Shows status of current environment  |
| `vagrant global-status`    | Shows status of all Vagrant machines |
| `vagrant package`          | Packages a VM into a reusable box    |
| `vagrant provision`        | Runs configured provisioners         |
| `vagrant plugin install`   | Installs a plugin                    |
| `vagrant plugin list`      | Lists installed plugins              |
| `vagrant plugin uninstall` | Uninstalls a plugin                  |
