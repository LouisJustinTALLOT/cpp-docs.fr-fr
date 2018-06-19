---
title: Erreur du compilateur C2082 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2082
dev_langs:
- C++
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbaa7f59b8853dd1b1ad0f2e839b00086db8eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172048"
---
# <a name="compiler-error-c2082"></a>Erreur du compilateur C2082
redéfinition du paramètre formel 'identifier'  
  
 Un paramètre formel d’une fonction est redéclaré dans le corps de la fonction. Pour corriger l’erreur, supprimez la redéfinition.  
  
 L’exemple suivant génère l’erreur C2082 :  
  
```  
// C2082.cpp  
void func(int i) {  
   int i;   // C2082  
   int ii;   // OK  
}  
```