---
title: Avertissement du compilateur (niveau 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187061"
---
# <a name="compiler-warning-level-1-c4369"></a>Avertissement du compilateur (niveau 1) C4369

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
