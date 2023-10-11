# Installation matérielle (recommandé)

## Pré-requis

::: tip Installation recommandée

Cette installation est fortement recommandée car plus adaptée à la philosophie du projet.

:::

- Mémoire vive (RAM) : **8GB.** 
- Processeur (CPU) : **N'importe quel modèle AMD ou Intel 64-bit architecture amd64 (4 cœurs physiques ou plus recommandés)**.
- Stockage : **60GB** minimum, **100GB** ou plus recommandés.
- Cartes réseaux (NIC) : **4 cartes réseaux** (peu importe le type de carte).

## Récupération des fichiers

Vous pouvez récupérer les fichiers sources du projet sur GitHub en HTTPS :

```sh
git clone https://github.com/Rulio974/OpenDiode
```

Ou en téléchargement directement les fichiers :

<a href="https://github.com/Rulio974/OpenDiode/archive/refs/heads/main.zip" download class="download-button">Télécharger les fichiers</a>


## Installation du système


L’installation d’OpenDiode s’effectue sur un système linux Mageia.

Vous pouvez récupérer une image ISO depuis : https://www.mageia.org/fr/downloads/get/?q=Mageia-8-x86_64.iso

::: details Monter une image ISO


_Graver l’image sur un support amovible (type CD, DVD ou Clé USB)._

_Depuis une machine Windows, vous pouvez utiliser le logiciel Rufus_ : 
https://rufus.ie/fr/ 

_Depuis une machine Linux, vous pouvez utiliser le logiciel Isodumper_ : 
https://wiki.mageia.org/en/IsoDumper_:_%C3%A9crire_une_image_ISO_sur_une_clef_USB-fr


:::

//details de l'install

## Installation de OpenDiode

### Copie des fichiers

**1. Se connecter en tant que *root* sur le système .** 

**2. Brancher la clé USB contenant les fichiers d'OpenDiode.**

**3. Repérer l’emplacement de la clé avec la commande suivante :** 

```sh
fdisk -l
```

::: tip Résulat

Pour nous, l'emplacement est :
```
/dev/sdb1/
```
:::

**4. Créer un dossier dans lequel monter la clé USB :**

```sh
mkdir /mnt/usb
```

**5. Monter la clé USB :**

```sh
mount /dev/sdb1/usb /mnt/usb
```

**6. Copier les fichiers de la clé USB vers “/home/opendiode” :**

```sh
cp /mnt/usb/opendiode/* /home/opendiode
```

**7. Ejectez la clé USB :**

```sh
umount /mnt/usb
```

### Installation de la diode

1. Vérifiez les cartes réseaux.

```sh
ip a
```

::: tip NIC

Vous devez comme indiqué précédemment posséder 4 cartes réseaux.

:::

2. Se déplacer dans le dossier d'installation :


```sh
cd /home/opendiode/
```

3. Lancez le script d'installation. Le format est le suivant :

```sh
./install.sh <internet_nic> <input_nic> <output_nic> <admin_nic>
```

Dans notre cas, cela donne :

```sh
./install.sh enp0s3 enp0s8 enp0s9 enp0s10
```

::: tip Logs

Il est possible de visualiser les logs d’installation en temps réel en ouvrant un second terminal avec le raccourci clavier Alt+F2 puis en exécutant la commande suivante :

```sh
tail -f /var/log/opendiode/install.log
```
:::