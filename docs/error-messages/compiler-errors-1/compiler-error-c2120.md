---
title: Erreur du compilateur C2120
ms.date: 11/04/2016
f1_keywords:
- C2120
helpviewer_keywords:
- C2120
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
ms.openlocfilehash: fd0b11b1500ea448ded4a24db8e6d8ebf9ee9782
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212850"
---
# <a name="compiler-error-c2120"></a>Erreur du compilateur C2120

'void’non conforme avec tous les types

Le **`void`** type est utilisé dans une déclaration avec un autre type.

L’exemple suivant génère l’C2120 :

```cpp
// C2120.cpp
int main() {
   void int i;   // C2120
   int j;   // OK
}
```
