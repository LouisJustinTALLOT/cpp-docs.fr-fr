---
title: Erreur du compilateur C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 45afe70b454f72dd8c9b8ce9771ce1f5aef6a10e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777781"
---
# <a name="compiler-error-c3185"></a>Erreur du compilateur C3185

'typeid' : utilisé avec le type managé ou WinRT 'type' ; utilisez 'opérateur' à la place

Vous ne pouvez pas appliquer le [typeid](../../cpp/typeid-operator.md) opérateur managée ou WinRT type ; utilisez [typeid](../../extensions/typeid-cpp-component-extensions.md) à la place.

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
