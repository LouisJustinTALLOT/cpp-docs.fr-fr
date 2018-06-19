---
title: Erreur du compilateur C3717 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3717
dev_langs:
- C++
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efe6cdb53b3ee78016c25b273eb4682ec380d12f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264010"
---
# <a name="compiler-error-c3717"></a>Erreur du compilateur C3717
'méthode' : une méthode qui déclenche des événements ne peut pas être définie.  
  
 Vous avez déclaré une méthode d’événement qui inclut une implémentation. Un [__event](../../cpp/event.md) déclaration de méthode ne peut pas avoir de définition. Pour corriger cette erreur, assurez-vous que les déclarations de méthode aucun événement ne possèdent les définitions. Par exemple, dans le code ci-dessous, supprimez le corps de la fonction à partir de la `event1` déclaration, comme indiqué par les commentaires.  
  
 L’exemple suivant génère l’erreur C3717 :  
  
```  
// C3717.cpp  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1() {   // C3717  
   }  
  
   // remove definition for event1 and substitute following declaration  
   // __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {  
   }  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
  
int main() {  
}  
```