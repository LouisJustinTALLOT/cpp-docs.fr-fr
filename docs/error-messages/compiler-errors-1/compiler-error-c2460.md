---
title: Erreur du compilateur C2460 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4220be654f93ecd79d196efc14657ca7346411f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197778"
---
# <a name="compiler-error-c2460"></a>Erreur du compilateur C2460
'identificateur1' : utilise 'identificateur2', qui est défini  
  
 Une classe ou structure (`identifier2`) est déclarée en tant que membre de lui-même (`identifier1`). Les définitions de classes et structures récursives ne sont pas autorisées.  
  
 L’exemple suivant génère l’erreur C2460 :  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 Au lieu de cela, utilisez une référence de pointeur de la classe.  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```