---
description: 'En savoir plus sur : erreur du compilateur C3253'
title: Erreur du compilateur C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: 492530dfdfbd5b4b219dcee920fd4f4940393b3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194291"
---
# <a name="compiler-error-c3253"></a>Erreur du compilateur C3253

'fonction' : erreur de substitution explicite

Une substitution explicite a été spécifiée de manière incorrecte. Par exemple, vous ne pouvez pas spécifier une implémentation pour un remplacement que vous spécifiez également comme pure. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3253 :

```cpp
// C3253.cpp
// compile with: /clr
public interface struct I {
   void a();
   void b();
   void c();
};

public ref struct R : I {
   virtual void a() = 0, I::a {}   // C3253
   virtual void b() = I::a {}   // OK
   virtual void c() = 0;   // OK
};
```
