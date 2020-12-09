---
title: 'vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS'
description: vcpkg est un gestionnaire de package en ligne de commande qui simplifie grandement l’acquisition et l’installation de bibliothèques C++ Open source sur Windows, macOS et Linux.
ms.date: 07/06/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: ec908824c19099ad6eaa46a4d85c0187ef12b3fd
ms.sourcegitcommit: 102bd6f7a878d85c8ceab8f28d0359f562850ea0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862553"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS

vcpkg est un gestionnaire de package en ligne de commande pour C++. Cela simplifie grandement l’acquisition et l’installation de bibliothèques tierces sur Windows, Linux et macOS. Si votre projet utilise des bibliothèques tierces, nous vous recommandons d’utiliser vcpkg pour les installer. vcpkg prend en charge les bibliothèques open source et propriétaires. La compatibilité de toutes les bibliothèques du catalogue Windows vcpkg a été testée avec Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019. Entre les catalogues Windows et Linux/macOS, vcpkg prend désormais en charge plus de 1900 bibliothèques. La communauté C++ ajoute régulièrement de nouvelles bibliothèques dans les deux catalogues.

## <a name="simple-yet-flexible"></a>Simple et pourtant flexible

À l’aide d’une commande unique, vous pouvez télécharger des sources et constituer une bibliothèque. vcpkg lui-même est un projet open source, disponible sur GitHub. Il est possible de personnaliser vos clones vcpkg privés comme vous le souhaitez. Par exemple, spécifiez des bibliothèques différentes ou des versions de bibliothèques différentes de celles figurant dans le catalogue public. Vous pouvez avoir plusieurs clones de vcpkg sur un seul ordinateur. Chacune d’elles peut être définie de façon à produire une collection personnalisée de bibliothèques, avec vos commutateurs de compilation préférés. Chaque clone est un environnement autonome avec son propre exemplaire de vcpkg.exe qui ne fonctionne que sur sa propre hiérarchie. vcpkg n’est ajouté à aucune variable d’environnement et n’a aucune dépendance vis-à-vis du Registre Windows ou de Visual Studio.

## <a name="sources-not-binaries"></a>Sources, et non des binaires

