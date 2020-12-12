---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4105'
title: Avertissement des outils Éditeur de liens LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 6536273a0b3e5b6e60b782e5953a70a7b3eb2798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294416"
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
