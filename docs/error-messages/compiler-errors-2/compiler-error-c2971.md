---
description: 'En savoir plus sur : erreur du compilateur C2971'
title: Erreur du compilateur C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 51cecf7fcf80b93231763bb183b870760820ca7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210385"
---
# <a name="compiler-error-c2971"></a>Erreur du compilateur C2971

'classe' : paramètre de modèle’param' : 'arg' : une variable locale ne peut pas être utilisée comme argument sans type

Vous ne pouvez pas utiliser le nom ou l’adresse d’une variable locale comme argument de modèle.

L’exemple suivant génère l’C2971 :

```cpp
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```
