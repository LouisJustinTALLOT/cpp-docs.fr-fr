---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: eb3ab24378071663b2a6a1abab700b81c3172419
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317235"
---
# <a name="__raise"></a>__raise

Met en évidence le site d'appel d'un événement.

## <a name="syntax"></a>Syntaxe

```
__raise method-declarator;
```

## <a name="remarks"></a>Notes

À partir du code managé, un événement ne peut être déclenché que par la classe dans laquelle il est défini. Voir [l’événement](../extensions/event-cpp-component-extensions.md) pour plus d’informations.

Le mot clé **__raise** provoque l’impression d’une erreur si vous appelez un non-événement.

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

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Manipulation de l’événement](../cpp/event-handling.md)<br/>
[Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md)
