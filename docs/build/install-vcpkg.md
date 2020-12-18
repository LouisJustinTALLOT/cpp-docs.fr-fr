---
title: Installer vcpkg sur Windows, Linux et macOS
description: Découvrez comment installer et mettre à jour vcpkg sur Windows, macOS et Linux.
ms.date: 12/17/2020
ms.topic: reference
ms.technology: cpp-ide
ms.openlocfilehash: aee9561dc94164c08e4d69ec49f60961392c1854
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684245"
---
# <a name="install-vcpkg-on-windows-linux-and-macos"></a>Installer vcpkg sur Windows, Linux et macOS

Vous installez vcpkg en créant un clone local (copie) à partir du référentiel GitHub vcpkg.

## <a name="install-vcpkg"></a>Installer vcpkg

Pour obtenir des instructions spécifiques, choisissez votre plateforme :

### <a name="linux"></a>[Linux](#tab/linux)

Conditions préalables pour Linux :

- [Git](https://git-scm.com/downloads)
- g + + version 6 ou supérieure

#### <a name="to-install-linux-development-tools"></a>Pour installer les outils de développement Linux

Différents distributions Linux peuvent nécessiter l’installation de packages différents. Suivez ces instructions sur Debian, Ubuntu, popOS et d’autres distributions basées sur Debian :

1. Dans une fenêtre d’interpréteur de commandes, exécutez la commande suivante :

   **`sudo apt-get update`**

1. Une fois la mise à jour terminée, exécutez la commande suivante :

   **`sudo apt-get install build-essential tar curl zip unzip`**

Suivez ces instructions sur CentOS :

1. Dans une fenêtre d’interpréteur de commandes, exécutez la commande suivante :

   **`sudo yum install centos-release-scl`**

1. Ensuite, installez et activez les outils de développement en exécutant les commandes suivantes :

   **`sudo yum install devtoolset-7`**

   **`scl enable devtoolset-7 bash`**

Pour toutes les autres distributions, assurez-vous d’installer g + + 6 ou une version ultérieure.

#### <a name="to-copy-and-set-up-vcpkg-on-linux"></a>Pour copier et configurer vcpkg sur Linux

1. Dans une fenêtre d’interpréteur de commandes, créez un répertoire pour votre instance clonée de vcpkg. Si vous envisagez d’installer des bibliothèques pour différentes cibles de build, il est judicieux d’inclure la cible dans le nom du répertoire. Nous vous recommandons d’utiliser des noms de chemin d’accès courts sans espaces, comme *`./x64`* ou *`./iot`* , dans le cas contraire, vous risquez de rencontrer des problèmes de chemin pour certains systèmes de génération de port. Dans la fenêtre de l’interpréteur de commandes, accédez au répertoire que vous venez de faire.

1. Clonez le référentiel vcpkg à partir de GitHub : [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) .

   > **`git clone https://github.com/microsoft/vcpkg`**

   Cette commande crée une copie locale de référentiel dans un *`vcpkg`* sous-répertoire. Cet emplacement est le *répertoire racine* vcpkg pour ce clone de vcpkg.

1. Ensuite, accédez au répertoire racine vcpkg et exécutez la commande de programme d’amorçage vcpkg :

   > **`./bootstrap-vcpkg.sh`**

   Le programme d’amorçage configure vcpkg avec les emplacements du compilateur, les outils et les bibliothèques standard.

### <a name="macos"></a>[macOS](#tab/macos)

Conditions préalables pour macOS :

- outils de développement macOS
- Sur macOS 10,14 ou les versions antérieures, vous aurez également besoin des éléments suivants :
  - Homebrew
  - g + + version 6 ou supérieure

#### <a name="to-install-macos-developer-tools"></a>Pour installer les outils de développement macOS

1. Sur macOS 10,15, exécutez la commande suivante dans Terminal :

   **`xcode-select --install`**

   Ensuite, suivez les invites dans les fenêtres qui s’affichent.

Sur macOS 10,14 et les versions antérieures, vous devez également installer g + + à partir de homebrew. Cette procédure est uniquement nécessaire si vous utilisez une version macOS antérieure à 10,15.

#### <a name="to-install-gcc-for-macos-before-1015"></a>Pour installer GCC pour macOS avant 10,15

1. Pour installer Homebrew, ouvrez terminal, puis exécutez la commande suivante :

   **`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`**

1. Pour installer une version à jour de GCC, exécutez la commande suivante dans Terminal :

   **`brew install gcc`**

#### <a name="to-copy-and-set-up-vcpkg-on-macos"></a>Pour copier et configurer vcpkg sur macOS

1. Dans Terminal, créez un répertoire pour votre instance clonée de vcpkg. Si vous envisagez d’installer des bibliothèques pour différentes cibles de build, il est judicieux d’inclure la cible dans le nom du répertoire. Nous vous recommandons d’utiliser des noms de chemin d’accès courts sans espaces, comme *`./macos`* ou *`./iot`* , dans le cas contraire, vous risquez de rencontrer des problèmes de chemin pour certains systèmes de génération de port. Dans Terminal, accédez au répertoire que vous venez de faire.

1. Clonez le référentiel vcpkg à partir de GitHub : [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) .

   > **`git clone https://github.com/microsoft/vcpkg`**

   Cette commande crée une copie locale de référentiel dans un *`vcpkg`* sous-répertoire. Cet emplacement est le *répertoire racine* vcpkg pour ce clone de vcpkg.

1. Ensuite, accédez au répertoire racine vcpkg et exécutez la commande de programme d’amorçage vcpkg :

   > **`./bootstrap-vcpkg.sh`**

   Le programme d’amorçage configure vcpkg avec les emplacements du compilateur, les outils et les bibliothèques standard.

### <a name="windows"></a>[Windows](#tab/windows)

Configuration requise :

- Windows 7 ou version ultérieure
- [Git pour Windows](https://git-scm.com/downloads)
- [Visual Studio](https://visualstudio.microsoft.com/) 2015 Update 3 ou version ultérieure avec le module linguistique anglais

#### <a name="to-copy-and-set-up-vcpkg-on-windows"></a>Pour copier et configurer vcpkg sur Windows

1. Dans une fenêtre d’invite de commandes, créez un répertoire pour votre instance clonée de vcpkg. Si vous envisagez d’installer des bibliothèques pour différentes cibles de build, il est judicieux d’inclure la cible dans le nom du répertoire. Nous vous recommandons d’utiliser des noms de chemin d’accès courts sans espaces, comme *`C:\src\win32\`* ou *`C:\dev\iot\`* , dans le cas contraire, vous risquez de rencontrer des problèmes de chemin pour certains systèmes de génération de port. Dans la fenêtre commande, accédez au répertoire que vous venez de faire.

1. Clonez le référentiel vcpkg à partir de GitHub : [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) .

   > **`git clone https://github.com/microsoft/vcpkg`**

   Cette commande crée une copie locale de référentiel dans un *`vcpkg`* sous-répertoire. Cet emplacement est le *répertoire racine* vcpkg pour ce clone de vcpkg.

1. Une fois le téléchargement terminé, accédez au *`vcpkg`* répertoire dans la fenêtre d’invite de commandes.

1. Dans le répertoire racine vcpkg, exécutez la commande de programme d’amorçage vcpkg :

   > **`bootstrap-vcpkg.bat`**

   Le programme d’amorçage configure vcpkg avec les emplacements des outils, bibliothèques et SDK Windows Microsoft C/C++.

---

Une fois vcpkg configuré, vous êtes prêt à installer les bibliothèques. Pour plus d’informations, consultez [gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md). vcpkg peut également être intégré à Visual Studio sur Windows, ou avec Visual Studio Code sur n’importe quelle plateforme. Pour plus d’informations, consultez [intégrer vcpkg](integrate-vcpkg.md).

## <a name="update-vcpkg"></a>Mettre à jour vcpkg

Le gestionnaire de package vcpkg est régulièrement mis à jour sur GitHub. Pour mettre à jour votre clone de vcpkg vers la dernière version, à partir du répertoire racine vcpkg, exécutez **`git pull`** . Cette commande synchronise votre copie de vcpkg avec la version sur GitHub. Une fois le téléchargement terminé, réexécutez le programme d’amorçage. Le programme d’amorçage reconstruit le programme vcpkg, mais laisse vos bibliothèques installées sur place.

## <a name="uninstall-vcpkg"></a>Désinstaller vcpkg

Pour désinstaller vcpkg, supprimez simplement le *`vcpkg`* répertoire. La suppression de ce répertoire désinstalle la distribution vcpkg et toutes les bibliothèques installées par vcpkg.

Toutefois, si vous avez exécuté **`vcpkg integrate install`** , vous devez exécuter **`vcpkg integrate remove`** pour vous assurer que l’intégration est nettoyée, avant que le dossier ne soit supprimé. Pour plus d’informations, consultez [intégrer vcpkg](integrate-vcpkg.md).

## <a name="see-also"></a>Voir aussi

[vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS](./vcpkg.md)\
[vcpkg sur GitHub](https://github.com/Microsoft/vcpkg)\
[Intégrer vcpkg](integrate-vcpkg.md)\
[Gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md)\
[informations de référence sur la ligne de commande vcpkg](vcpkg-command-line-reference.md)\
[Démarrage rapide](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[Forum aux questions](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
