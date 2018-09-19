---
title: Erreur du compilateur C3009 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3009
dev_langs:
- C++
helpviewer_keywords:
- C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd26f94ecb97e578073f2c3991ed13ebdc592fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035227"
---
# <a name="compiler-error-c3009"></a>Erreur du compilateur C3009

'étiquette' : saut dans le bloc structuré OpenMP non autorisé

Le code ne peut pas sauter dans ou hors d’un bloc OpenMP.

L’exemple suivant génère l’erreur C3009 :

```
// C3009.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
   lbl2:;
   }
   goto lbl2;   // C3009
}
```