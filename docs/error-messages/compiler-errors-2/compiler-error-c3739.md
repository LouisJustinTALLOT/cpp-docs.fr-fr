---
title: Erreur du compilateur C3739 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3739
dev_langs:
- C++
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 283156f436695c011642dc2603d2cc846a449b3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264736"
---
# <a name="compiler-error-c3739"></a>Erreur du compilateur C3739
'classe' : syntaxe est uniquement pris en charge le paramètre 'layout_dependent' d’event_receiver a la valeur true  
  
 Vous avez essayé de raccorder une interface d’événements complète mais `layout_dependent` sur [event_receiver](../../windows/event-receiver.md) attribut n’est pas vrai ; vous devez raccorder un événement à la fois.  
  
 L’exemple suivant génère l’erreur C3739 :  
  
```  
// C3739.cpp  
struct A  
{  
   __event void e();  
};  
  
// event_receiver is implied  
// [ event_receiver(layout_dependent=false)]  
  
// use the following line instead  
// [event_receiver(com, layout_dependent=true), coclass ]  
struct B  
{  
   void f();  
   B(A* a)  
   {  
      __hook(A, a, &B::f);   // C3739  
      // use the following line instead to hook a single event  
      // __hook(&A::e, a, &B::f);  
   }  
};  
  
int main()  
{  
}  
```