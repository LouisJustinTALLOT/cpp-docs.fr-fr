---
title: Compilateur avertissement (niveau 4) C4690 | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853320"
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
