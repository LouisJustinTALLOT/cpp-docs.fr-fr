---
title: Erreur du compilateur C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757954"
---
# <a name="compiler-error-c3707"></a>Erreur du compilateur C3707

'fonction' : la méthode dispinterface doit avoir un DISPID

Si vous utilisez une méthode `dispinterface`, vous devez lui assigner une `dispid`. Pour corriger cette erreur, assignez un `dispid` à la méthode `dispinterface`, par exemple, en supprimant les marques de commentaire de l’attribut `id` sur la méthode dans l’exemple ci-dessous. Pour plus d’informations, consultez attributs [dispinterface](../../windows/dispinterface.md) et [ID](../../windows/id.md).

L’exemple suivant génère l’C3707 :

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
