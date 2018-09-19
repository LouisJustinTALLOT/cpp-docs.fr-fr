---
title: Erreur du compilateur C2274 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcc6b0afe78e089c268f69274be1cbfb6f3d32c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093197"
---
# <a name="compiler-error-c2274"></a>Erreur du compilateur C2274

'type' : non conforme à droite de '.' opérateur

Un type apparaît comme l’opérande de droite d’un opérateur d’accès aux membres (.).

Cette erreur peut résulter en essayant d’accéder à une conversion de type défini par l’utilisateur. Utilisez le mot clé `operator` entre la période et `type`.

L’exemple suivant génère l’erreur C2286 :

```
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```