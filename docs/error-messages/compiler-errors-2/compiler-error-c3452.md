---
title: Erreur du compilateur C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: 165c031f23f3b317300900970b30414da42e7840
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397443"
---
# <a name="compiler-error-c3452"></a>Erreur du compilateur C3452

le membre argument de la liste n'est pas une constante

Un argument a été passé à un attribut qui attendait une constante, valeur qui peut être évaluée au moment de la compilation.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3452.

```
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```