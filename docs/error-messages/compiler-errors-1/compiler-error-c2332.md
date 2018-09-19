---
title: Erreur du compilateur C2332 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2332
dev_langs:
- C++
helpviewer_keywords:
- C2332
ms.assetid: fb05cd68-e271-4bea-9fb7-ef4edb0a26ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4652dfbc1965abccb31aa6edb5419446af7ba68a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027971"
---
# <a name="compiler-error-c2332"></a>Erreur du compilateur C2332

'typedef' : nom de balise manquant

Le compilateur a détecté une définition de type incomplet.

L’exemple suivant génère l’erreur C2332 :

```
// C2332.cpp
// compile with: /c
struct S {
   int i;
};

typedef struct * pS;   // C2332
typedef struct S* pS;   // OK

int get_S_i(pS p) {
   return p->i;
}
```