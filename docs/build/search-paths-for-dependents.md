---
title: Chemins de recherche des dépendants | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1fd407f99abb98fb949b6d5bcc45b10c6ff9121
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706296"
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