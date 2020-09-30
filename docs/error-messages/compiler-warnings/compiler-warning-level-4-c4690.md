---
title: Avertissement du compilateur (niveau 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: de996128c68ebf96b4a00f6206cbaf54d97ca275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509974"
---
# <a name="compiler-warning-level-4-c4690"></a>Avertissement du compilateur (niveau 4) C4690

> \[ emitidl (POP)] : plus de pop que de push

## <a name="remarks"></a>Remarques

L’attribut [emitidl](../../windows/attributes/emitidl.md) a fait l’objet d’un pop de plus que les push.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4690. Pour résoudre ce problème, assurez-vous que l’attribut est dépilé exactement autant de fois qu’il est envoyé.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
