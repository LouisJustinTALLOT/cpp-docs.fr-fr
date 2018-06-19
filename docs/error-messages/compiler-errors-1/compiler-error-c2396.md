---
title: Erreur du compilateur C2396 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd9007d15cb5b6f9badf8f0962c8c1aa29df5bf7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197453"
---
# <a name="compiler-error-c2396"></a>Erreur du compilateur C2396
' your_type::operator '' : functionnot de conversion définie par l’utilisateur CLR ou WinRT valide. La conversion doit être opérée depuis ou vers : 'T^', 'T^%', 'T^&', où T = 'your_type'  
  
 Une fonction de conversion dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type qui contient la fonction de conversion.  
  
 L'exemple suivant génère l'erreur C2396 et montre comment la corriger :  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```