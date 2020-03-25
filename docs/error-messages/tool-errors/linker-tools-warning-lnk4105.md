---
title: Avertissement des outils Éditeur de liens LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183291"
---
# <a name="linker-tools-warning-lnk4105"></a>Avertissement des outils Éditeur de liens LNK4105

aucun argument spécifié avec l’option’option'; option ignorée

Cet avertissement se produit uniquement lorsque l’option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) est définie. Si aucun répertoire n’est spécifié avec cette option, l’éditeur de liens ignore l’option et génère ce message d’avertissement.

Si vous n’avez pas besoin de remplacer les paramètres existants de la bibliothèque environnementale, supprimez l’option/LIBPATH de la ligne de commande de l’éditeur de liens. Si vous souhaitez utiliser un autre chemin de recherche pour les bibliothèques, spécifiez le chemin alternatif suivant l’option/LIBPATH.

## <a name="example"></a>Exemple

```
link /libpath:c:\filepath\lib bar.obj
```

indique à l’éditeur de liens de rechercher les bibliothèques requises dans `c:\filepath\lib` avant de rechercher dans les emplacements par défaut.
