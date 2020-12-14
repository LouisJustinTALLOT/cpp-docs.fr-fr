---
description: 'En savoir plus sur : informations de référence sur la bibliothèque STL/CLR'
title: Référence de bibliothèque STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: c051b58b76a70dd5ef3bd17b1f9bec1cbeeccebf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335322"
---
# <a name="stlclr-library-reference"></a>Référence de bibliothèque STL/CLR

La bibliothèque STL/CLR fournit une interface semblable aux conteneurs de bibliothèque standard C++ à utiliser avec C++ et le .NET Framework common language runtime (CLR). STL/CLR est complètement distinct de l’implémentation Microsoft de la bibliothèque standard C++. STL/CLR est conservé pour la prise en charge héritée, mais n’est pas tenu à jour avec la norme C++. Nous vous recommandons vivement d’utiliser les conteneurs de la [bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md) natif au lieu de STL/CLR chaque fois que cela est possible.

Pour utiliser STL/CLR :

- Incluez les en-têtes du sous-répertoire **cliext** include au lieu des équivalents habituels de la bibliothèque standard C++.

- Qualifiez les noms de bibliothèque avec `cliext::` au lieu de `std::` .

La bibliothèque STL/CLR fournit une interface de type STL pour une utilisation avec C++ et le .NET Framework common language runtime (CLR). Cette bibliothèque est conservée pour la prise en charge héritée, mais elle n’est pas mise à jour avec la norme C++. Nous vous recommandons fortement d’utiliser les conteneurs de la [bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md) natif au lieu de STL/CLR.

## <a name="in-this-section"></a>Dans cette section

[Espace de noms cliext](../dotnet/cliext-namespace.md)<br/>
Présente l’espace de noms qui contient tous les types de la bibliothèque STL/CLR.

[Conteneurs STL/CLR](../dotnet/stl-clr-containers.md)<br/>
Fournit une vue d’ensemble des conteneurs qui se trouvent dans la bibliothèque standard C++, y compris les spécifications pour les éléments de conteneur, les types d’éléments qui peuvent être insérés et les problèmes de propriété.

[Exigences pour les éléments de conteneur STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Décrit la configuration minimale requise pour tous les types référence insérés dans les conteneurs de bibliothèque standard C++.

[Comment : effectuer une conversion à partir d’une collection .NET vers un conteneur STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
Décrit comment convertir une collection .NET en conteneur STL/CLR.

[Comment : effectuer une conversion à partir d’un conteneur STL/CLR en collection .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
Décrit comment convertir un conteneur STL/CLR en collection .NET.

[Comment : exposer un conteneur STL/CLR à partir d’un assembly](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
Montre comment afficher les éléments de plusieurs conteneurs STL/CLR écrits dans un assembly C++.

En outre, cette section décrit également les composants suivants de STL/CLR :

:::row:::
   :::column span="":::
      [`adapter` (STL/CLR)](../dotnet/adapter-stl-clr.md)\
      [`algorithm` (STL/CLR)](../dotnet/algorithm-stl-clr.md)\
      [`deque` (STL/CLR)](../dotnet/deque-stl-clr.md)\
      [`for each`, `in`](../dotnet/for-each-in.md)\
      [`functional` (STL/CLR)](../dotnet/functional-stl-clr.md)\
      [`hash_map` (STL/CLR)](../dotnet/hash-map-stl-clr.md)\
      [`hash_multimap` (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)\
      [`hash_multiset` (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)\
      [`hash_set` (STL/CLR)](../dotnet/hash-set-stl-clr.md)\
      [`list` (STL/CLR)](../dotnet/list-stl-clr.md)\
   :::column-end:::
   :::column span="":::
      [`map` (STL/CLR)](../dotnet/map-stl-clr.md)\
      [`multimap` (STL/CLR)](../dotnet/multimap-stl-clr.md)\
      [`multiset` (STL/CLR)](../dotnet/multiset-stl-clr.md)\
      [`numeric` (STL/CLR)](../dotnet/numeric-stl-clr.md)\
      [`priority_queue` (STL/CLR)](../dotnet/priority-queue-stl-clr.md)\
      [`queue` (STL/CLR)](../dotnet/queue-stl-clr.md)\
      [`set` (STL/CLR)](../dotnet/set-stl-clr.md)\
      [`stack` (STL/CLR)](../dotnet/stack-stl-clr.md)\
      [`utility` (STL/CLR)](../dotnet/utility-stl-clr.md)\
      [`vector` (STL/CLR)](../dotnet/vector-stl-clr.md)\
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi

[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
