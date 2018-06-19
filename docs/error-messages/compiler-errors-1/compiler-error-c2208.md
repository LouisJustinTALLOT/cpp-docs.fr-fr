---
title: Erreur du compilateur C2208 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2208
dev_langs:
- C++
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24377d17735fc63e9dc0541dfd9fb432eb0e0cda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172107"
---
# <a name="compiler-error-c2208"></a>Erreur du compilateur C2208
'type' : aucun membre défini à l’aide de ce type  
  
 Un identificateur résolu en un nom de type est dans une déclaration globale, mais le compilateur ne peut pas déclarer un membre.  
  
 L’exemple suivant génère l’erreur C2208 :  
  
```  
// C2208.cpp  
class C {  
   C;   // C2208  
   C(){}   // OK  
};  
```