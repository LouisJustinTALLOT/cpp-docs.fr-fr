---
title: classe ref et struct ref (C++/CLI et C++/CX)
ms.date: 05/30/2019
ms.topic: reference
f1_keywords:
- ref class
- value class
- ref struct
- value struct
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 42742d8fadad78702a665e5c53119f022bc00971
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228724"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>classe ref et struct ref (C++/CLI et C++/CX)

Les extensions **classe ref** ou **struct ref** déclarent une classe ou un struct dont la *durée de vie des objets* est automatiquement administrée. Lorsque l’objet n’est plus accessible ou se trouve hors de portée, la mémoire est libérée.

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

*class_access*<br/>
(Facultatif) Accessibilité de la classe ou du struct en dehors de l’assembly. Les valeurs possibles sont **`public`** et **`private`** ( **`private`** est la valeur par défaut). Les classes ou structs imbriqués ne peuvent pas avoir de spécificateur *class_access*.

*name*<br/>
Nom de la classe ou du struct.

*modificateur*<br/>
(Facultatif) [abstract](abstract-cpp-component-extensions.md) et [sealed](sealed-cpp-component-extensions.md) sont des modificateurs valides.

*inherit_access*<br/>
(Facultatif) Accessibilité de *base_type*. La seule accessibilité autorisée est **`public`** ( **`public`** est la valeur par défaut).

*base_type*<br/>
(Facultatif) Le type de base. Toutefois, un type valeur ne peut pas agir comme un type de base.

Pour plus d’informations, consultez les descriptions propres aux langages de ce paramètre dans les sections Windows Runtime et Common Language Runtime.

### <a name="remarks"></a>Notes

L’accessibilité par défaut d’un objet déclaré avec une classe **ref** ou une **classe value** est **`private`** . Et l’accessibilité par défaut des membres d’un objet déclaré avec **struct Ref** ou **struct value** est **`public`** .

Quand un type référence hérite d’un autre type référence, les fonctions virtuelles dans la classe de base doivent être explicitement remplacées (avec [override](override-cpp-component-extensions.md)) ou masquées (avec [new (nouvel emplacement dans vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)). Les fonctions de classe dérivée doivent également être marquées explicitement comme **`virtual`** .

Pour détecter au moment de la compilation si un type est une **classe ref** ou un **struct ref**, ou une **classe value** ou un **struct value**, utilisez `__is_ref_class (type)`, `__is_value_class (type)`, ou `__is_simple_value_class (type)`. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](compiler-support-for-type-traits-cpp-component-extensions.md).

Pour plus d'informations sur les classes et structs, consultez

- [Instanciation de classes et structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Sémantique de pile C++ pour les types référence](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Classes, structures et unions](../cpp/classes-and-structs-cpp.md)

- [Destructeurs et finaliseurs dans Comment : définir et consommer des classes et des structs (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Opérateurs définis par l’utilisateur (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Conversions définies par l’utilisateur (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Comment : encapsuler une classe native pour une utilisation par C #](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Classes génériques (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Consultez [Classes et structures de référence](../cppcx/ref-classes-and-structs-c-cx.md) et [Classes de valeur et structures de valeur](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="parameters"></a>Paramètres

*base_type*<br/>
(Facultatif) Le type de base. Une **classe ref** ou un **struct ref** peuvent hériter de zéro interface ou plus et de zéro ou un type **ref**. Une **classe value** ou un **struct value** peuvent uniquement hériter de zéro interface ou plus.

Quand vous déclarez un objet à l’aide des mots clés **ref class** ou **ref struct**, l’objet est accessible par un descripteur, autrement dit, un pointeur de compteur de référence vers l’objet. Quand la variable déclarée est hors de portée, le compilateur supprime automatiquement l'objet sous-jacent. Quand l'objet est utilisé en tant que paramètre dans un appel ou qu'il est stocké dans une variable, un handle vers l'objet est réellement transmis ou stocké.

Quand vous déclarez un objet à l’aide des mots clés **value class** ou **value struct**, la durée de vie de l’objet déclaré n’est pas contrôlée. L'objet est comme toute autre classe ou tout autre struct C++ standard.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les différences spécifiques à C++/CLI par rapport à la syntaxe indiquée dans la section **Tous les runtimes**.

### <a name="parameters"></a>Paramètres

*base_type*<br/>
(Facultatif) Le type de base. Une **classe ref** ou un **struct ref** peuvent hériter de zéro interface managée ou plus et de zéro ou un type ref. Une **classe value** ou un **struct value** peuvent uniquement hériter de zéro interface managée ou plus.

Les mots clés **ref class** et **ref struct** indiquent au compilateur que la classe ou le struct doivent être alloués sur le tas. Quand l'objet est utilisé en tant que paramètre dans un appel ou qu'il est stocké dans une variable, une référence à l'objet est réellement transmise ou stockée.

Les mots clés **value class** et **value struct** indiquent au compilateur que la valeur de la classe allouée ou du struct alloué est transmise aux fonctions ou stockée dans les membres.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
