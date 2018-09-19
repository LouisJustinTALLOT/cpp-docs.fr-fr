---
title: Avertissement LNK4105 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024981"
---
# <a name="linker-tools-warning-lnk4105"></a>Avertissement des outils Éditeur de liens LNK4105

aucun argument spécifié avec l’option 'option' ; option ignorée

Cet avertissement se produit uniquement lorsque le [/LIBPATH](../../build/reference/libpath-additional-libpath.md) option est définie. Si aucun répertoire n’est spécifié avec cette option, l’éditeur de liens ignore l’option et génère ce message d’avertissement.

Si vous n’avez pas besoin remplacer les paramètres de bibliothèque d’environnement existant, supprimez l’option /LIBPATH à partir de la ligne de commande de l’éditeur de liens. Si vous souhaitez utiliser un autre chemin de recherche pour les bibliothèques, spécifiez le chemin d’accès à l’autre suite de l’option /LIBPATH.

## <a name="example"></a>Exemple

```
link /libpath:c:\filepath\lib bar.obj
```

l’éditeur de liens pour rechercher les bibliothèques requises dans `c:\filepath\lib` avant de les rechercher dans les emplacements par défaut.