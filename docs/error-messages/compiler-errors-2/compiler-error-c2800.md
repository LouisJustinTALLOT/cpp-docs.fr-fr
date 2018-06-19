---
title: Erreur du compilateur C2800 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd9723513042ae7ef6d63914f5abecd63192e37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235595"
---
# <a name="compiler-error-c2800"></a>Erreur du compilateur C2800
'operator opérateur' ne peut pas être surchargé.  
  
 Les opérateurs suivants ne peuvent pas être surchargés : accès au membre de classe (`.`), pointeur vers membre (`.*`), résolution de portée (`::`), expression conditionnelle (`? :`), et `sizeof`.  
  
 L’exemple suivant génère l’erreur C2800 :  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```