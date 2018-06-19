---
title: Erreur du compilateur C3923 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3923
dev_langs:
- C++
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d93ff388ae4ba1a97f9a194df1ca1006e05eb51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275147"
---
# <a name="compiler-error-c3923"></a>Erreur du compilateur C3923
'membre' : les définitions de classes, de structures ou d'unions locales ne sont pas autorisées dans une fonction membre d'une classe managée ou WinRT  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C3923.  
  
```  
// C3923.cpp  
// compile with: /clr /c  
ref struct x {  
   void Test() {  
      struct a {};   // C3923  
      class b {};   // C3923  
      union c {};   // C3923  
   }  
};  
```