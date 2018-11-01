---
title: Avertissement du compilateur (niveau 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518480"
---
# <a name="compiler-warning-level-4-c4690"></a>Avertissement du compilateur (niveau 4) C4690

> \[ emitidl (pop)] : plus de POP que de push

## <a name="remarks"></a>Notes

L’attribut [emitidl](../../windows/emitidl.md) a fait l’objet d’un pop de plus que les push.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4690. Pour résoudre ce problème, assurez-vous que l’attribut est dépilé exactement comme autant de fois qu’elle est envoyée.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
