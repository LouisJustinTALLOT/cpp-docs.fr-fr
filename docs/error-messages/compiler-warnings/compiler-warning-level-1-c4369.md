---
title: Avertissement du compilateur (niveau 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207028"
---
# <a name="compiler-warning-level-1-c4369"></a>Avertissement du compilateur (niveau 1) C4369

'énumérateur' : valeur de l’énumérateur 'value' ne peut pas être représentée comme 'type', la valeur est 'nouvelle_valeur'

Un énumérateur a été calculé est supérieure à la plus grande valeur pour le type sous-jacent spécifié.  Cela a provoqué un dépassement de capacité et le compilateur a la valeur de l’énumérateur à la plus petite valeur possible pour le type encapsulé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4369 :.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```