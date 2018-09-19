---
title: Compilateur avertissement (niveau 1) C4807 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8eecbd1e7c9c88ec463224b9738cebbf9ff8f4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039866"
---
# <a name="compiler-warning-level-1-c4807"></a>Avertissement du compilateur (niveau 1) C4807

'operation' : mélange risqué de type 'type' et champ de bits signé de type 'type'

Cet avertissement est généré lors de la comparaison d’un champ de bits signé à un bit avec une variable `bool` . Un champ de bits signé à un bit peut seulement contenir les valeurs -1 ou 0. Il est risqué de le comparer à `bool`. Aucun avertissement n’est généré sur la combinaison de `bool` et de champs de bits non signés à un bit, car ils sont identiques à `bool` et ne peuvent contenir que 0 ou 1.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4807 :

```
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```