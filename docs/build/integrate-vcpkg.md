---
title: Intégrer vcpkg à Visual Studio ou Visual Studio Code
description: Découvrez comment intégrer vcpkg à Visual Studio sur Windows, ou Visual Studio Code sur macOS et Linux.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: b6f092313dde14b10a05d4cff0904adf5174b264
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684248"
---
# <a name="integrate-vcpkg-with-visual-studio-or-visual-studio-code"></a>Intégrer vcpkg à Visual Studio ou Visual Studio Code

vcpkg est un gestionnaire de package en ligne de commande multiplateforme pour les bibliothèques C et C++. Vous pouvez l’intégrer à Visual Studio sur Windows ou Visual Studio Code sur Linux et macOS.

## <a name="integrate-with-visual-studio-on-windows"></a>Intégrer avec Visual Studio sur Windows

### <a name="integrate-per-user"></a>Intégrer par utilisateur

À partir du répertoire racine vcpkg, exécutez **`vcpkg integrate install`** pour configurer Visual Studio afin de localiser tous les fichiers d’en-tête vcpkg et les fichiers binaires pour chaque utilisateur. Il n’est pas nécessaire de modifier les chemins d’accès aux répertoires VC + + dans Visual Studio. Si vous disposez de plusieurs clones de vcpkg, le clone sur lequel vous exécutez cette commande devient le nouvel emplacement par défaut.

Vous pouvez maintenant inclure des en-têtes en tapant le nom du dossier ou de l’en-tête, et la saisie semi-automatique vous aide. Vous n’avez pas besoin d’effectuer d’étapes supplémentaires pour créer des liens vers des bibliothèques ou pour ajouter des références de projet. L’illustration suivante montre comment Visual Studio recherche les *`azure-storage-cpp`* en-têtes. vcpkg place ses en-têtes dans le *`/installed`* sous-dossier, partitionné par la plateforme cible. Le diagramme suivant montre la liste des fichiers include dans le *`/was`* sous-dossier de la bibliothèque :

![Fenêtre contextuelle de saisie semi-automatique IntelliSense dans l’éditeur Visual Studio](media/vcpkg-intellisense.png "vcpkg et IntelliSense")

### <a name="integrate-per-project"></a>Intégrer par projet

Si vous devez utiliser une version spécifique d’une bibliothèque qui est différente de la version de votre instance active vcpkg, procédez comme suit :

1. Créez un nouveau clone de vcpkg. Pour plus d’informations, voir [install vcpkg](install-vcpkg.md).

1. Accédez au nouveau répertoire racine vcpkg.

1. Modifiez le portfile pour la bibliothèque afin d’obtenir la version dont vous avez besoin.

1. Exécutez **`vcpkg install <library>`** . Pour plus d’informations, consultez [gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md).

1. Utilisez **`vcpkg integrate project`** pour créer un package NuGet qui fait référence à cette bibliothèque pour chaque projet.

## <a name="integrate-with-visual-studio-code-on-linux-or-macos"></a>Intégration avec Visual Studio Code sur Linux ou macOS

Dans votre shell ou fenêtre de terminal, accédez au répertoire racine vcpkg. Exécutez ensuite **`./vcpkg integrate install`** pour configurer Visual Studio code sur Linux ou MacOS. Cette commande définit l’emplacement des bibliothèques et des outils vcpkg, et active IntelliSense sur les fichiers sources.

## <a name="remove-vcpkg-integration"></a>Supprimer l’intégration vcpkg

Si vous avez utilisé l' **`integrate`** option, vous devez supprimer l’intégration avant de supprimer une instance vcpkg. Pour supprimer et nettoyer votre intégration, accédez au répertoire racine vcpkg. Sur Windows, exécutez **`vcpkg integrate remove`** pour vous assurer que l’intégration est nettoyée. Sur Linux ou macOS, exécutez la **`./vcpkg integrate remove`** commande.

## <a name="see-also"></a>Voir aussi

[vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS](./vcpkg.md)\
[vcpkg sur GitHub](https://github.com/Microsoft/vcpkg)\
[Installer vcpkg](install-vcpkg.md)\
[Gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md)\
[informations de référence sur la ligne de commande vcpkg](vcpkg-command-line-reference.md)\
[Démarrage rapide](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[Forum aux questions](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
