---
description: 'En savoir plus sur : ligne de commande BSCMAKE'
title: Ligne de commande BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: a0d6cb81fb207c30cd89fbfe3a988380a865a399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182656"
---
# <a name="bscmake-command-line"></a>Ligne de commande BSCMAKE

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Pour exécuter BSCMAKE, utilisez la syntaxe de ligne de commande suivante :

```
BSCMAKE [options] sbrfiles
```

Les options peuvent apparaître uniquement dans le `options` champ sur la ligne de commande.

Le champ *sbrfiles* spécifie un ou plusieurs fichiers. SBR créés par un compilateur ou un assembleur. Séparez les noms des fichiers. SBR par des espaces ou des tabulations. Vous devez spécifier l’extension ; Il n’y a pas de valeur par défaut. Vous pouvez spécifier un chemin d’accès avec le nom de fichier, et vous pouvez utiliser les caractères génériques du système d’exploitation ( \* et ?).

Pendant une génération incrémentielle, vous pouvez spécifier de nouveaux fichiers. sbr qui ne faisaient pas partie de la build d’origine. Si vous souhaitez que toutes les contributions restent dans le fichier d’informations de consultation, vous devez spécifier tous les fichiers. SBR (y compris les fichiers tronqués) qui ont été utilisés à l’origine pour créer le fichier. bsc. Si vous omettez un fichier. SBR, la contribution de ce fichier au fichier d’informations de consultation est supprimée.

Ne spécifiez pas de fichier. sbr tronqué pour une génération complète. Une build complète requiert des contributions de tous les fichiers. SBR spécifiés. Avant d’effectuer une génération complète, recompilez le projet et créez un nouveau fichier. SBR pour chaque fichier vide.

La commande suivante exécute BSCMAKE pour générer un fichier appelé MAIN. bsc à partir de trois fichiers. SBR :

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

Pour obtenir des informations connexes, consultez [BSCMAKE, fichier de commandes](bscmake-command-file-response-file.md) et BSCMAKE, [options](bscmake-options.md).

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](bscmake-reference.md)
