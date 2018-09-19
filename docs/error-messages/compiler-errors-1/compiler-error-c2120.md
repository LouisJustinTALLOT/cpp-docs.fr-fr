---
title: Erreur du compilateur C2120 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2120
dev_langs:
- C++
helpviewer_keywords:
- C2120
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4f4247d8e752e71b86829ea61756f2f04d26762
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105990"
---
# <a name="compiler-error-c2120"></a>Erreur du compilateur C2120

'void' non conforme avec tous les types

Le `void` type est utilisé dans une déclaration avec un autre type.

L’exemple suivant génère C2120 :

```
// C2120.cpp
int main() {
   void int i;   // C2120
   int j;   // OK
}
```