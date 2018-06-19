---
title: Compilateur avertissement (niveau 1) C4683 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418bf25d565c616d5bc4aaf58361c4f28df298ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285341"
---
# <a name="compiler-warning-level-1-c4683"></a>Avertissement du compilateur (niveau 1) C4683
**'**   
 ***fonction* ' : source de l’événement a un paramètre 'out'-paramètre ; faites attention lorsque vous raccordez plusieurs gestionnaires d’événements**  
  
 Si plus d’un récepteur d’événements est à l’écoute à une source d’événements COM, la valeur d’un paramètre de sortie peut être ignorée.  
  
 Sachez qu’une fuite de mémoire se produit dans la situation suivante :  
  
1.  Si une méthode a un paramètre de sortie qui est affecté en interne, par exemple un BSTR *.  
  
2.  Si l’événement a plusieurs gestionnaires (est un événement multidiffusion)  
  
 La raison de la fuite de mémoire est que le paramètre de sortie sera défini par plusieurs gestionnaire, mais retourné sur le site d’appel par le dernier gestionnaire uniquement.  
  
 L’exemple suivant génère l’erreur C4683 :  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```