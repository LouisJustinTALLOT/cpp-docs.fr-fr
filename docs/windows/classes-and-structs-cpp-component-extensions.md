---
title: Classes et Structs (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04a632e657b57519d02c013d9c03e558b9aec8e1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726620"
---
# <a name="classes-and-structs--c-component-extensions"></a>Classes et structs  (extensions du composant C++)

Déclare une classe ou un struct dont *durée de vie* est automatiquement administrée. Quand l'objet n'est plus accessible ou qu'il est hors de portée, Visual C++ ignore automatiquement la mémoire allouée à cet objet.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};

```

### <a name="parameters"></a>Paramètres

*accès_classe*  
(Facultatif) L’accessibilité de la classe ou un struct en dehors de l’assembly. Les valeurs possibles sont **public** et **privé** (**privé** est la valeur par défaut). Classes ou structs imbriqués ne peut pas avoir un *accès_classe* spécificateur.

*name*  
Nom de la classe ou du struct.

*Modificateur*  
(Facultatif) [abstraite](../windows/abstract-cpp-component-extensions.md) et [sealed](../windows/sealed-cpp-component-extensions.md) sont des modificateurs valides.

*hériter_accès*  
(Facultatif) L’accessibilité de *base_type*. La seule accessibilité autorisée est **public** (**public** est la valeur par défaut).

*base_type*  
(Facultatif) Un type de base. Toutefois, un type valeur ne peut pas agir comme un type de base.

Pour plus d’informations, consultez les descriptions de spécifique à la langue de ce paramètre dans le Windows Runtime et le Common Language Runtimesections.

### <a name="remarks"></a>Notes

L’accessibilité des membres par défaut d’un objet déclaré avec **classe ref** ou **classe value** est **privé**. Et l’accessibilité des membres par défaut d’un objet déclaré avec **ref struct** ou **struct value** est **public**.

Lorsqu’un type référence hérite d’un autre type référence, les fonctions virtuelles dans la classe de base doivent être explicitement remplacées (avec [remplacer](../windows/override-cpp-component-extensions.md)) ou masquées (avec [new (nouvel emplacement dans vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Les fonctions de la classe dérivée doivent également être marquées explicitement comme **virtuel**.

Permet de détecter au moment de la compilation si un type est un **classe ref** ou **ref struct**, ou un **classe value** ou **struct value**, utilisez `__is_ref_class (type)`, `__is_value_class (type)`, ou `__is_simple_value_class (type)`. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

Pour plus d'informations sur les classes et structs, consultez

- [Instanciation de Classes et Structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Sémantique de pile C++ pour les types de référence](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Classes, Structures et Unions](../cpp/classes-and-structs-cpp.md)

- [Destructeurs et finaliseurs dans Comment : définir et consommer des classes et structs (C++ / c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Opérateurs définis par l’utilisateur (C++-CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Conversions définies par l’utilisateur (C++-CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Guide pratique pour inclure une classe native dans un wrapper pour une utilisation par C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Classes génériques (C++-CLI)](../windows/generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Consultez [classes et structs Ref](../cppcx/ref-classes-and-structs-c-cx.md) et [classes et structs Value](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Paramètres

*base_type*  
(Facultatif) Un type de base. Un **classe ref** ou **ref struct** peuvent hériter de zéro ou plusieurs interfaces et zéro ou un **ref** types. Un **classe value** ou **struct value** peut uniquement hériter de zéro ou plusieurs interfaces.

Lorsque vous déclarez un objet à l’aide de la **classe ref** ou **ref struct** mots clés, l’objet est accessible par un handle vers un objet ; autrement dit, un pointeur de compteur de références à l’objet. Quand la variable déclarée est hors de portée, le compilateur supprime automatiquement l'objet sous-jacent. Quand l'objet est utilisé en tant que paramètre dans un appel ou qu'il est stocké dans une variable, un handle vers l'objet est réellement transmis ou stocké.

Lorsque vous déclarez un objet à l’aide de la **classe value** ou **struct value** mots clés, la durée de vie de l’objet déclaré n’est pas supervisée. L'objet est comme toute autre classe ou tout autre struct C++ standard.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les différences par rapport à la syntaxe indiquée dans le **tous les Runtimes** section sont spécifiques à C++ / c++ / CLI.

### <a name="parameters"></a>Paramètres

*base_type*  
(Facultatif) Un type de base. Un **classe ref** ou **ref struct** peuvent hériter de zéro ou plusieurs gérés des interfaces et zéro ou un type référence. Un **classe value** ou **struct value** peut uniquement hériter de zéro ou plusieurs interfaces gérées.

Le **classe ref** et **ref struct** mots clés indiquent au compilateur que la classe ou structure doit être alloué sur le tas. Quand l'objet est utilisé en tant que paramètre dans un appel ou qu'il est stocké dans une variable, une référence à l'objet est réellement transmise ou stockée.

Le **classe value** et **struct value** mots clés indique au compilateur que la valeur de la classe allouée ou la structure est transmise aux fonctions ou stockée dans les membres.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)