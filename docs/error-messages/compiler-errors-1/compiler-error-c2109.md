---
title: Erreur du compilateur C2109 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2109
dev_langs: C++
helpviewer_keywords: C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5e783c0a68effd6a2302939ccf8303d401e23d6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2109"></a>Erreur du compilateur C2109
indice requiert un type tableau ou pointeur  
  
 L’indice a été utilisé sur une variable qui n’est pas un tableau.  
  
 L’exemple suivant génère C2109 :  
  
```  
// C2109.cpp  
int main() {  
   int a, b[10] = {0};  
   a[0] = 1;   // C2109  
   b[0] = 1;   // OK  
}  
```