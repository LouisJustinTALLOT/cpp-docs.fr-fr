---
title: Chemins de recherche des dépendants
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 9f2251a5fff9d708a783797d04606572e5ebce62
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426457"
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
