---
title: Avertissement du compilateur (niveau 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: 30e2ecb1d5e0de290c028cdfb53c7df831a732b4
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966462"
---
# <a name="compiler-warning-level-1-c4377"></a>Avertissement du compilateur (niveau 1) C4377

les types natifs sont privés par défaut ; -d1PrivateNativeTypes est déconseillé

Dans les versions précédentes, les types natifs dans les assemblys étaient publics par défaut, et une option de compilateur non documentée interne ( **/d1PrivateNativeTypes**) était utilisée pour les rendre privés.

Tous les types, natif et CLR, sont désormais privés par défaut dans un assembly, de sorte que **/d1PrivateNativeTypes** n’est plus nécessaire.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4377.

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```