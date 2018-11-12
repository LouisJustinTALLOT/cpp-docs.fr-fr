---
title: Erreur du compilateur C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: 226fc078312a214c561e80064474ee237245c0f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559976"
---
# <a name="compiler-error-c2824"></a>Erreur du compilateur C2824

type de retour de 'operator new' doit être ' void *'

Avec des pointeurs non based, les surcharges de l’opérateur `new` doit retourner `void *`.

L’exemple suivant génère l’erreur C2824 :

```
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```