---
title: Chemins de recherche des dépendants
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 8856d845d51072d205c84278978c7fbb447aed9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448800"
---
# <a name="search-paths-for-dependents"></a>Chemins de recherche des dépendants

Chaque dépendant a un chemin de recherche facultatif, spécifié comme suit :

## <a name="syntax"></a>Syntaxe

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>Notes

NMAKE recherche une dépendance tout d’abord dans le répertoire actif, puis, dans les répertoires dans l’ordre spécifié. Une macro peut spécifier tout ou partie d’un chemin de recherche. Placez les noms de répertoires entre accolades ({}) ; Séparez les répertoires multiples par un point-virgule ( ;). Aucun espace ni les onglets ne sont autorisées.

## <a name="see-also"></a>Voir aussi

[Dépendants](../build/dependents.md)