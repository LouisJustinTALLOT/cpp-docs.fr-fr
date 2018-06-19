---
title: Erreur du compilateur C2529 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2529
dev_langs:
- C++
helpviewer_keywords:
- C2529
ms.assetid: 73a99e55-b91e-488d-9b72-cc80faaeb436
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb2d5de2375a243250b320ac313de4129795eb32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199753"
---
# <a name="compiler-error-c2529"></a>Erreur du compilateur C2529
'nom' : référence à une référence non conforme  
  
 Cette erreur peut être corrigée en utilisant la syntaxe de pointeur et de déclaration d’une référence à un pointeur.  
  
 L’exemple suivant génère l’erreur C2529 :  
  
```  
// C2529.cpp  
// compile with: /c  
int i;  
int &ri = i;  
int &(&rri) = ri;   // C2529  
```