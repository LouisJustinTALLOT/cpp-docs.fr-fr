---
title: Erreur du compilateur C3707 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d18d4a82d06018cdba6147ba6756b1718648847a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052780"
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