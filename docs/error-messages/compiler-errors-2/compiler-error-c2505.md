---
title: Erreur du compilateur C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: eabed85c61eaaa43b0106e0011f0357ece2e1ae1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221170"
---
# <a name="compiler-error-c2505"></a>Erreur du compilateur C2505

'Symbol' : ' __declspec (modifier) 'ne peut s’appliquer qu’aux déclarations ou définitions d’objets globaux ou de données membres static

Un **`__declspec`** modificateur conçu pour être utilisé uniquement au niveau de la portée globale a été utilisé dans une fonction.

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
