---
title: Erreur du compilateur C2628 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2628
dev_langs:
- C++
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3f9813f103f59e61093ab82366e50a7ef6dae46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230230"
---
# <a name="compiler-error-c2628"></a>Erreur du compilateur C2628
'type1' suivi de 'type2' est non conforme (n’auriez-vous pas oublié un ';' ?)  
  
 Un point-virgule est peut-être manquant.  
  
 L’exemple suivant génère l’erreur C2628 :  
  
```  
// C2628.cpp  
class CMyClass {}  
int main(){}   // C2628 error  
```  
  
 Solution possible :  
  
```  
// C2628b.cpp  
class CMyClass {};  
int main(){}  
```