---
title: 'vcpkg : un gestionnaire de forfaitS CMD pour Windows, Linux et MacOS'
description: vcpkg est un gestionnaire de paquets de ligne de commande qui simplifie grandement l’acquisition et l’installation de bibliothèques en source open C sur Windows, MacOS et Linux.
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 9dbeba1f55164ace01fb8bb26155dd9319ba62db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335409"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg : un gestionnaire de forfaitS CMD pour Windows, Linux et MacOS

vcpkg est un gestionnaire de paquets de ligne de commande pour le C. Il simplifie grandement l’acquisition et l’installation de bibliothèques tierces sur Windows, Linux et MacOS. Si votre projet utilise des bibliothèques tierces, nous vous recommandons d’utiliser vcpkg pour les installer. vcpkg prend en charge les bibliothèques open source et propriétaires. La compatibilité de toutes les bibliothèques du catalogue Windows vcpkg a été testée avec Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019. Entre les catalogues Windows et Linux/MacOS, vcpkg prend désormais en charge plus de 1900 bibliothèques. La communauté C++ ajoute régulièrement de nouvelles bibliothèques dans les deux catalogues.

## <a name="simple-yet-flexible"></a>Simple et pourtant flexible

À l’aide d’une commande unique, vous pouvez télécharger des sources et constituer une bibliothèque. vcpkg lui-même est un projet open source, disponible sur GitHub. Il est possible de personnaliser vos clones privés vcpkg de la façon que vous voulez. Par exemple, spécifiez différentes bibliothèques ou différentes versions des bibliothèques que celle que l’on trouve dans le catalogue public. Vous pouvez avoir plusieurs clones de vcpkg sur une seule machine. Chacun peut être configuré pour produire une collection personnalisée de bibliothèques, avec vos commutateurs de compilation préférés. Chaque clone est un environnement autonome avec son propre exemplaire de vcpkg.exe qui ne fonctionne que sur sa propre hiérarchie. vcpkg n’est pas ajouté à des variables d’environnement, et n’a aucune dépendance sur le registre Windows ou Visual Studio.

## <a name="sources-not-binaries"></a>Sources, et non binaires

