---
title: Erreur du compilateur C2299 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e21213f08e25050932274a64d0ed56db96f2a453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170841"
---
# <a name="compiler-error-c2299"></a>Erreur du compilateur C2299
'fonction' : changement de comportement : une spécialisation explicite ne peut pas être un constructeur de copie ou un opérateur d’assignation de copie  
  
 Cette erreur peut également être due à la mise en conformité du compilateur pour Visual C++ 2005 : les versions précédentes de Visual C++ autorisaient les spécialisations explicites pour un constructeur de copie ou un opérateur d’assignation de copie.  
  
 Pour résoudre C2299, n’apportez pas le constructeur de copie ou opérateur d’assignation une fonction de modèle, mais plutôt une fonction sans modèle qui prend un type de classe. Tout code qui appelle le constructeur de copie ou un opérateur d’assignation en spécifiant explicitement les arguments template doit supprimer les arguments template.  
  
 L’exemple suivant génère l’erreur C2299 :  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```