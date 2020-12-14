---
description: 'En savoir plus sur : erreur du compilateur C3707'
title: Erreur du compilateur C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 77a1193eae9b9d0158065978438b5af1d2176d12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241844"
---
# <a name="compiler-error-c3707"></a>Erreur du compilateur C3707

'fonction' : la méthode dispinterface doit avoir un DISPID

Si vous utilisez une `dispinterface` méthode, vous devez lui assigner un `dispid` . Pour corriger cette erreur, assignez un `dispid` à la `dispinterface` méthode, par exemple, en supprimant les marques de commentaire de l' `id` attribut sur la méthode dans l’exemple ci-dessous. Pour plus d’informations, consultez attributs [dispinterface](../../windows/attributes/dispinterface.md) et [ID](../../windows/attributes/id.md).

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
