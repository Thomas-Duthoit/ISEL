# <span style='color: #0f2;'>**ig2i@isel**</span>:<span style='color: #4DA6FF; font-family: Monospace'>- $ ISEL/TP2</span>
[**Accès au Repository d'ISEL**](https://github.com/Thomas-Duthoit/ISEL)
### **Identification utilisateur:**
```
id
> renvoie l'uid, le gid, et les groupes auxquels on appartient  ->  renvoie l'identité courrante
```

- UID: **`User Identifier`** = Numéro qui identifie un utilisateur.
<br>
- Les utilisateurs sont organisés en groupes => Chaque groupe possède un GID **`(Group Identifier)`**

***

>`/etc/passwd` contient les mots de passe de tout les utilisateurs:

=> Structure classique en colonnes: 
- nom_du_compte
- mot_de_passe*
- numero_utilisateur
- numero_de_groupe
- commentaires*
- répertoire_personnel
- commande*

> `/etc/group`: contient la liste des utilisateurs appartenant aux différents groupes

Un nom d'utilisateur peut apparaitre dans plusieurs groupes
<br>
On peut changer de groupe avec la commande <span style='color: #0f0;'>newgrp</span>

***

### **3 permissions * 3 classes**

**Fichiers:**
<br>
3 permissions: rwx:
- r: droit de lecture du fichier
- w: droit d'écriture du fichier
- x: droit d'éxécution du fichier

**Répertoires:**
<br>
les clés rwx perdent leur signification habituelle:
- r: droit de lecture: listage (ls)
- w: droit décriture (rm, rmdir, mkdir, touch)
- x: droit de traversée (cd)

***

### **Algorithme des droits d'accès:**

Un processus lancé par un utilisateur **(UID, GID)** est caractérisé par des identifiants effectifs: **EUID** et **EGID**.
<br>
Le plus souvent, **EUID**=**UID** et **EGID**=**GID**

***

### **Chaque fichier est caractérisé par:**
- le propriéataire du fichier: **FUID**
- Le groupe de fichier: **FGID**
- Ses permissions d'accès pour les classes **user**, **group**, **other**
> Utiliser <span style='color: #0f0;'>ls -l</span> pour voir les infos

***

### **Modification des permissions: <span style='color: #0f0;'>chmod</span>**

- Mode absolu: <span style='color: #0f0;'>chmod \<permissions en octal> <fichiers à modifier></span>

- Mode symbolique: <span style='color: #0f0;'>chmod \<liste des permissions>* <fichiers à modifier></span>

\*séparés par une virgule et sans espace blancs

#### <ins>Mode absolu</ins>:

permissions d'accès:
- r=4
- w=2
- x=1
- 0=aucuns droits

#### <ins>Mode symbolique</ins>:
chaque permissions s'exprime par **[ugoa][+-=][rwxst]**
- u = user
- o = other
- a = all
- g = groupe

<span style='color: #0f0;'>umask \<mask></span> : masque de création des fichiers (inverse de nos permissions)
<br>
La valeur de umask est exprimée en base octale:

> "umask 066: sécurité et souplesse"

***

<span style='color: #0f0;'>newgrp</span>: permet à l'utilisateur de changer de groupe principal
<br>
<span style='color: #0f0;'>chown</span>: permet de changer le propriétaire du fichier
<br>
<span style='color: #0f0;'>chgrp</span>: permet de changer le groupe du fichier

***

> **Utilité du groupe principal par rapport aux groupes secondaires:** Quand on crée un fichier, il appartiendra par défaut à notre groupe principal

***

><span style='color: #0f0;'>adduser user</span> : ajouter user
<br>
<span style='color: #0f0;'>addgroup group</span> : ajouter le groupe group
<br>
<span style='color: #0f0;'>passwd user</span> : change le mdp de user 
<br>
<span style='color: #0f0;'>deluser user</span> : supprime l'utilisateur user
<br>
<span style='color: #0f0;'>delgroup group</span> : supprime le groupe groupe

***

