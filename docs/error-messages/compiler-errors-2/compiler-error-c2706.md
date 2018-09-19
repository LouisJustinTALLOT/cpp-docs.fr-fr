---
title: Erreur du compilateur C2706 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2706
dev_langs:
- C++
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 560edb9953d4f7c751f4ab4102fd544fb09bb86d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066009"
---
# <a name="compiler-error-c2706"></a>Erreur du compilateur C2706

__except non conforme sans correspondance \__try (manquant '}' dans \__try bloc ?)

Le compilateur n’a pas trouvé une accolade fermante pour un `__try` bloc.

L’exemple suivant génère l’erreur C2706 :

```
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```