---
title: Avertissement du compilateur (niveau 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: e471ca3e478d1166b150e49bf25efa4b9d5803cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402513"
---
# <a name="compiler-warning-level-1-c4606"></a>Avertissement du compilateur (niveau 1) C4606

\#Avertissement de pragma : 'numéro_avertissement' ignoré ; Avertissements d’analyse du code ne sont pas associés à des niveaux d’avertissement

Pour les avertissements d’analyse du Code, uniquement `error`, `once`, et `default` sont pris en charge avec le [avertissement](../../preprocessor/warning.md) pragma.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4606.

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```