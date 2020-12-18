---
title: informations de référence sur la ligne de commande vcpkg
description: Découvrez comment utiliser les options de ligne de commande pour vcpkg sur Windows, macOS et Linux.
ms.date: 12/17/2020
ms.topic: reference
ms.technology: cpp-ide
ms.openlocfilehash: d60ebf983fea2eb41430f05b8c12e4a4a6fe370b
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684244"
---
# <a name="vcpkg-command-line-reference"></a>informations de référence sur la ligne de commande vcpkg

Référence rapide aux commandes disponibles dans vcpkg.

## <a name="commands"></a>Commandes

| Commande | Description |
|--|--|
| **`vcpkg search [pat]`** | Rechercher des packages disponibles pour l’installation |
| **`vcpkg install <pkg>...`** | Installer un package |
| **`vcpkg remove <pkg>...`** | Désinstaller un package |
| **`vcpkg remove --outdated`** | Désinstaller tous les packages obsolètes |
| **`vcpkg list`** | Lister les packages installés |
| **`vcpkg update`** | Afficher la liste des packages pour la mise à jour |
| **`vcpkg upgrade`** | Regénérer tous les packages obsolètes |
| **`vcpkg hash <file> [alg]`** | Hacher un fichier à l’aide d’un algorithme spécifique, par défaut SHA512 |
| **`vcpkg integrate install`** | Mettre les packages installés à la disposition des utilisateurs. Nécessite des privilèges d’administrateur lors de la première utilisation |
| **`vcpkg integrate remove`** | Supprimer l’intégration à l’échelle de l’utilisateur |
| **`vcpkg integrate project`** | Générer un package NuGet de référence pour un usage de projet VS individuel |
| **`vcpkg export <pkg>... [opt]...`** | Exporter un package |
| **`vcpkg edit <pkg>`** | Ouvrir un port pour la modification (utilise %EDITOR%, 'code' par défaut) |
| **`vcpkg create <pkg> <url> [archivename]`** | Créer un package |
| **`vcpkg cache`** | Lister les packages compilés mis en cache |
| **`vcpkg version`** | Afficher les informations de version |
| **`vcpkg contact --survey`** | Afficher les coordonnées pour envoyer des commentaires. |

## <a name="options"></a>Options

| Option | Description |
|--|--|
| **`--triplet <t>`** | Spécifier le triplet de l’architecture cible. (par défaut : `%VCPKG_DEFAULT_TRIPLET%` , voir aussi **`vcpkg help triplet`** ) |
| **`--vcpkg-root <path>`** | Spécifier le répertoire racine de vcpkg (valeur par défaut : `%VCPKG_ROOT%`) |

## <a name="see-also"></a>Voir aussi

[vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS](./vcpkg.md)\
[vcpkg sur GitHub](https://github.com/Microsoft/vcpkg)\
[Installer vcpkg](install-vcpkg.md)\
[Intégrer vcpkg](integrate-vcpkg.md)\
[Gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md)\
[Démarrage rapide](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[Forum aux questions](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
