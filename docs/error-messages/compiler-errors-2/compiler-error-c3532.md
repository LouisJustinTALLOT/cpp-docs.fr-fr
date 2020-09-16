---
title: Erreur du compilateur C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: f9339797f42967ef1de0253b1e51092e6d98df5d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686780"
---
# <a name="compiler-error-c3532"></a>Erreur du compilateur C3532

'type' : utilisation incorrecte de’auto'

Le type indiqué ne peut pas être déclaré avec le **`auto`** mot clé. Par exemple, vous ne pouvez pas utiliser le **`auto`** mot clé pour déclarer un tableau ou un type de retour de méthode.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que l’expression d’initialisation génère un type valide.

1. Veillez à ne pas déclarer un tableau ou un type de retour de méthode.

## <a name="examples"></a>Exemples

L’exemple suivant génère C3532, car le **`auto`** mot clé ne peut pas déclarer un type de retour de méthode.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

L’exemple suivant génère C3532, car le **`auto`** mot clé ne peut pas déclarer un tableau.

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

[Auto, mot clé](../../cpp/auto-keyword.md)