Pour les bibliothèques du catalogue Windows, vcpkg télécharge les sources à la place des binaires<sup>1</sup>. Il compile ces sources à l’aide de la version la plus récente de Visual Studio qu’il trouve. En C++, il est important que le code de votre application et les bibliothèques que vous utilisez soient compilés par le même compilateur et la même version du compilateur. En utilisant vcpkg, vous éliminez ou au moins réduisez considérablement les risques de binaires incompatibles et les problèmes qu’ils peuvent engendrer. Dans les équipes qui sont standardisées sur une version spécifique d’un compilateur, un membre de l’équipe peut utiliser vcpkg pour télécharger des sources et compiler un ensemble de fichiers binaires. Ils peuvent ensuite utiliser la commande exporter pour compresser les binaires et les en-têtes des autres membres de l’équipe. Pour plus d’informations, consultez [Exporter les fichiers binaires et les en-têtes compilés](#export_binaries_per_project).

Vous pouvez également créer un clone vcpkg contenant des bibliothèques privées dans la collection ports. Ajoutez un port qui télécharge vos fichiers binaires et en-têtes prédéfinis. Ensuite, écrivez un fichier *portfile. cmake* qui copie simplement ces fichiers à l’emplacement préféré.

<sup>1</sup> *Remarque : les sources ne sont pas disponibles pour certaines bibliothèques propriétaires. Dans ce cas, vcpkg télécharge les fichiers binaires prégénérés compatibles.*

## <a name="installation"></a>Installation

Clonez le référentiel vcpkg à partir de GitHub : [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) . Vous pouvez télécharger vers n’importe quel emplacement de dossier de votre choix. Cet emplacement est la *racine* vcpkg. Une fois le téléchargement terminé, accédez à ce répertoire dans votre interface de commande.

Dans le répertoire racine vcpkg, exécutez le programme d’amorçage vcpkg :

- **`bootstrap-vcpkg.bat`** Windows
- **`./bootstrap-vcpkg.sh`** (Linux, macOS)

Sur Linux ou macOS, vous devrez peut-être préfixer les commandes vcpkg en utilisant **`./`** dans les exemples qui suivent. N’oubliez pas d’exécuter ces commandes à partir du répertoire racine vcpkg.

## <a name="search-the-list-of-available-libraries"></a>Recherche dans la liste des bibliothèques disponibles

Pour voir quels packages sont disponibles, tapez **`vcpkg search`** à l’invite de commandes.

Cette commande énumère les fichiers de contrôle dans les sous-dossiers *vcpkg/ports* . Une liste semblable à celle-ci s’affiche :

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

Vous pouvez filtrer sur un modèle, par exemple **`vcpkg search ta`** :

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Installer une bibliothèque sur votre ordinateur local

Une fois que vous avez obtenu le nom d’une bibliothèque à l’aide de **`vcpkg search`** , vous utilisez **`vcpkg install`** pour télécharger la bibliothèque et la compiler. vcpkg utilise le portfile de la bibliothèque dans le répertoire *ports* . Si un triplet n’est pas spécifié, vcpkg installe et compile pour l’triplet par défaut pour la plateforme cible : x86-Windows, x64-Linux. cmake ou x64-OSX. cmake.

Pour les bibliothèques Linux, vcpkg dépend de l’installation de gcc sur l’ordinateur local. Sur macOS, vcpkg utilise Clang.

Lorsque le portfile spécifie des dépendances, vcpkg les télécharge et les installe également. Après le téléchargement, vcpkg génère la bibliothèque à l’aide du système de génération que la bibliothèque utilise. Les projets CMake (sur Windows) et MSBuild sont préférables, mais MAKE est pris en charge de même que tout autre système de génération. Si vcpkg ne parvient pas à trouver le système de génération spécifié sur l’ordinateur local, il le télécharge et l’installe.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Pour les projets CMake, utilisez `CMAKE_TOOLCHAIN_FILE` pour mettre des bibliothèques à disposition avec `find_package()` . Par exemple, sur Linux ou macOS :

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake
```

Sur Windows :

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake
```

Certaines bibliothèques incluent des options installables. Par exemple, lorsque vous recherchez la bibliothèque de boucles, vous voyez également une liste d’options prises en charge entre crochets :

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

Dans ce cas, les crochets **`[`** et **`]`** sont des littéraux, et non des métacaractères.

Vous pouvez spécifier une option spécifique à installer sur la ligne de commande. Par exemple, pour installer des bibliothèques pour la boucle à l’aide du backend SSL par défaut pour Windows, utilisez la **`vcpkg install curl[ssl]:x86-windows`** commande. La commande installe les composants requis, y compris la bibliothèque principale, si nécessaire :

```cmd
> vcpkg list
curl:x86-windows            7.68.0-3   A library for transferring data with URLs
curl[non-http]:x86-windows             Enables protocols beyond HTTP/HTTPS/HTTP2
curl[ssl]:x86-windows                  Default SSL backend
curl[sspi]:x86-windows                 SSPI support
curl[winssl]:x86-windows               SSL support (Secure Channel / "WinSSL")
zlib:x86-windows            1.2.11-6   A compression library
```

## <a name="list-the-libraries-already-installed"></a>Répertorier les bibliothèques déjà installées

Après avoir installé certaines bibliothèques, vous pouvez utiliser **`vcpkg list`** pour voir ce que vous avez :

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

Exécutez **`vcpkg integrate install`** pour configurer Visual Studio afin de localiser tous les fichiers d’en-tête vcpkg et les fichiers binaires par utilisateur. Il n’est pas nécessaire de modifier manuellement les chemins d’accès des répertoires VC + +. Si vous disposez de plusieurs clones de vcpkg, le clone sur lequel vous exécutez cette commande devient le nouvel emplacement par défaut.

À présent, vous pouvez #include en-têtes en tapant simplement le dossier/l’en-tête, et la saisie semi-automatique vous aide. Aucune étape supplémentaire n’est nécessaire pour la liaison à des bibliothèques, ou pour l’ajout de références de projet. L’illustration suivante montre comment Visual Studio recherche les en-têtes azure-storage-cpp. vcpkg place ses en-têtes dans le sous-dossier */installed*, partitionné par la plateforme cible. Le diagramme suivant présente la liste des fichiers include dans le sous-dossier */was* pour la bibliothèque :

![vcpkg et IntelliSense](media/vcpkg-intellisense.png "vcpkg et IntelliSense")

### <a name="per-project"></a>Par projet

Si vous devez utiliser une version spécifique d’une bibliothèque qui est différente de la version de votre instance active vcpkg, procédez comme suit :

1. Créez un clone de vcpkg.
1. Modifiez le portfile de la bibliothèque pour obtenir la version dont vous avez besoin.
1. Exécutez **`vcpkg install <library>`** .
1. Utilisez **`vcpkg integrate project`** pour créer un package NuGet qui fait référence à cette bibliothèque pour chaque projet.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Intégration avec Visual Studio Code (Linux/macOS)

Exécutez **`vcpkg integrate install`** pour configurer Visual Studio code sur Linux/MacOS. Cette commande définit l’emplacement de l’inscription vcpkg et active IntelliSense sur les fichiers sources.

## <a name="target-linux-from-windows-via-wsl"></a>Cibler Linux à partir de Windows par le biais de WSL

Vous pouvez produire des fichiers binaires Linux sur un ordinateur Windows à l’aide du sous-système Windows pour Linux ou WSL. Suivez les instructions pour [configurer WSL sur Windows 10](/windows/wsl/install-win10). Ensuite, configurez-le avec l' [extension Visual Studio pour Linux](https://devblogs.microsoft.com/cppblog/targeting-windows-subsystem-for-linux-from-visual-studio/). Il est possible de placer toutes vos bibliothèques intégrées pour Windows et Linux dans le même dossier. Ils sont accessibles à partir de Windows et WSL.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> Exporter les fichiers binaires et les en-têtes compilés

Il est inefficace de faire en sorte que tous les membres d’une équipe téléchargent et créent des bibliothèques communes. Un seul membre de l’équipe peut utiliser la **`vcpkg export`** commande pour créer un fichier zip commun des fichiers binaires et des en-têtes, ou un package NuGet. Ensuite, il est facile de la partager avec d’autres membres de l’équipe.

## <a name="updateupgrade-installed-libraries"></a>Mettre à jour ou à niveau les bibliothèques installées

Le catalogue public est mis à jour avec les dernières versions des bibliothèques. Pour déterminer quelles bibliothèques locales sont obsolètes, utilisez **`vcpkg update`** . Lorsque vous êtes prêt à mettre à jour votre collection de ports avec la dernière version du catalogue public, exécutez la **`vcpkg upgrade`** commande. Il télécharge et reconstruit automatiquement toutes les bibliothèques installées qui sont obsolètes.

Par défaut, la **`vcpkg upgrade`** commande répertorie uniquement les bibliothèques obsolètes ; elle ne les met pas à niveau. Pour mettre à niveau les bibliothèques, utilisez l' **`--no-dry-run`** option.

```cmd
> vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Options de mise à niveau

- **`--no-dry-run`**  Effectuez la mise à niveau ; lorsqu’elle n’est pas spécifiée, la commande répertorie uniquement les packages obsolètes.
- **`--keep-going`**  Continuer l’installation des packages même si l’un d’eux échoue.
- **`--triplet <t>`**  Définissez les triplets par défaut pour les packages non qualifiés.
- **`--vcpkg-root <path>`**  Spécifiez le répertoire vcpkg à utiliser au lieu du répertoire actif ou du répertoire d’outils.

### <a name="upgrade-example"></a>Exemple de mise à niveau

L’exemple suivant montre comment mettre à niveau les bibliothèques spécifiées uniquement. vcpkg extrait automatiquement les dépendances si nécessaire.

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

Tapez **`vcpkg remove`** pour supprimer une bibliothèque installée. Si d’autres bibliothèques dépendent de celle-ci, vous êtes invité à exécuter à nouveau la commande avec **`--recurse`** , ce qui entraîne la suppression de toutes les bibliothèques en aval.

## <a name="customize-vcpkg"></a>Personnaliser vcpkg

Vous pouvez modifier votre clone de vcpkg comme vous le souhaitez. Vous pouvez même créer plusieurs clones vcpkg, puis modifier les portfiles dans chacun d’eux. C’est un moyen simple d’obtenir des versions de bibliothèque spécifiques ou de spécifier des paramètres de ligne de commande particuliers. Par exemple, les groupes de développeurs individuels d’une entreprise peuvent travailler sur des logiciels qui ont des dépendances spécifiques à leur groupe. La solution consiste à configurer un clone de vcpkg pour chaque équipe. Ensuite, modifiez les clones pour télécharger les versions de la bibliothèque et définir les commutateurs de compilation dont chaque équipe a besoin.

## <a name="update-vcpkg"></a>Mettre à jour vcpkg

Le gestionnaire de package vcpkg est régulièrement mis à jour sur GitHub. Pour mettre à jour votre clone de vcpkg vers la dernière version, à partir du répertoire racine vcpkg, exécutez **`git pull`** . Cette commande synchronise votre copie de vcpkg avec la version sur GitHub. Une fois le téléchargement terminé, réexécutez le programme d’amorçage. Le programme d’amorçage reconstruit le programme vcpkg, mais laisse vos bibliothèques installées sur place.

## <a name="uninstall-vcpkg"></a>Désinstaller vcpkg

Pour désinstaller vcpkg, supprimez simplement le répertoire vcpkg. La suppression de ce répertoire désinstalle la distribution vcpkg et toutes les bibliothèques installées par vcpkg.

Toutefois, si vous avez exécuté **`vcpkg integrate install`** , vous devez exécuter **`vcpkg integrate remove`** pour vous assurer que l’intégration est nettoyée, avant que le dossier ne soit supprimé.

## <a name="send-feedback-about-vcpkg"></a>Envoyer des commentaires à propos de vcpkg

Utilisez la **`vcpkg contact --survey`** commande pour envoyer des commentaires à Microsoft sur vcpkg, notamment des rapports de bogues et des suggestions de fonctionnalités.

## <a name="the-vcpkg-folder-hierarchy"></a>La hiérarchie des dossiers vcpkg

Toutes les données et les fonctionnalités de vcpkg sont autonomes dans une hiérarchie de répertoires unique, appelée « instance ». Il n’existe pas de paramètre de Registre ni de variable d’environnement. Vous pouvez avoir un nombre quelconque d’instances de vcpkg sur un ordinateur, et elles n’interfèrent pas les unes avec les autres.

Une instance de vcpkg comporte les éléments suivants :

- buildtrees : contient les sous-dossiers des sources à partir desquelles chaque bibliothèque est créée.
- docs-documentation et exemples
- téléchargements-copies mises en cache de tous les outils ou sources téléchargées. vcpkg recherche d’abord ici quand vous exécutez la commande d’installation.
- installé : contient les en-têtes et les binaires de chaque bibliothèque installée. Lorsque vous intégrez à Visual Studio, vous lui dites essentiellement d’ajouter ce dossier à ses chemins de recherche.
- packages-dossier interne pour la mise en lots entre les installations.
- ports : fichiers qui décrivent chaque bibliothèque dans le catalogue, sa version et l’emplacement où la télécharger. Le cas échéant, vous pouvez ajouter vos propres ports.
- scripts : scripts (CMake, PowerShell) utilisés par vcpkg.
- toolsrc-code source C++ pour vcpkg et les composants associés
- triplets-contient les paramètres pour chaque plateforme cible prise en charge (par exemple, x86-Windows ou x64-UWP).

## <a name="command-line-reference"></a>Informations de référence sur la ligne de commande

|Commande|Description|
|---------|---------|
|**`vcpkg search [pat]`**|Rechercher des packages disponibles pour l’installation|
|**`vcpkg install <pkg>...`**|Installer un package|
|**`vcpkg remove <pkg>...`**|Désinstaller un package|
|**`vcpkg remove --outdated`**|Désinstaller tous les packages obsolètes|
|**`vcpkg list`**|Lister les packages installés|
|**`vcpkg update`**|Afficher la liste des packages pour la mise à jour|
|**`vcpkg upgrade`**|Regénérer tous les packages obsolètes|
|**`vcpkg hash <file> [alg]`**|Hacher un fichier à l’aide d’un algorithme spécifique, par défaut SHA512|
|**`vcpkg integrate install`**|Mettre les packages installés à la disposition des utilisateurs. Nécessite des privilèges d’administrateur lors de la première utilisation|
|**`vcpkg integrate remove`**|Supprimer l’intégration à l’échelle de l’utilisateur|
|**`vcpkg integrate project`**|Générer un package NuGet de référence pour un usage de projet VS individuel|
|**`vcpkg export <pkg>... [opt]...`**|Exporter un package|
|**`vcpkg edit <pkg>`**|Ouvrir un port pour la modification (utilise %EDITOR%, 'code' par défaut)|
|**`vcpkg create <pkg> <url> [archivename]`**|Créer un package|
|**`vcpkg cache`**|Lister les packages compilés mis en cache|
|**`vcpkg version`**|Afficher les informations de version|
|**`vcpkg contact --survey`**|Afficher les coordonnées pour envoyer des commentaires.|

### <a name="options"></a>Options

|Option|Description|
|---------|---------|
|**`--triplet <t>`**|Spécifier le triplet de l’architecture cible. (par défaut : `%VCPKG_DEFAULT_TRIPLET%` , voir aussi **`vcpkg help triplet`** )|
|**`--vcpkg-root <path>`**|Spécifier le répertoire racine de vcpkg (valeur par défaut : `%VCPKG_ROOT%`)|
