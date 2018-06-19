---
title: Erreur du compilateur C3156 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3156
dev_langs:
- C++
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9557043bac056435dd53b210359e7bb72b29b6d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248227"
---
# <a name="compiler-error-c3156"></a>Erreur du compilateur C3156
'classe' : vous ne pouvez pas avoir de définition locale d'un type managé ou WinRT  
  
 Une fonction ne peut pas contenir la définition, ou la déclaration, d'une classe, d'un struct ou d'une interface managé(e) ou WinRT.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C3156.  
  
```  
// C3156.cpp  
// compile with: /clr /c  
void f() {  
   ref class X {};   // C3156  
   ref class Y;   // C3156  
}  
```  
