---
title: Erreur du compilateur C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: c491217f01d8e78375401b54faa48d9db410ccad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756719"
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
