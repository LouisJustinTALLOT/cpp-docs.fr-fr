---
title: Avertissement du compilateur (niveau 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: 617cb2cc3774b288581a3868125ced19b28ba45a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966510"
---
# <a name="compiler-warning-level-1-c4369"></a>Avertissement du compilateur (niveau 1) C4369

'Enumerator' : la valeur de l’énumérateur’value’ne peut pas être représentée en tant que’type', la valeur est’new_value'

Un énumérateur a été calculé pour être supérieur à la valeur la plus élevée pour le type sous-jacent spécifié.  Cela a provoqué un dépassement de capacité et le compilateur a encapsulé la valeur de l’énumérateur à la valeur la plus basse possible pour le type.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4369.

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```