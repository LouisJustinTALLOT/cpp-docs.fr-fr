---
description: 'En savoir plus sur : héritage (C++)'
title: Héritage (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: d3007b8e12d6ba695a8a3e6604270a65f1118bb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113894"
---
# <a name="inheritance--c"></a>Héritage (C++)

Cette section explique comment utiliser les classes dérivées pour générer des programmes extensibles.

## <a name="overview"></a>Vue d’ensemble

Les nouvelles classes peuvent être dérivées des classes existantes à l’aide d’un mécanisme appelé « héritage » (voir les informations qui commencent par [héritage unique](../cpp/single-inheritance.md)). Les classes utilisées pour la dérivation sont appelées classes de base d'une classe dérivée particulière. Une classe dérivée est déclarée en utilisant la syntaxe suivante :

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

Après l’étiquette (nom) de la classe, un signe deux-points apparaît, suivi d’une liste de spécifications de base.  Les classes de base ainsi nommées doivent avoir été déclarées précédemment.  Les spécifications de base peuvent contenir un spécificateur d’accès, qui est l’un des mots clés **`public`** , **`protected`** ou **`private`** .  Ces spécificateurs d'accès apparaissent avant le nom de classe de base et s'appliquent uniquement à cette classe de base.  Ces spécificateurs contrôlent l'autorisation de la classe dérivée à utiliser pour les membres de la classe de base.  Consultez [member-Access Control](../cpp/member-access-control-cpp.md) pour plus d’informations sur l’accès aux membres de la classe de base.  Si le spécificateur d’accès est omis, l’accès à cette base est pris en compte **`private`** .  Les spécifications de base peuvent contenir le mot clé **`virtual`** pour indiquer l’héritage virtuel.  Ce mot clé peut apparaître avant ou après le spécificateur d'accès, le cas échéant.  Si l'héritage virtuel est utilisé, la classe de base est appelée classe de base virtuelle.

Plusieurs classes de base peuvent être spécifiées en les séparant par des virgules.  Si une seule classe de base est spécifiée, le modèle d’héritage est un [héritage simple](../cpp/single-inheritance.md). Si plusieurs classes de base sont spécifiées, le modèle d’héritage est appelé [héritage multiple](../cpp/multiple-base-classes.md).

Cet article contient les rubriques suivantes :

- [Héritage simple](../cpp/single-inheritance.md)

- [Plusieurs classes de base](../cpp/multiple-base-classes.md)

- [Fonctions virtuelles](../cpp/virtual-functions.md)

- [Substitutions explicites](../cpp/explicit-overrides-cpp.md)

- [Classes abstraites](../cpp/abstract-classes-cpp.md)

- [Résumé des règles d’étendue](../cpp/summary-of-scope-rules.md)

Les mots clés [__super](../cpp/super.md) et [__interface](../cpp/interface.md) sont documentés dans cette section.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)
