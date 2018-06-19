---
title: Erreur du compilateur C2063 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2063
dev_langs:
- C++
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dee835df0c30501c0b9a31fd542e51c498ae28d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163736"
---
# <a name="compiler-error-c2063"></a>Erreur du compilateur C2063
'identifier' : n’est pas une fonction  
  
 L’identificateur est utilisé comme fonction mais il n’est pas déclaré en tant que fonction.  
  
 L’exemple suivant génère l’erreur C2063 :  
  
```  
// C2063.c  
int main() {  
   int i, j;  
   j = i();    // C2063, i is not a function  
}  
```  
  
 Solution possible :  
  
```  
// C2063b.c  
int i() { return 0;}  
int main() {  
   int j;  
   j = i();  
}  
```