---
title: Erreur du compilateur C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: d7c55ede285d027b1a65b33adbf6407df243f068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635637"
---
# <a name="compiler-error-c3824"></a>Erreur du compilateur C3824

'membre' : ce type ne peut pas apparaître dans ce contexte (paramètre de fonction, type de retour ou un membre statique)

Épinglage de pointeurs ne peuvent pas être des paramètres de fonction, types de retour ou déclarés `static`.

## <a name="example"></a>Exemple

L’exemple suivant génère C3824 :

```
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
