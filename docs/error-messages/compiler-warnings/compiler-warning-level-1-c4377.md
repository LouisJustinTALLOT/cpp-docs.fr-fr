---
title: Avertissement du compilateur (niveau 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410423"
---
# <a name="compiler-warning-level-1-c4377"></a>Avertissement du compilateur (niveau 1) C4377

les types natifs sont privés par défaut ; -d1PrivateNativeTypes est déconseillé.

Dans les versions précédentes, les types natifs dans les assemblys étaient publics par défaut et une option de compilateur interne, non documentée (**/d1PrivateNativeTypes**) a été utilisé pour les rendre privé.

Tous les types, natifs et CLR, sont désormais privés par défaut dans un assembly, donc **/d1PrivateNativeTypes** n’est plus nécessaire.

## <a name="example"></a>Exemple

L’exemple suivant génère C4377.

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```