---
title: Erreur du compilateur C2860
ms.date: 11/04/2016
f1_keywords:
- C2860
helpviewer_keywords:
- C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
ms.openlocfilehash: 25ae5f0ffee659dee2e0ac388da207a5165ecc8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214566"
---
# <a name="compiler-error-c2860"></a>Erreur du compilateur C2860

'void’ne peut pas être un type d’argument, à l’exception de' (void) '

Le type **`void`** ne peut pas être utilisé en tant que type d’argument avec d’autres arguments.

L’exemple suivant génère l’C2860 :

```cpp
// C2860.cpp
// compile with: /c
void profunc1(void, int i);   // C2860
void func10(void);   // OK
```
