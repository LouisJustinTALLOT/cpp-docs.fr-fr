---
title: Compilateur avertissement (niveau 1) C4377 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613ebe183b61c6b9894ed3b726f90061e2b24ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047172"
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