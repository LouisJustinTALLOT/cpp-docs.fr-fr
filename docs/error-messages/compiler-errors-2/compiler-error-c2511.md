---
title: Erreur du compilateur C2511 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2511
dev_langs:
- C++
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d97cbbd75d3b39b55ff640ed99e261ba349043d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199626"
---
# <a name="compiler-error-c2511"></a>Erreur du compilateur C2511
'identificateur' : la fonction membre introuvable dans 'classe' surchargée  
  
 Aucune version de la fonction n’est déclarée avec les paramètres spécifiés.  Causes possibles :  
  
1.  Paramètres incorrects passés à la fonction.  
  
2.  Paramètres passés dans un ordre incorrect.  
  
3.  Orthographe incorrecte des noms de paramètre.  
  
 L’exemple suivant génère l’erreur C2511 :  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```