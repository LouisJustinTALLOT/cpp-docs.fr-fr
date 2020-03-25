---
title: Classes et structs (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 19d95c9519670db39f3ca467aff794233823d7ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180886"
---
# <a name="classes-and-structs-c"></a>Classes et structs (C++)

Cette section présente les classes et structs C++. Les deux constructions sont identiques en C++ sauf que l'accessibilité par défaut est publique dans les structs, alors qu'elle est privée dans les classes.

Les classes et structs sont les constructions par lesquels vous définissez vos propres types. Les classes et structs peuvent tous deux contenir des données membres et des fonctions membres, qui vous permettent de décrire l'état et le comportement du type.

Cet article contient les rubriques suivantes :

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Vue d’ensemble des membres de classe](../cpp/class-member-overview.md)

- [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md)

- [Héritage](../cpp/inheritance-cpp.md)

- [Membres static](../cpp/static-members-cpp.md)

- [Conversions de type définies par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md)

- [Membres de données mutables (spécificateur mutable)](../cpp/mutable-data-members-cpp.md)

- [Déclarations de classes imbriquées](../cpp/nested-class-declarations.md)

- [Types de classes anonymes](../cpp/anonymous-class-types.md)

- [Pointeurs vers des membres](../cpp/pointers-to-members.md)

- [Pointeur this](../cpp/this-pointer.md)

- [Champs de bits C++](../cpp/cpp-bit-fields.md)

Les trois types de classes sont la structure, la classe et l'union. Ils sont déclarés à l’aide des mots clés [struct](../cpp/struct-cpp.md), [Class](../cpp/class-cpp.md)et [Union](../cpp/unions.md) . Le tableau suivant montre les différences entre les trois types de classes.

Pour plus d’informations sur les unions, consultez [unions](../cpp/unions.md). Pour plus d’informations sur les classes et C++les structs dans/CLI et C++/CX, consultez [classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Contrôle d'accès et contraintes de structures, de classes et d'unions

|Structures|Classes|Unions|
|----------------|-------------|------------|
|la clé de classe est **struct**|la clé de classe est **classe**|la clé de classe est **Union**|
|L'accès par défaut est public|L'accès par défaut est privé|L'accès par défaut est public|
|Aucune contrainte d'utilisation|Aucune contrainte d'utilisation|Utilisation d'un seul membre à la fois|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)
