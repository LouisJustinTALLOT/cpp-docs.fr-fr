---
description: 'En savoir plus sur : erreur du compilateur C3769'
title: Erreur du compilateur C3769
ms.date: 11/04/2016
f1_keywords:
- C3769
helpviewer_keywords:
- C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
ms.openlocfilehash: 5ed980ed75997637a59c6f2a0f864a20297e9a97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291699"
---
# <a name="compiler-error-c3769"></a>Erreur du compilateur C3769

'type' : une classe imbriquée ne peut pas avoir le même nom que la classe immédiatement englobante

Une classe imbriquée ne peut pas avoir le même nom que la classe immédiatement englobante.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3769.

```cpp
// C3769.cpp
// compile with: /c
class x {
   class x {};   // C3769
   class y {
      class x{};   // OK
   };
};
```
