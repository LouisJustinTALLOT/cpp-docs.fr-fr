---
title: Avertissement des outils Éditeur de liens LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 880c8519a530f492d0c322575a1386af8a7d0187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310927"
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