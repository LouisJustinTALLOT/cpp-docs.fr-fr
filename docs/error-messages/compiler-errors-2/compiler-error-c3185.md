---
description: 'En savoir plus sur : erreur du compilateur C3185'
title: Erreur du compilateur C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 7dbcf11aa7c88d883aeccc8325832849f8b7a238
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242013"
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
