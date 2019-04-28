---
title: Erreur du compilateur C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 09f3578bff5806fc32a3b5599dcfa8caa3696974
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256321"
---
# <a name="compiler-error-c2971"></a>Erreur du compilateur C2971

'classe' : paramètre de modèle 'param' : 'arg' : une variable locale ne peut pas être utilisée comme argument sans type

Vous ne pouvez pas utiliser le nom ou l’adresse d’une variable locale comme argument template.

L’exemple suivant génère l’erreur C2971 :

```
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```