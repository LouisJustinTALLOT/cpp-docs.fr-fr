---
title: Erreur du compilateur C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: f2fcb75098f18ad113ba68959035b37d9cddd6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667023"
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