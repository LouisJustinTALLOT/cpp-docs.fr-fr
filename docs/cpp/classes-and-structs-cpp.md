---
title: Les classes et Structs (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61348578018a5bbddcaff293fa3ed76575eb16de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413243"
---
# <a name="classes-and-structs-c"></a>Classes et structs (C++)
Cette section présente les classes et structs C++. Les deux constructions sont identiques en C++ sauf que l'accessibilité par défaut est publique dans les structs, alors qu'elle est privée dans les classes.  
  
 Les classes et structs sont les constructions par lesquels vous définissez vos propres types. Les classes et structs peuvent tous deux contenir des données membres et des fonctions membres, qui vous permettent de décrire l'état et le comportement du type.  
  
 Les rubriques suivantes sont incluses :  
  
-   [class](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Vue d’ensemble des membres de classe](../cpp/class-member-overview.md)  
  
-   [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md)  
  
-   [Héritage](../cpp/inheritance-cpp.md)  
  
-   [Membres static](../cpp/static-members-cpp.md)  
  
-   [Conversions de type définies par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [Mutables (spécificateur mutable) les membres de données](../cpp/mutable-data-members-cpp.md)  
  
-   [Déclarations de classes imbriquées](../cpp/nested-class-declarations.md)  
  
-   [Types de classes anonymes](../cpp/anonymous-class-types.md)  
  
-   [Pointeurs vers des membres](../cpp/pointers-to-members.md)  
  
-   [Pointeur this](../cpp/this-pointer.md)  
  
-   [Champs de bits C++](../cpp/cpp-bit-fields.md)  
  
 Les trois types de classes sont la structure, la classe et l'union. Ils sont déclarés à l’aide de la [struct](../cpp/struct-cpp.md), [classe](../cpp/class-cpp.md), et [union](../cpp/unions.md) mots clés (consultez [définition des Types de classe](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da)). Le tableau suivant montre les différences entre les trois types de classes.  
  
 Pour plus d’informations sur les unions, consultez [Unions](../cpp/unions.md). Pour plus d’informations sur les classes et structs, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Contrôle d'accès et contraintes de structures, de classes et d'unions  
  
|Structures|Classes|Unions|  
|----------------|-------------|------------|  
|la clé de la classe est `struct`|clé de la classe est **classe**|clé de la classe est **union**|  
|L'accès par défaut est public|L'accès par défaut est privé|L'accès par défaut est public|  
|Aucune contrainte d'utilisation|Aucune contrainte d'utilisation|Utilisation d'un seul membre à la fois|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)