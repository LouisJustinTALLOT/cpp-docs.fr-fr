---
title: Modifications générales apportées au langage (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418455"
---
# <a name="general-language-changes-ccli"></a>Modifications d'ordre général apportées au langage (C++/CLI)

Un nombre de fonctionnalités de langage CLR modifié à partir des Extensions managées pour C++ vers Visual C++.

Les modifications décrites dans cette section sont une sorte de sorte de pot-pourri de langage. Il inclut une modification dans la gestion des littéraux de chaîne, une modification de la résolution de surcharge entre des points de suspension et la `Param` d’attribut, la modification de `typeof` à `typeid`, une modification dans l’appel des listes d’initialiseurs de constructeur et le introduction d’une nouvelle notation de cast, celle de `safe_cast`.

[Littéral de chaîne](../dotnet/string-literal.md)<br/>
Explique comment la gestion des littéraux de chaîne a changé.

[Tableau Param et points de suspension](../dotnet/param-array-and-ellipsis.md)<br/>
Explique comment `ParamArray` est désormais priorité sur les points de suspension (`...`) pour résoudre les appels de fonction avec des nombres d’arguments variables.

[typeof va à T::typeid](../dotnet/typeof-goes-to-t-typeid.md)<br/>
Explique comment la `typeof` opérateur a été supplanté par `typeid`.

[Listes d’initialiseurs](../dotnet/initializer-lists.md)<br/>
Traite des modifications dans l’ordre d’appel de listes d’initialiseurs.

[Notation castée et introduction de safe_cast](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
Traite des modifications à la notation de cast et en particulier l’introduction de `safe_cast`.

## <a name="see-also"></a>Voir aussi

[Initiation à la migration de C++/CLI](../dotnet/cpp-cli-migration-primer.md)