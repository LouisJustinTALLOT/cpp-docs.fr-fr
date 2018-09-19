---
title: Erreur du compilateur C2275 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2275
dev_langs:
- C++
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: deedbf10edd3d9fd870dfbb1a896e504bfe9d877
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052360"
---
# <a name="compiler-error-c2275"></a>Erreur du compilateur C2275

'identificateur' : utilisation non conforme de ce type en tant qu’expression

Une expression utilise le `->` opérateur avec un `typedef` identificateur.

L’exemple suivant génère l’erreur C2275 :

```
// C2275.cpp
typedef struct S {
    int mem;
} *S_t;
void func1( int *parm );
void func2() {
    func1( &S_t->mem );   // C2275, S_t is a typedef
}
```