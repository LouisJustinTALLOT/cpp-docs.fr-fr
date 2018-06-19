---
title: Chemins de recherche des dépendants | Documents Microsoft
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
ms.openlocfilehash: 577fc7e44bfff35cf7efdcff20dc4cdca1c7001e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380483"
---
# <a name="search-paths-for-dependents"></a>Chemins de recherche des dépendants
À chaque dépendant correspond un chemin de recherche facultatif, spécifié comme suit :  
  
## <a name="syntax"></a>Syntaxe  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>Notes  
 NMAKE recherche d’un dépendant dans le répertoire en cours, puis dans les répertoires dans l’ordre spécifié. Une macro peut spécifier tout ou partie d’un chemin de recherche. Placez les noms de répertoires entre accolades ({}) ; Séparez les répertoires multiples par un point-virgule ( ;). Aucun des espaces ou des onglets ne sont autorisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépendants](../build/dependents.md)