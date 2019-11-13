---
title: Avertissement du compilateur (niveau 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: c2c8f794356ea429f7cf647af18e06e7ebe9183e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050272"
---
# <a name="compiler-warning-level-1-c4939"></a>Avertissement du compilateur (niveau 1) C4939

\#pragma vtordisp est déconseillé et sera supprimé dans une version ultérieure de VisualC++

Le pragma [vtordisp](../../preprocessor/vtordisp.md) sera supprimé dans une prochaine version de Visual C++.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4939.

```cpp
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```