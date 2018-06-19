---
title: Erreur du compilateur C2236 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2236
dev_langs:
- C++
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f755c9ba72e2d36bdce608e93e8a60175e493a45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170552"
---
# <a name="compiler-error-c2236"></a>Erreur du compilateur C2236
jeton 'identificateur' inattendu. N'auriez-vous pas oublié un ';' ?  
  
 L'identificateur est déjà défini comme un type et ne peut pas être remplacé par un type défini par l'utilisateur.  
  
 L'exemple suivant génère l'erreur C2236 :  
  
```  
// C2236.cpp  
// compile with: /c  
int class A {};  // C2236 "int class" is unexpected  
int i;  
class B {};  
```