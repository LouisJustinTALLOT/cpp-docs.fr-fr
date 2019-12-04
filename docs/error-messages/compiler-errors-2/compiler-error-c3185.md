---
title: Erreur du compilateur C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 36f350287a1cfaf937ee739800042aaf99f31769
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761632"
---
# <a name="compiler-error-c3185"></a>Erreur du compilateur C3185

'typeid' : utilisé avec le type managé ou WinRT 'type' ; utilisez 'opérateur' à la place

Vous ne pouvez pas appliquer l’opérateur [typeid](../../cpp/typeid-operator.md) à un type managé ou WinRT ; Utilisez à la place [typeid](../../extensions/typeid-cpp-component-extensions.md) .

L'exemple suivant génère l'erreur C3185 et montre comment la corriger :

```cpp
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```
