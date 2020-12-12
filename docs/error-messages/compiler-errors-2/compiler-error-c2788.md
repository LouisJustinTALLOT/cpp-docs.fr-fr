---
description: 'En savoir plus sur : erreur du compilateur C2788'
title: Erreur du compilateur C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: 8521df743e6c19f250d0344d4adf2299934887e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297783"
---
# <a name="compiler-error-c2788"></a>Erreur du compilateur C2788

'identificateur' : plus d’un GUID associé à cet objet

L’opérateur [__uuidof](../../cpp/uuidof-operator.md) prend un type défini par l’utilisateur avec un GUID attaché ou un objet de ce type défini par l’utilisateur. Cette erreur se produit lorsque l’argument est un objet avec plusieurs GUID.

L’exemple suivant génère l’C2788 :

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
