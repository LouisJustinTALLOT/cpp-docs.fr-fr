---
title: Erreur du compilateur C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: 94a6f180c93839646d771509145b2f65a00780fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746862"
---
# <a name="compiler-error-c2505"></a>Erreur du compilateur C2505

'Symbol' : ' __declspec (modifier) 'ne peut s’appliquer qu’aux déclarations ou définitions d’objets globaux ou de données membres static

Un modificateur de `__declspec` conçu pour être utilisé uniquement au niveau de la portée globale a été utilisé dans une fonction.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

L’exemple suivant génère l’C2505 :

```cpp
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
