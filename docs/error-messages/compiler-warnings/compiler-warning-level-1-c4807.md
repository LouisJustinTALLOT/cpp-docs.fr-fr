---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4807'
title: Avertissement du compilateur (niveau 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 4c015d2ee7c566199411374402719c4a8eaee37f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238139"
---
# <a name="compiler-warning-level-1-c4807"></a>Avertissement du compilateur (niveau 1) C4807

'operation' : mélange risqué de type 'type' et champ de bits signé de type 'type'

Cet avertissement est généré lors de la comparaison d’un champ de bits signé à un bit avec une **`bool`** variable. Comme un champ de bits signé à un bit ne peut contenir que les valeurs-1 ou 0, il est dangereux de le comparer à **`bool`** . Aucun avertissement n’est généré à propos de la combinaison des champs de **`bool`** bits non signés un bit et un bit, car ils sont identiques à **`bool`** et ne peuvent contenir que 0 ou 1.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4807 :

```cpp
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
