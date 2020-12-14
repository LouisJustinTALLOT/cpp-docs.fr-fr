---
description: 'En savoir plus sur : erreur du compilateur C3650'
title: Erreur du compilateur C3650
ms.date: 11/04/2016
f1_keywords:
- C3650
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
ms.openlocfilehash: 02230eed0f1e3448bfc91d331611f28a7b6b7531
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203729"
---
# <a name="compiler-error-c3650"></a>Erreur du compilateur C3650

'interface_method' : ne peut pas être utilisé comme substitution explicite, doit être une fonction membre virtuelle d’une classe de base

Une tentative a été effectuée pour effectuer une substitution explicite sur un membre qui n’était pas virtuel.

Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3650 :

```cpp
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```
