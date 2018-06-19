---
title: Erreur du compilateur C3709 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3709
dev_langs:
- C++
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e42cb78c54dd1529a02733b5d8e0246ab6806289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263866"
---
# <a name="compiler-error-c3709"></a>Erreur du compilateur C3709
'fonction' : syntaxe incorrecte pour spécifier un événement dans __hook /\__unhook  
  
 Lorsque vous spécifiez une source d’événement avec [__hook](../../cpp/hook.md) ou [__unhook](../../cpp/unhook.md), le premier paramètre doit être une méthode d’événement valide et le second paramètre doit être un objet de source d’événement valide (pas une méthode).  
  
 L’exemple suivant génère l’erreur C3709 :  
  
```  
// C3709.cpp  
// compile with: /LD  
[event_source(native)]  
class CEventSrc  
{  
public:  
   __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec  
{  
public:  
   void handler1()  
   {  
   }  
  
   void HookEvents(CEventSrc* pSrc)  
   {  
      __hook(bad, pSrc, CEventRec::handler1);   // C3709  
      // Try the following line instead:  
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc)  
   {  
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
```