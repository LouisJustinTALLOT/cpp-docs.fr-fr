---
title: Erreur du compilateur C3153 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3153
dev_langs:
- C++
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c9829313947c7d3e954ddfd309f47d571ae2639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246070"
---
# <a name="compiler-error-c3153"></a>Erreur du compilateur C3153
'interface' : vous ne pouvez pas créer une instance d’une interface  
  
 Une interface ne peut pas être instanciée. Pour utiliser les membres d’une interface, dérivez une classe de l’interface, implémentez les membres d’interface et ensuite utiliser les membres.  
  
 L’exemple suivant génère l’erreur C3153 :  
  
```  
// C3153.cpp  
// compile with: /clr  
interface class A {  
};  
  
int main() {  
   A^ a = gcnew A;   // C3153  
}  
```  
