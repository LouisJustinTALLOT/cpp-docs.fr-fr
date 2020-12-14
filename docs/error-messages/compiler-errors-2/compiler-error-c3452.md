---
description: 'En savoir plus sur : erreur du compilateur C3452'
title: Erreur du compilateur C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: 7153088ccd132112f47823cd1eb1147480615fc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315983"
---
# <a name="compiler-error-c3452"></a>Erreur du compilateur C3452

le membre argument de la liste n'est pas une constante

Un argument a été passé à un attribut qui attendait une constante, valeur qui peut être évaluée au moment de la compilation.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3452.

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```
