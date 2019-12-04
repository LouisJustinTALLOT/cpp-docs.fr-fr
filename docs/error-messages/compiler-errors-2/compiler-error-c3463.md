---
title: Erreur du compilateur C3463
ms.date: 11/04/2016
f1_keywords:
- C3463
helpviewer_keywords:
- C3463
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
ms.openlocfilehash: e4aa8405d9baac61b8d3addead6ac19bbf6fd3b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756589"
---
# <a name="compiler-error-c3463"></a>Erreur du compilateur C3463

'type' : type non autorisé dans l’attribut 'implements'

Un type non valide a été passé à l’attribut [implements](../../windows/implements-cpp.md) . Par exemple, vous pouvez passer une interface à `implements`, mais vous ne pouvez pas passer un pointeur à une interface.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3463.

```cpp
// C3463.cpp
// compile with: /c
#include <windows.h>
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X {};

typedef X* PX;

[ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463
// try the following line instead
// [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ]
class CMyClass : public X {};
```
