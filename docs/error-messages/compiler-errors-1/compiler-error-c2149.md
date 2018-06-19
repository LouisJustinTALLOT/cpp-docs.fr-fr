---
title: Erreur du compilateur C2149 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2149
dev_langs:
- C++
helpviewer_keywords:
- C2149
ms.assetid: 7a106dab-d79f-41b9-85be-f36e86e4d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e02d69aa89c77c72685ef0db3125dab2cbf1898b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167822"
---
# <a name="compiler-error-c2149"></a>Erreur du compilateur C2149
'identificateur' : un champ de bits nommé ne peut pas avoir une largeur égale à zéro  
  
 Les champs de bits ne peuvent avoir une largeur égale à zéro que s’ils ne portent pas de nom.  
  
 L’exemple suivant génère l’erreur C2149 :  
  
```  
// C2149.cpp  
// compile with: /c  
struct C {  
   int i : 0;   // C2149  
   int j : 2;   // OK  
};  
```