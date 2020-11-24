---
title: __raise
description: Découvrez comment utiliser le mot clé d’extension Microsoft C++ `__raise` pour la gestion des événements natifs.
ms.date: 11/20/2020
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.openlocfilehash: c9df602803062bc51b8c0cee13f17263cdc91786
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483144"
---
# <a name="__raise-keyword"></a>`__raise` mot

Met en évidence le site d'appel d'un événement.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="syntax"></a>Syntaxe

> **`__raise`** *`method-declarator`* **`;`**

## <a name="remarks"></a>Notes

À partir du code managé, un événement ne peut être déclenché qu’à partir de la classe dans laquelle il est défini. Pour plus d’informations, consultez [`event`](../extensions/event-cpp-component-extensions.md).

Le mot clé **`__raise`** provoque l’émission d’une erreur si vous appelez un non-événement.

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="example"></a>Exemple

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>Voir aussi

[Mot](../cpp/keywords-cpp.md)\
[Gestion des événements](../cpp/event-handling.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[Extensions de composants pour .NET et UWP](../extensions/component-extensions-for-runtime-platforms.md)
