---
title: Erreur du compilateur C2273 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2273
dev_langs:
- C++
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 995f75487820976d045e5db05fe2b170260240cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066216"
---
# <a name="compiler-error-c2273"></a>Erreur du compilateur C2273

'type' : non conforme à droite de l’opérateur '->'

Un type apparaît comme l’opérande de droite d’un `->` opérateur.

Cette erreur peut résulter en essayant d’accéder à une conversion de type défini par l’utilisateur. Utilisez le mot clé `operator` entre -> et `type`.

L’exemple suivant génère l’erreur C2273 :

```
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```