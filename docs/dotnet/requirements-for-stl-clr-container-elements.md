---
title: Configuration requise pour les éléments de conteneur STL/CLR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 523b3e8d3f9c04a933f37032fcea670d75dafccf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162434"
---
# <a name="requirements-for-stlclr-container-elements"></a>Exigences pour les éléments de conteneur STL/CLR
Tous les types de référence sont insérées dans des conteneurs STL/CLR doivent avoir au minimum, les éléments suivants :  
  
-   Un constructeur de copie public.  
  
-   Un opérateur d’assignation de public.  
  
-   Un destructeur public.  
  
 En outre, les conteneurs associatifs comme [définir](../dotnet/set-stl-clr.md) et [carte](../dotnet/map-stl-clr.md) doivent avoir un opérateur de comparaison public défini, qui est `operator<` par défaut. Certaines opérations sur les conteneurs peuvent également nécessiter un constructeur public par défaut et un opérateur d’équivalence public à définir.  
  
 Comme les types référence, les types valeur et les descripteurs pour faire référence aux types qui doivent être insérés dans un conteneur associatif de doivent avoir un opérateur de comparaison tel que `operator<` défini. La configuration requise pour un constructeur de copie public, opérateur d’assignation public et un destructeur public n’existe pas pour les types valeur ou des handles vers des types référence.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)