---
title: Erreur du compilateur C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: ab6708e7ae0a56bd71adebad4fb42d6ea9abe116
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432654"
---
# <a name="compiler-error-c2815"></a>Erreur du compilateur C2815

'operator delete' : le premier paramètre formel doit être ' void *', mais 'param' a été utilisé.

Un est défini par l’utilisateur [opérateur delete](../../standard-library/new-operators.md#op_delete) fonction doit prendre un premier paramètre formel de type `void *`.

L’exemple suivant génère l’erreur C2815 :

```
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```