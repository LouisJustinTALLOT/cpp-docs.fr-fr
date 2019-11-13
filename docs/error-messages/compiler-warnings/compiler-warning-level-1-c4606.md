---
title: Avertissement du compilateur (niveau 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: d36031aa9a831d4669d796d8a40292e2d6ba15a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964978"
---
# <a name="compiler-warning-level-1-c4606"></a>Avertissement du compilateur (niveau 1) C4606

\#pragma warning : 'warning_number’ignoré ; Les avertissements de l’analyse du code ne sont pas associés à des niveaux d’avertissement

Pour les avertissements d’analyse du code, seuls `error`, `once`et `default` sont pris en charge avec le pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4606.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```