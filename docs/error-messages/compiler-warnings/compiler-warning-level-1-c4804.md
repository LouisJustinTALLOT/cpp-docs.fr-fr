---
title: Compilateur avertissement (niveau 1) C4804 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677899230b2475c80f9bdd461a0c79740c4d3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286979"
---
# <a name="compiler-warning-level-1-c4804"></a>Avertissement du compilateur (niveau 1) C4804
'opération' : utilisation risquée du type 'bool' dans l’opération  
  
 Cet avertissement se produit lorsque vous utilisez un `bool` variable ou une valeur de manière inattendue. Par exemple, C4804 est généré, si vous utilisez des opérateurs tels que l’opérateur unaire négatif (**-**) ou l’opérateur de complément (`~`). Le compilateur évalue l’expression.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4804 :  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```