Pour les bibliothèques du catalogue Windows, vcpkg télécharge des sources au lieu de binaires<sup>1</sup>. Il compile ces sources à l’aide de la version la plus récente de Visual Studio qu’il trouve. Dans le C, il est important que votre code d’application et toutes les bibliothèques que vous utilisez soient compilés par le même compilateur et la même version compilateur. En utilisant vcpkg, vous éliminez ou au moins réduisez considérablement les risques de binaires incompatibles et les problèmes qu’ils peuvent engendrer. Dans les équipes qui sont standardisées sur une version spécifique d’un compilateur, un membre de l’équipe peut utiliser des vcpkg pour télécharger des sources et compiler un ensemble de binaires. Ensuite, ils peuvent utiliser la commande d’exportation pour zip jusqu’à les binaires et les en-têtes pour les autres membres de l’équipe. Pour plus d’informations, consultez [Exporter les fichiers binaires et les en-têtes compilés](#export_binaries_per_project).

Vous pouvez également créer un clone vcpkg qui a des bibliothèques privées dans la collection de ports. Ajoutez un port qui télécharge vos binaires préconstruis et en-têtes. Ensuite, écrivez un fichier portfile.cmake qui copie simplement ces fichiers à l’endroit préféré.

<sup>1</sup> *Note : les sources ne sont pas disponibles pour certaines bibliothèques propriétaires. Dans ces cas, vcpkg télécharge des binaires préconstruis compatibles.*

## <a name="installation"></a>Installation

Clonez le répo vcpkg [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg)de GitHub: . Vous pouvez télécharger vers n’importe quel emplacement de dossier de votre choix.

Exécutez le programme d’amorçage dans le dossier racine :

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Recherche dans la liste des bibliothèques disponibles

Pour afficher les packages qui sont disponibles, à l’invite de commandes, tapez : **vcpkg search**

Cette commande énumère les fichiers de contrôle dans les sous-dossiers vcpkg/ports. Vous verrez une liste comme celle-ci:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Vous pouvez filtrer sur un modèle, par exemple **vcpkg search ta** :

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Installer une bibliothèque sur votre ordinateur local

Après avoir obtenu le nom d’une bibliothèque à l’aide de **vcpkg search**, vous utilisez **vcpkg install** pour télécharger la bibliothèque et la compiler. vcpkg utilise le portfile de la bibliothèque dans le répertoire des ports. Si aucun triplet n’est spécifié, vcpkg installe et compile pour le triplet par défaut pour la plateforme cible : x86-windows, x64-linux.cmake ou x64-osx.cmake.

Pour les bibliothèques Linux, vcpkg dépend de l’installation de gcc sur l’ordinateur local. Sur MacOS, vcpkg utilise Clang.

Lorsque le portfile spécifie les dépendances, vcpkg les télécharge et les installe aussi. Après le téléchargement, vcpkg construit la bibliothèque en utilisant le même système de construction que la bibliothèque utilise. Les projets CMake et (sur Windows) MSBuild sont préférés, mais MAKE est pris en charge, ainsi que tout autre système de construction. Si vcpkg ne peut pas trouver le système de construction spécifié sur la machine locale, il télécharge et l’installe.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Pour les projets CMAKE, utilisez CMAKE_TOOLCHAIN_FILE afin de rendre les bibliothèques accessibles avec `find_package()`. Par exemple :

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Répertorier les bibliothèques déjà installées

Une fois que vous avez installé certaines bibliothèques, vous pouvez utiliser **la liste des vcpkg** pour voir ce que vous avez :

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Intégrer avec Visual Studio (Windows)

### <a name="per-user"></a>Par utilisateur

Exécuter **vcpkg intégrer installer** pour configurer Visual Studio pour localiser tous les fichiers d’en-tête vcpkg et binaires sur une base par utilisateur. Il n’est pas nécessaire d’éditer manuellement les chemins des annuaires VCMD. Si vous avez plusieurs clones, le clone que vous exécutez cette commande devient le nouvel emplacement par défaut.

Maintenant, vous pouvez #include en-têtes simplement en tapant le dossier / en-tête, et autocomplete vous aide. Aucune étape supplémentaire n’est nécessaire pour la liaison à des bibliothèques, ou pour l’ajout de références de projet. L’illustration suivante montre comment Visual Studio recherche les en-têtes azure-storage-cpp. vcpkg place ses en-têtes dans le sous-dossier **/installed**, partitionné par la plateforme cible. Le diagramme suivant présente la liste des fichiers include dans le sous-dossier **/was** pour la bibliothèque :

![vcpkg et IntelliSense](media/vcpkg-intellisense.png "vcpkg et IntelliSense")

### <a name="per-project"></a>Par projet

Si vous avez besoin d’utiliser une version spécifique d’une bibliothèque différente de la version dans votre instance active vcpkg, suivez ces étapes:

1. Créez un clone de vcpkg.
1. Modifiez le portfile de la bibliothèque pour obtenir la version dont vous avez besoin.
1. Exécutez **vcpkg install \<bibliothèque>**.
1. Utilisez **vcpkg integrate project** pour créer un package NuGet qui référence cette bibliothèque en fonction du projet.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Intégrer avec Visual Studio Code (Linux/MacOS)

Exécuter **vcpkg intégrer installer** pour configurer Visual Studio Code sur Linux/ MacOS. Cette commande définit l’emplacement de l’enrôlement vcpkg et permet IntelliSense sur les fichiers source.

## <a name="target-linux-from-windows-via-wsl"></a>Cibler Linux à partir de Windows par le biais de WSL

Vous pouvez produire des binaires Linux sur une machine Windows en utilisant le sous-système Windows pour Linux, ou WSL. Suivez les instructions pour [configurer WSL sur Windows 10](/windows/wsl/install-win10), puis configurez-le avec [l’extension Visual Studio pour Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Il est acceptable de mettre toutes vos bibliothèques construites pour Windows et Linux dans le même dossier. Ils sont accessibles à partir de Windows et WSL.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> Exporter les fichiers binaires et les en-têtes compilés

Il est inefficace de faire télécharger et construire des bibliothèques communes à tout le monde dans une équipe. Un seul membre de l’équipe peut utiliser la commande **d’exportation de vcpkg** pour créer un fichier zip commun des binaires et des en-têtes, ou un paquet NuGet. Ensuite, il est facile de le partager avec d’autres membres de l’équipe.

## <a name="updateupgrade-installed-libraries"></a>Mettre à jour ou à niveau les bibliothèques installées

Le catalogue public est tenu au courant des dernières versions des bibliothèques. Pour déterminer lesquelles de vos bibliothèques locales sont obsolètes, utilisez **vcpkg update**. Lorsque vous êtes prêt à mettre à jour votre collection de ports à la dernière version du catalogue public, exécutez la commande **de mise à niveau vcpkg.** Il télécharge et reconstruit automatiquement l’une ou l’autre de vos bibliothèques installées qui sont obsolètes.

Par défaut, la commande **de mise à niveau** ne répertorie que les bibliothèques qui sont périmées; il ne les met pas à niveau. Pour réellement mettre à niveau les bibliothèques, utilisez l’option **--no-dry-run.**

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Options de mise à niveau

- **--no-dry-run** Effectuer la mise à niveau ; quand cette option n’est pas spécifiée, la commande ne fait que lister les packages obsolètes.
- **--keep-going** Continuer l’installation des packages, même si l’un d’eux échoue.
- **--triplet \<t>** Définir le triplet par défaut pour les packages non qualifiés.
- **--vcpkg-root \<chemin>** Spécifier le répertoire vcpkg à utiliser à la place du répertoire actif ou du répertoire de l’outil.

### <a name="upgrade-example"></a>Exemple de mise à niveau

L’exemple suivant montre comment mettre à niveau les bibliothèques spécifiées uniquement. vcpkg tire automatiquement dans les dépendances au besoin.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Apporter de nouvelles bibliothèques

Vous pouvez inclure toutes les bibliothèques que vous souhaitez dans votre collection de ports privés. Pour suggérer une nouvelle bibliothèque pour le catalogue public, ouvrez un problème sur la [page des problèmes vcpkg de GitHub](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Supprimer une bibliothèque

Tapez **vcpkg remove** pour supprimer une bibliothèque installée. Si d’autres bibliothèques en dépendent, on vous demande de rejouer la commande avec **--récurse**, ce qui provoque la suppression de toutes les bibliothèques en aval.

## <a name="customize-vcpkg"></a>Personnaliser vcpkg

Vous pouvez modifier votre clone de vcpkg comme vous le souhaitez. Vous pouvez même créer plusieurs clones de vcpkg, puis modifier les fichiers de port dans chacun d’eux. C’est un moyen simple d’obtenir des versions spécifiques de bibliothèque, ou de spécifier des paramètres de ligne de commande particuliers. Par exemple, dans une entreprise, des groupes individuels de développeurs peuvent travailler sur un logiciel qui a un ensemble de dépendances spécifiques à leur groupe. La solution est de configurer un clone de vcpkg pour chaque équipe. Ensuite, modifiez les clones pour télécharger les versions de la bibliothèque et définissez les commutateurs de compilation dont chaque équipe a besoin.

## <a name="uninstall-vcpkg"></a>Désinstaller vcpkg

Il suffit de supprimer l’annuaire vcpkg. La suppression de ce répertoire désinstalle la distribution de vcpkg, et toutes les bibliothèques que vcpkg a installées.

## <a name="send-feedback-about-vcpkg"></a>Envoyer des commentaires à propos de vcpkg

Utilisez la commande **vcpkg contact --survey** pour envoyer des commentaires à Microsoft sur vcpkg, notamment des rapports de bogues et des suggestions de fonctionnalités.

## <a name="the-vcpkg-folder-hierarchy"></a>La hiérarchie des dossiers vcpkg

Toutes les données et les fonctionnalités de vcpkg sont autonomes dans une hiérarchie de répertoires unique, appelée « instance ». Il n’existe pas de paramètre de Registre ni de variable d’environnement. Vous pouvez avoir n’importe quel nombre d’instances de vcpkg sur une machine, et ils ne seront pas interférer les uns avec les autres.

Une instance de vcpkg comporte les éléments suivants :

- buildtrees -- Contient les sous-dossiers des sources à partir desquelles chaque bibliothèque est générée.
- docs -- Documentation et exemples.
- downloads -- Copies mises en cache des sources ou outils téléchargés. vcpkg recherche ici d’abord lorsque vous exécutez la commande d’installation.
- installed -- Contient les en-têtes et les fichiers binaires de chaque bibliothèque installée. Lorsque vous vous intégrez à Visual Studio, vous lui dites essentiellement d’ajouter ce dossier à ses chemins de recherche.
- packages -- Dossier interne pour l’environnement intermédiaire entre les installations.
- ports -- Fichiers qui décrivent chaque bibliothèque dans le catalogue, sa version et l’endroit où la télécharger. Le cas échéant, vous pouvez ajouter vos propres ports.
- scripts -- Scripts (cmake, powershell) utilisés par vcpkg.
- toolsrc -- Code source C++ de vcpkg et des composants associés.
- triplets -- Contient les paramètres pour chaque plateforme cible prise en charge (par exemple, windows x86 ou uwp x64).

## <a name="command-line-reference"></a>Informations de référence sur la ligne de commande

|Commande|Description|
|---------|---------|
|**vcpkg \[pat recherche]**|Rechercher des packages disponibles pour l’installation|
|**vcpkg install \<pkg>...**|Installer un package|
|**vcpkg remove \<pkg>...**|Désinstaller un package|
|**vcpkg remove --outdated**|Désinstaller tous les packages obsolètes|
|**vcpkg list**|Lister les packages installés|
|**vcpkg update**|Afficher la liste des packages pour la mise à jour|
|**vcpkg upgrade**|Regénérer tous les packages obsolètes|
|**vcpkg fichier \<de hachage> \[alg]**|Hacher un fichier à l’aide d’un algorithme spécifique, par défaut SHA512|
|**vcpkg integrate install**|Mettre les packages installés à la disposition des utilisateurs. Nécessite des privilèges d’administrateur lors de la première utilisation|
|**vcpkg integrate remove**|Supprimer l’intégration à l’échelle de l’utilisateur|
|**vcpkg integrate project**|Générer un package NuGet de référence pour un usage de projet VS individuel|
|**vcpkg \<export pkg>... \[opt]...**|Exporter un package|
|**vcpkg edit \<pkg>**|Ouvrir un port pour la modification (utilise %EDITOR%, 'code' par défaut)|
|**vcpkg \<créer pkg> \<url> \[nom d’archive]**|Créer un package|
|**vcpkg cache**|Lister les packages compilés mis en cache|
|**vcpkg version**|Afficher les informations de version|
|**vcpkg contact --survey**|Afficher les coordonnées pour envoyer des commentaires.|

### <a name="options"></a>Options

|Option|Description|
|---------|---------|
|**--triplet \<t>**|Spécifier le triplet de l’architecture cible. (valeur par défaut : `%VCPKG_DEFAULT_TRIPLET%`, voir aussi **vcpkg help triplet**)|
|**--vcpkg-root \<chemin>**|Spécifier le répertoire racine de vcpkg (valeur par défaut : `%VCPKG_ROOT%`)|
