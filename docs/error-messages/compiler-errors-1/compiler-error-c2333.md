---
title: Erreur du compilateur C2333 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2333
dev_langs:
- C++
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1613d560ef22c33ca1a19ac63584138a18c19c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195280"
---
# <a name="compiler-error-c2333"></a>Erreur du compilateur C2333
'fonction' : erreur dans la déclaration de fonction ; corps de la fonction ignoré  
  
 Cette erreur se produit après une autre erreur, pour les fonctions membres définies à l’intérieur de leur classe.  
  
 L’exemple suivant génère l’erreur C2333 :  
  
```  
// C2333.cpp  
struct s1 {  
   s1(s1) {}   // C2333  
};  
```