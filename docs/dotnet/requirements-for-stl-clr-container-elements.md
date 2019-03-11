---
title: Spécifications pour les éléments de conteneur STL/CLR
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 113624b15a0c2c6062feb7113c4771fda6d6cf39
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739403"
---
# <a name="requirements-for-stlclr-container-elements"></a>Spécifications pour les éléments de conteneur STL/CLR

Tous les types de référence sont insérées dans des conteneurs STL/CLR doivent avoir au minimum, les éléments suivants :

- Un constructeur de copie public.

- Un opérateur d’assignation publique.

- Un destructeur public.

En outre, les conteneurs associatifs comme [définir](../dotnet/set-stl-clr.md) et [carte](../dotnet/map-stl-clr.md) doit avoir un opérateur de comparaison public défini, qui est `operator<` par défaut. Certaines opérations sur les conteneurs peuvent également nécessiter un constructeur public par défaut et un opérateur d’équivalence public à définir.

Comme les types référence, les types valeur et les descripteurs pour faire référence à types qui doivent être insérés dans un conteneur associatif doivent avoir un opérateur de comparaison tels que `operator<` défini. La configuration requise pour un constructeur de copie public, opérateur d’assignation publique et un destructeur public n’existe pas pour les types valeur ou les handles aux types référence.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
