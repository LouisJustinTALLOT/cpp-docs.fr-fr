---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4377'
title: Avertissement du compilateur (niveau 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: 674bfb69a20c901f20509a7359ed408b0e38f479
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185698"
---
# <a name="compiler-warning-level-1-c4377"></a>Avertissement du compilateur (niveau 1) C4377

les types natifs sont privés par défaut ; -d1PrivateNativeTypes est déconseillé

Dans les versions précédentes, les types natifs dans les assemblys étaient publics par défaut, et une option de compilateur non documentée interne (**/d1PrivateNativeTypes**) était utilisée pour les rendre privés.

Tous les types, natif et CLR, sont désormais privés par défaut dans un assembly, de sorte que **/d1PrivateNativeTypes** n’est plus nécessaire.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4377.

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```
