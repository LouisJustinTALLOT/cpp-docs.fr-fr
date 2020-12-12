---
description: 'En savoir plus sur : erreur du compilateur C2931'
title: Erreur du compilateur C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: a4d659a0529fa80affc6749d150b9a567d015d90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320329"
---
# <a name="compiler-error-c2931"></a>Erreur du compilateur C2931

'class' : type-class-id redéfini en tant que fonction membre d’'identifier'

Vous ne pouvez pas utiliser une classe ou un modèle générique en tant que fonction membre d’une autre classe.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2931 :

```cpp
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

L’erreur C2931 peut également se produire lors de l’utilisation de génériques.

```cpp
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```
