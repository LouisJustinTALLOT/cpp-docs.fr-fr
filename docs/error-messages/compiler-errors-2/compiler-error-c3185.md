---
title: Erreur du compilateur C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: db448b462cd3a3f325c529e730e5c8f65e2b8f51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598807"
---
# <a name="compiler-error-c3185"></a>Erreur du compilateur C3185

'typeid' : utilisé avec le type managé ou WinRT 'type' ; utilisez 'opérateur' à la place

Vous ne pouvez pas appliquer le [typeid](../../cpp/typeid-operator.md) opérateur managée ou WinRT type ; utilisez [typeid](../../windows/typeid-cpp-component-extensions.md) à la place.

L'exemple suivant génère l'erreur C3185 et montre comment la corriger :

```
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
