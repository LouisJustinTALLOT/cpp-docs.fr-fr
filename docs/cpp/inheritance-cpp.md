---
title: Héritage (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3181369f492f82fca1590e07655e728dbbcd40ff
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958596"
---
# <a name="inheritance--c"></a>Héritage (C++)
Cette section explique comment utiliser les classes dérivées pour générer des programmes extensibles.  
  
## <a name="overview"></a>Vue d'ensemble  
 Nouvelles classes peuvent être dérivés de classes existantes à l’aide d’un mécanisme appelé « héritage » (voir le début de l’information dans [l’héritage unique](../cpp/single-inheritance.md)). Les classes utilisées pour la dérivation sont appelées classes de base d'une classe dérivée particulière. Une classe dérivée est déclarée en utilisant la syntaxe suivante :  
  
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
  
Après la balise (nom) de la classe, un signe deux-points apparaît, suivi d'une liste de spécifications de base.  Les classes de base ainsi nommées doivent avoir été déclarées précédemment.  Les spécifications de base peuvent contenir un spécificateur d’accès, qui est un des mots clés **public**, **protégé** ou **privé**.  Ces spécificateurs d'accès apparaissent avant le nom de classe de base et s'appliquent uniquement à cette classe de base.  Ces spécificateurs contrôlent l'autorisation de la classe dérivée à utiliser pour les membres de la classe de base.  Consultez [contrôle d’accès de membre](../cpp/member-access-control-cpp.md) pour plus d’informations sur l’accès aux membres de classe de base.  Si le spécificateur d’accès est omis, l’accès à cette base est considéré comme **privé**.  Les spécifications de base peuvent contenir le mot clé **virtuel** pour indiquer l’héritage virtuel.  Ce mot clé peut apparaître avant ou après le spécificateur d'accès, le cas échéant.  Si l'héritage virtuel est utilisé, la classe de base est appelée classe de base virtuelle.  
  
 Plusieurs classes de base peuvent être spécifiées en les séparant par des virgules.  Si une seule classe de base est spécifiée, le modèle d’héritage est [l’héritage simple](../cpp/single-inheritance.md). Si plusieurs classes de base est spécifié, le modèle d’héritage est appelé [l’héritage Multiple](../cpp/multiple-base-classes.md).  
  
 Les rubriques suivantes sont incluses :  
  
-   [Héritage simple](../cpp/single-inheritance.md)  
  
-   [Plusieurs classes de base](../cpp/multiple-base-classes.md)  
  
-   [Fonctions virtuelles](../cpp/virtual-functions.md)  
  
-   [Substitutions explicites](../cpp/explicit-overrides-cpp.md)  
  
-   [Classes abstraites](../cpp/abstract-classes-cpp.md)  
  
-   [Résumé des règles de portée](../cpp/summary-of-scope-rules.md)  
  
 Le [__super](../cpp/super.md) et [__interface](../cpp/interface.md) mots clés sont documentées dans cette section.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)
