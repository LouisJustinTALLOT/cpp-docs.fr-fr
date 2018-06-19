---
title: Erreur du compilateur C3136 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f892c7f3d1ca7bf2aebf3ecfe7574182b544fd01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248849"
---
# <a name="compiler-error-c3136"></a>Erreur du compilateur C3136
'interface' : une interface COM ne peut hériter que d’une autre interface COM, 'interface' n’est pas une interface COM  
  
 Une interface à laquelle vous avez appliqué un [attribut interface](../../windows/interface-attributes.md) hérite d’une interface qui n’est pas une interface COM. Finalement, une interface COM hérite `IUnknown`. N’importe quelle interface précédé d’un attribut d’interface est une interface COM.  
  
 L’exemple suivant génère l’erreur C3136 :  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```