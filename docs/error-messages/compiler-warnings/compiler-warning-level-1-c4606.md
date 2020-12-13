---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4606'
title: Avertissement du compilateur (niveau 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: b347be103d2a84dba2143861cb35b67f3d38fb9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341735"
---
# <a name="compiler-warning-level-1-c4606"></a>Avertissement du compilateur (niveau 1) C4606

\#pragma warning : 'warning_number’ignoré ; Les avertissements de l’analyse du code ne sont pas associés à des niveaux d’avertissement

Pour les avertissements d’analyse du code, seuls, `error` `once` et `default` sont pris en charge avec le pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4606.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```
