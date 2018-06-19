---
title: Erreur du compilateur C3733 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3733
dev_langs:
- C++
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7d5531bf9eb7352f1866bc0800734a78261b585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266628"
---
# <a name="compiler-error-c3733"></a>Erreur du compilateur C3733
'événement' : syntaxe incorrecte pour spécifier un événement COM ; n’auriez-vous pas oublié '__interface' ?  
  
 Une syntaxe incorrecte a été utilisée pour un événement COM. Pour corriger cette erreur, modifiez le type d’événement ou corrigez la syntaxe pour se conformer aux règles d’événement COM.  
  
 L’exemple suivant génère l’erreur C3733 :  
  
```  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[coclass, event_source(com), // change 'com' to 'native' to resolve  
uuid("00000000-0000-0000-0000-000000000001")]  
class A  
{  
   __event void func();   // C3733  
};  
  
int main()  
{  
}  
```