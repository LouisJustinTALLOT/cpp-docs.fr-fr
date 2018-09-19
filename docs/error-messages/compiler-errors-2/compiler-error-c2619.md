---
title: Erreur du compilateur C2619 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2619
dev_langs:
- C++
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bbf372e615c727a619d83daa6b673490edc4172
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109156"
---
# <a name="compiler-error-c2619"></a>Erreur du compilateur C2619

'identificateur' : un membre de données statique n'est pas autorisé dans un struct ou union anonyme

Un membre d'un struct ou d'une union anonyme est déclaré `static`.

L'exemple suivant génère l'erreur C2619 et montre comment résoudre le problème en supprimant le mot clé static.

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```