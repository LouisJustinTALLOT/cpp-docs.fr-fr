---
title: Erreur du compilateur C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 8a1525539c84ea427815a03057bb6d2f9213fec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431108"
---
# <a name="compiler-error-c3707"></a>Erreur du compilateur C3707

'fonction' : la méthode dispinterface doit avoir un dispid

Si vous utilisez un `dispinterface` (méthode), vous devez lui assigner un `dispid`. Pour corriger cette erreur, vous devez affecter un `dispid` à la `dispinterface` méthode, par exemple, en supprimant commentaires le `id` attribut sur la méthode dans l’exemple ci-dessous. Pour plus d’informations, voir les attributs [dispinterface](../../windows/dispinterface.md) et [id](../../windows/id.md).

L’exemple suivant génère l’erreur C3707 :

```
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