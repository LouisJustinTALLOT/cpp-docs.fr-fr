---
title: Gérer les bibliothèques avec vcpkg
description: Découvrez comment gérer des bibliothèques à l’aide de vcpkg sur Windows, macOS et Linux.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: 88f8bc1cff7b4b04f5e38b5018676e313383733f
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684249"
---
# <a name="manage-libraries-with-vcpkg"></a>Gérer les bibliothèques avec vcpkg

Une fois que vous avez [installé vcpkg](install-vcpkg.md), vous pouvez l’utiliser pour obtenir et générer des bibliothèques sur votre ordinateur local.

## <a name="search-the-list-of-available-libraries"></a>Recherche dans la liste des bibliothèques disponibles

### <a name="windows"></a>[Windows](#tab/windows)

Pour voir quels packages sont disponibles, tapez **`vcpkg search`** à l’invite de commandes.

Cette commande énumère les fichiers de contrôle dans les *`vcpkg/ports`* sous-dossiers. Une liste semblable à celle-ci s’affiche :

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

### <a name="macos"></a>[macOS](#tab/macos)

Pour voir quels packages sont disponibles, accédez au répertoire racine vcpkg et entrez **`./vcpkg search`** dans Terminal.

Cette commande énumère les fichiers de contrôle dans les *`vcpkg/ports`* sous-dossiers. Une liste semblable à celle-ci s’affiche :

```Terminal
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

```Terminal
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-computer"></a>Installer une bibliothèque sur votre ordinateur

Une fois que vous avez obtenu le nom d’une bibliothèque à l’aide de **`vcpkg search`** , vous utilisez **`vcpkg install`** pour télécharger la bibliothèque et la compiler. vcpkg utilise le portfile de la bibliothèque dans le répertoire *ports* . Si un triplet n’est pas spécifié, vcpkg installe et compile pour l’triplet par défaut pour la plateforme cible : x86-Windows, x64-Linux. cmake ou x64-OSX. cmake.

Pour les bibliothèques Linux, vcpkg dépend de l’installation de gcc sur l’ordinateur local. Sur macOS, vcpkg utilise Clang.

Lorsque le portfile spécifie des dépendances, vcpkg les télécharge et les installe également. Après le téléchargement, vcpkg génère la bibliothèque à l’aide du système de génération que la bibliothèque utilise. Les projets CMake (sur Windows) et MSBuild sont préférables, mais MAKE est pris en charge de même que tout autre système de génération. Si vcpkg ne parvient pas à trouver le système de génération spécifié sur l’ordinateur local, il le télécharge et l’installe.

```Terminal
$ ./vcpkg install boost

The following packages will be built and installed:
    boost:x86-macos
  * bzip2:x86-macos
  * zlib:x86-macos
Additional packages (*) will be installed to complete this operation.
```

Pour les projets CMake, utilisez `CMAKE_TOOLCHAIN_FILE` pour mettre des bibliothèques à disposition avec `find_package()` . Par exemple :

```Terminal
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
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

Vous pouvez spécifier une option spécifique à installer sur la ligne de commande. Par exemple, pour installer des bibliothèques pour la boucle à l’aide du backend SSL par défaut, utilisez la **`./vcpkg install curl[ssl]`** commande. La commande installe les composants requis, y compris la bibliothèque principale, si nécessaire.

### <a name="linux"></a>[Linux](#tab/linux)

Pour voir quels packages sont disponibles, accédez au répertoire racine vcpkg dans l’interpréteur de commandes, puis entrez **`./vcpkg search`** .

Cette commande énumère les fichiers de contrôle dans les *`vcpkg/ports`* sous-dossiers. Une liste semblable à celle-ci s’affiche :

```shell
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Vous pouvez filtrer sur un modèle, par exemple **`./vcpkg search ta`** :

```shell
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-linux-machine"></a>Installer une bibliothèque sur votre machine Linux

Une fois que vous avez obtenu le nom d’une bibliothèque à l’aide de **`./vcpkg search`** , vous utilisez **`/vcpkg install`** pour télécharger la bibliothèque et la compiler. vcpkg utilise le portfile de la bibliothèque dans le *`ports`* répertoire. Si un triplet n’est pas spécifié, vcpkg installe et compile pour l’triplet par défaut pour la plateforme cible, par exemple x64-Linux. cmake.

Pour les bibliothèques Linux, vcpkg dépend de l’installation de gcc sur l’ordinateur local.

Lorsque le portfile spécifie des dépendances, vcpkg les télécharge et les installe également. Après le téléchargement, vcpkg génère la bibliothèque à l’aide du système de génération que la bibliothèque utilise. Les projets CMake sont préférés, mais le fait est pris en charge avec tout autre système de génération. Si vcpkg ne parvient pas à trouver le système de génération spécifié sur l’ordinateur local, il le télécharge et l’installe.

```shell
$ ./vcpkg install boost:x64-linux

The following packages will be built and installed:
    boost:x64-linux
  * bzip2:x64-linux
  * zlib:x64-linux
Additional packages (*) will be installed to complete this operation.
```

Pour les projets CMake, utilisez `CMAKE_TOOLCHAIN_FILE` pour mettre des bibliothèques à disposition avec `find_package()` . Par exemple :

```shell
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
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

Vous pouvez spécifier une option spécifique à installer sur la ligne de commande. Par exemple, pour installer des bibliothèques pour la boucle à l’aide du backend SSL par défaut, utilisez la **`./vcpkg install curl[ssl]`** commande. La commande installe les composants requis, y compris la bibliothèque principale, si nécessaire.

---

## <a name="list-the-libraries-already-installed"></a>Répertorier les bibliothèques déjà installées

Après avoir installé certaines bibliothèques, vous pouvez utiliser la **`vcpkg list`** commande sur Windows pour voir ce que vous avez. Les commandes Linux et macOS sont analogues.

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

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

L’exemple suivant montre comment mettre à niveau uniquement les bibliothèques spécifiées sur Windows. Les commandes Linux et macOS sont analogues. vcpkg extrait automatiquement les dépendances si nécessaire.

```cmd
c:\users\username\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
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

## <a name="see-also"></a>Voir aussi

[vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS](./vcpkg.md)\
[vcpkg sur GitHub](https://github.com/Microsoft/vcpkg)\
[Installer vcpkg](install-vcpkg.md)\
[Intégrer vcpkg](integrate-vcpkg.md)\
[informations de référence sur la ligne de commande vcpkg](vcpkg-command-line-reference.md)\
[Démarrage rapide](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[Forum aux questions](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)\
[Installation et utilisation de packages exemple : SQLite](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)
