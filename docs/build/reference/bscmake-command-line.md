---
title: Ligne de commande BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 7724069a401aadcdb2e3e8487dc85273dac357fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818646"
---
# <a name="bscmake-command-line"></a>Ligne de commande BSCMAKE

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
