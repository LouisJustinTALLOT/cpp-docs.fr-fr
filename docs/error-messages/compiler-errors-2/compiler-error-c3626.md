---
title: Erreur du compilateur C3626 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3626
dev_langs:
- C++
helpviewer_keywords:
- C3626
ms.assetid: 43926e2b-1ba9-4a43-9343-c58449cbb336
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ede2ec42b3afc581126d2591cba072817dcc8748
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266166"
---
# <a name="compiler-error-c3626"></a>Erreur du compilateur C3626
'mot clé' : mot clé '__event' peut uniquement être utilisé sur les interfaces COM, les fonctions membres et les membres de données qui sont des pointeurs vers les délégués  
  
 Un mot clé a été utilisé incorrectement.  
  
 L’exemple suivant génère l’erreur C3626 :  
  
```  
// C3626.cpp  
// compile with: /c  
struct A {  
   __event int i;   // C3626  
// try the following line instead  
// __event int i();  
};  
```