---
title: Ligne de commande BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 61035ce0f211e6a474bb83fc7de7d95b4a29cf3d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272908"
---
# <a name="bscmake-command-line"></a>Ligne de commande BSCMAKE

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Pour exécuter BSCMAKE, utilisez la syntaxe de ligne de commande suivante :

```
BSCMAKE [options] sbrfiles
```

Options peuvent apparaître uniquement dans le `options` champ sur la ligne de commande.

Le *sbrfiles* champ spécifie un ou plusieurs fichiers .sbr créés par un compilateur ou un assembleur. Séparez les noms des fichiers .sbr avec des espaces ou des tabulations. Vous devez spécifier l’extension. Il n’existe aucune valeur par défaut. Vous pouvez spécifier un chemin d’accès avec le nom de fichier, et vous pouvez utiliser des caractères génériques de système d’exploitation (\* et ?).

Pendant une génération incrémentielle, vous pouvez spécifier de nouveaux fichiers .sbr qui ne faisaient pas partie de la génération d’origine. Si vous souhaitez que toutes les contributions à rester dans le fichier d’informations de consultation, vous devez spécifier tous les fichiers .sbr (y compris les fichiers tronqués) qui ont servi à créer le fichier .bsc. Si vous omettez un fichier .sbr, la contribution de ce fichier pour le fichier d’informations est supprimée.

Ne spécifiez pas un fichier .sbr tronqué pour une génération complète. Une génération complète nécessite la contribution de tous les fichiers .sbr spécifié. Avant d’effectuer une génération complète, recompilez le projet et créez un fichier .sbr pour chaque fichier vide.

La commande suivante exécute BSCMAKE pour générer un fichier nommé MAIN.bsc à partir de trois fichiers .sbr :

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

Pour plus d’informations, consultez [BSCMAKE, fichier de commandes](bscmake-command-file-response-file.md) et [Options BSCMAKE](bscmake-options.md).

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](bscmake-reference.md)
