---
title: Référence de bibliothèque STL/CLR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cab573b0c1de57ef2629f662108098095b722eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171820"
---
# <a name="stlclr-library-reference"></a>Référence de bibliothèque STL/CLR
La bibliothèque STL/CLR est un package d’un sous-ensemble de la bibliothèque C++ Standard pour une utilisation avec C++ et le common language runtime (CLR) du .NET Framework. Avec STL/CLR, vous pouvez utiliser tous les conteneurs, les itérateurs et les algorithmes de la bibliothèque standard dans un environnement géré.  
  
 Pour utiliser STL/CLR :  
  
-   Inclure les en-têtes à partir de la **cliext** incluent le sous-répertoire au lieu des équivalents de bibliothèque C++ Standard habituelles.  
  
-   Qualifie les noms de bibliothèque avec `cliext::` au lieu de `std::`.  
  
 STL/CLR expose les types génériques et les interfaces qu’il utilise dans les scénarios inter-assembly dans l’assembly .NET **Microsoft.VisualC.STLCLR.dll**. Cette DLL est incluse dans le .NET Framework 3.5. Si vous redistribuez une application qui utilise STL/CLR, vous devez inclure le .NET Framework 3.5, ainsi que toutes les bibliothèques Visual C++ qui utilise de votre projet, dans la section des dépendances de votre projet d’installation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Espace de noms cliext](../dotnet/cliext-namespace.md)  
 Décrit l’espace de noms qui contient tous les types de la bibliothèque STL/CLR.  
  
 [STL/CLR, conteneurs](../dotnet/stl-clr-containers.md)  
 Fournit une vue d’ensemble des conteneurs qui se trouvent dans la bibliothèque C++ Standard, y compris les exigences d’éléments de conteneur, les types d’éléments qui peuvent être insérées et les problèmes de propriété.  
  
 [Exigences pour les éléments de conteneur STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)  
 Décrit la configuration minimale requise pour tous les types de référence sont insérées dans des conteneurs de bibliothèque C++ Standard.  
  
 [Guide pratique pour convertir une collection .NET en conteneur STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 Décrit comment convertir une collection .NET à un conteneur STL/CLR.  
  
 [Guide pratique pour convertir un conteneur STL/CLR en collection .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 Décrit comment convertir un conteneur STL/CLR en collection .NET.  
  
 [Guide pratique pour exposer un conteneur STL/CLR d’un assembly](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 Montre comment afficher les éléments de plusieurs conteneurs STL/CLR sont écrites dans un assembly C++.  
  
 En outre, cette section décrit également les composants suivants de STL/CLR :  
  
|||  
|-|-|  
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|  
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|  
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|  
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|  
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|  
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|  
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|  
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|  
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|  
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque C++ Standard](../standard-library/cpp-standard-library-reference.md)