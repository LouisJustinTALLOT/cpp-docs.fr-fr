---
description: 'En savoir plus sur : exigences pour les éléments de conteneur STL/CLR'
title: Spécifications pour les éléments de conteneur STL/CLR
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 3696d9df40f69b1dd39205a2dc7a3b802e815841
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305505"
---
# <a name="requirements-for-stlclr-container-elements"></a>Spécifications pour les éléments de conteneur STL/CLR

Tous les types de référence insérés dans des conteneurs STL/CLR doivent avoir au minimum les éléments suivants :

- Constructeur de copie public.

- Opérateur d’assignation public.

- Destructeur public.

En outre, les conteneurs associatifs tels que [Set](../dotnet/set-stl-clr.md) et [Map](../dotnet/map-stl-clr.md) doivent avoir un opérateur de comparaison public défini, qui est `operator<` par défaut. Certaines opérations sur les conteneurs peuvent également nécessiter un constructeur public par défaut et un opérateur d’équivalence public à définir.

Comme les types référence, les types valeur et les handles vers des types référence qui doivent être insérés dans un conteneur associatif doivent avoir un opérateur de comparaison tel que `operator<` défini. La configuration requise pour un constructeur de copie public, un opérateur d’assignation public et un destructeur public n’existe pas pour les types valeur ou les handles vers des types référence.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
