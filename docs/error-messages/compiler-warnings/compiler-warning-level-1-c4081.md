---
title: Avertissement du compilateur (niveau 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: f43a736a73b4a504755cd8dc079a41e59aaf72bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363425"
---
# <a name="compiler-warning-level-1-c4081"></a>Avertissement du compilateur (niveau 1) C4081

'token1' attendu ; 'token2' trouvé

Le compilateur attendait un jeton différent dans ce contexte.

## <a name="example"></a>Exemple

```
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```