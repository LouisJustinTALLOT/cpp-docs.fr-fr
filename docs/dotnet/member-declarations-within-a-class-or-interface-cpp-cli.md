---
title: Déclarations de membre dans une classe ou Interface (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430631"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>Déclarations de membre dans une classe ou interface (C++/CLI)

La déclaration de propriétés et les opérateurs a été largement revue d’Extensions managées pour C++ vers Visual C++, en masquant les détails d’implémentation sous-jacente qui ont été exposés dans la conception des Extensions managées. Déclarations d’événements ont été modifiées également.

Sous la catégorie des modifications que n’avez aucune prise en charge des Extensions managées, les constructeurs statiques peuvent désormais être définis hors ligne (ils devaient être définies inline dans les Extensions managées) et la notion d’un constructeur de délégation a été introduit.

## <a name="in-this-section"></a>Dans cette section

[Déclaration de propriété](../dotnet/property-declaration.md)<br/>
Traite des modifications apportées aux déclarations de propriété.

[Déclaration de l’index de la propriété](../dotnet/property-index-declaration.md)<br/>
Traite des modifications apportées aux déclarations de propriété indexée.

[Délégués et événements](../dotnet/delegates-and-events.md)<br/>
Traite des modifications apportées à la syntaxe de déclaration des délégués et événements.

[Sceller une fonction virtuelle](../dotnet/sealing-a-virtual-function.md)<br/>
Traite des modifications apportées à la syntaxe pour sceller une fonction.

[Opérateurs surchargés](../dotnet/overloaded-operators.md)<br/>
Traite des modifications apportées à la surcharge d’opérateur.

[Modifications apportées aux opérateurs de conversion](../dotnet/changes-to-conversion-operators.md)<br/>
Traite des modifications apportées aux opérateurs de conversion.

[Substitution explicite d’un membre d’interface](../dotnet/explicit-override-of-an-interface-member.md)<br/>
Traite des modifications apportées à la méthode de substitution explicitement un membre d’interface.

[Fonctions virtuelles privées](../dotnet/private-virtual-functions.md)<br/>
Traite des modifications dans le traitement des fonctions virtuelles privées dans les classes dérivées.

[La liaison Static Const Int n’est plus littérale](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
Traite des modifications de la façon `static const` membres intégraux sont liés et comment déclarer explicitement une constante à l’aide de la nouvelle `literal` mot clé.

## <a name="see-also"></a>Voir aussi

[Initiation à la migration de C++/CLI](../dotnet/cpp-cli-migration-primer.md)