---
title: Erreur du compilateur C2805 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2805
dev_langs:
- C++
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17885edc9cc508455cf780c7089f6ba3f9c793d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237555"
---
# <a name="compiler-error-c2805"></a>Erreur du compilateur C2805
opérateur binaire 'operator opérateur' a trop peu de paramètres  
  
 L’opérateur binaire n’a aucun paramètre.  
  
 L’exemple suivant génère l’erreur C2805 :  
  
```  
// C2805.cpp  
// compile with: /c  
class X {  
public:  
   X operator< ( void );   // C2805 must take one parameter  
   X operator< ( X );   // OK  
};  
```