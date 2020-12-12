---
description: 'En savoir plus sur : erreur du compilateur C3210'
title: Erreur du compilateur C3210
ms.date: 11/04/2016
f1_keywords:
- C3210
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
ms.openlocfilehash: 5349a7ea8677a8a55511f514e74251375a262fb7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173907"
---
# <a name="compiler-error-c3210"></a>Erreur du compilateur C3210

'type' : la déclaration d’accès ne peut être appliquée qu’à un membre de classe de base

Une [déclaration using](../../cpp/using-declaration.md) a été spécifiée de manière incorrecte.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3210.

```cpp
// C3210.cpp
// compile with: /c
struct A {
protected:
   int i;
};

struct B {
   using A::i;   // C3210
};

struct C : public A {
   using A::i;   // OK
};
```
