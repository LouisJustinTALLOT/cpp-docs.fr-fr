---
title: Erreur du compilateur C2054 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2054
dev_langs:
- C++
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfb6d7bf69885d2ac5bf59947ea9f2f70c797003
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170373"
---
# <a name="compiler-error-c2054"></a>Erreur du compilateur C2054
attendu ' (' suivre 'identificateur'  
  
 L’identificateur de fonction est utilisée dans un contexte qui requiert des parenthèses fermantes.  
  
 Cette erreur peut résulter de l’omission d’un signe égal (=) dans une initialisation complexe.  
  
 L’exemple suivant génère l’erreur C2054 :  
  
```  
// C2054.c  
int array1[] { 1, 2, 3 };   // C2054, missing =  
```  
  
 Solution possible :  
  
```  
// C2054b.c  
int main() {  
   int array2[] = { 1, 2, 3 };  
}  
```