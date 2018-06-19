---
title: Erreur du compilateur C3707 | Documents Microsoft
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
ms.openlocfilehash: 7268f584d9f269b4f2f15b837379ec12ab0185d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273723"
---
# <a name="compiler-error-c3707"></a>Erreur du compilateur C3707
'fonction' : la méthode dispinterface doit avoir un dispid  
  
 Si vous utilisez un `dispinterface` (méthode), vous devez lui assigner un `dispid`. Pour corriger cette erreur, vous devez affecter un `dispid` à la `dispinterface` méthode, par exemple, en supprimant commentaires le `id` attribut sur la méthode dans l’exemple ci-dessous. Pour plus d’informations, consultez les attributs [dispinterface](../../windows/dispinterface.md) et [id](../../windows/id.md).  
  
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