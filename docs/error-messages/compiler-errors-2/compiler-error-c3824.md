---
title: Erreur du compilateur C3824 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e5202ff0236fca8d14c87bd55f1d314baa6bb2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268890"
---
# <a name="compiler-error-c3824"></a>Erreur du compilateur C3824
'membre' : ce type ne peut pas apparaître dans ce contexte (paramètre de fonction, type de retour ou un membre statique)  
  
 Pointeurs épingle ne peuvent pas être des paramètres de fonction, types de retour, ou déclaré `static`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3824 :  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
