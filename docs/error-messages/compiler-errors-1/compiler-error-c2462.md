---
description: 'En savoir plus sur : erreur du compilateur C2462'
title: Erreur du compilateur C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: f85d8f2e38c38043765b29b6e766c0cbd4fef1fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341813"
---
# <a name="compiler-error-c2462"></a>Erreur du compilateur C2462

'identificateur' : impossible de définir un type dans une’New-expression'

Vous ne pouvez pas définir un type dans le champ d’opérande de l' **`new`** opérateur. Placez la définition de type dans une instruction distincte.

L’exemple suivant génère l’C2462 :

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
