---
title: Types (C++-CL) managés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408029"
---
# <a name="managed-types-ccl"></a>Types managés (C++/CL)

La syntaxe pour la déclaration des types managés et à créer et utiliser des objets de ces types a été considérablement modifiée à partir des Extensions managées pour C++ Visual C++. Cela a été fait pour favoriser leur intégration dans le système de type ISO-C++. Ces modifications sont présentées en détail dans les sous-sections suivantes.

## <a name="in-this-section"></a>Dans cette section

[Déclaration d’un type de classe managée](../dotnet/declaration-of-a-managed-class-type.md)<br/>
Explique comment déclarer un géré `class`, `struct`, ou `interface`.

[Déclaration d’un objet de classe de référence du CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
Explique comment déclarer un objet de type de classe de référence à l’aide d’un handle de suivi.

[Déclaration d’un tableau CLR](../dotnet/declaration-of-a-clr-array.md)<br/>
Explique comment déclarer et initialiser un tableau.

[Modifications dans l’ordre d’initialisation des constructeurs](../dotnet/changes-in-constructor-initialization-order.md)<br/>
Traite des principales modifications dans l’ordre de l’initialisation de constructeur de classe.

[Modifications de la sémantique du destructeur](../dotnet/changes-in-destructor-semantics.md)<br/>
Traite de finalisation non déterministe, `Finalize` et `Dispose`, ramifications profondes pour les objets de référence et l’utilisation d’explicite `Finalize`.

**Remarque :** la discussion de délégués est différée jusqu'à ce que [délégués et événements](../dotnet/delegates-and-events.md) afin de les présenter avec les membres de l’événement dans une classe, le sujet général du [déclarations de membre dans une classe ou Interface (C + C++ / CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>Voir aussi

[Initiation à la migration de C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Tableaux](../windows/arrays-cpp-component-extensions.md)