---
title: Erreur du compilateur C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: bf5ffb9b6bad3db1d264941a6aefa391be521c98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610208"
---
# <a name="compiler-error-c2505"></a>Erreur du compilateur C2505

'symbol' : '__declspec (modifier)' peut uniquement être appliqué aux déclarations ou définitions d’objets globaux ou de données membres static

Un `__declspec` modificateur qui vise uniquement à être utilisé dans une portée globale a été utilisé dans une fonction.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

L’exemple suivant génère l’erreur C2505 :

```
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```