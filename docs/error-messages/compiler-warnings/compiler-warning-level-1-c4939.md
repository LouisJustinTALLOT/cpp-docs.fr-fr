---
title: Avertissement du compilateur (niveau 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538530"
---
# <a name="compiler-warning-level-1-c4939"></a>Avertissement du compilateur (niveau 1) C4939

\#pragma vtordisp est déconseillé et sera supprimée dans une prochaine version de Visual C++

Le pragma [vtordisp](../../preprocessor/vtordisp.md) sera supprimé dans une prochaine version de Visual C++.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4939.

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```