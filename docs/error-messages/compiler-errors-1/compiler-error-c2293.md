---
title: Erreur du compilateur C2293
ms.date: 11/04/2016
f1_keywords:
- C2293
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
ms.openlocfilehash: 8073e952e8248367c444415cfb182743247dc6fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182741"
---
# <a name="compiler-error-c2293"></a>Erreur du compilateur C2293

'identificateur' : une variable membre ne peut pas être un spécificateur __based

Les spécificateurs du modificateur `__based` doivent être des pointeurs non membres.

L’exemple suivant génère l’erreur C2293 :

```
// C2293.cpp
// compile with: /c
class A {
   static int *i;
   void __based(i) *bp;   // C2293
   void *bp2;   // OK
};
```