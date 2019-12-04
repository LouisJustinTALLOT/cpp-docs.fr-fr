---
title: Erreur du compilateur C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761931"
---
# <a name="compiler-error-c3532"></a>Erreur du compilateur C3532

'type' : utilisation incorrecte de’auto'

Le type indiqué ne peut pas être déclaré avec le mot clé `auto`. Par exemple, vous ne pouvez pas utiliser le mot clé `auto` pour déclarer un tableau ou un type de retour de méthode.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que l’expression d’initialisation génère un type valide.

1. Veillez à ne pas déclarer un tableau ou un type de retour de méthode.

## <a name="example"></a>Exemple

L’exemple suivant génère C3532, car le mot clé `auto` ne peut pas déclarer un type de retour de méthode.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Exemple

L’exemple suivant génère C3532, car le mot clé `auto` ne peut pas déclarer un tableau.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)
