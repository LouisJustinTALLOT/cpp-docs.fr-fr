---
title: Erreur du compilateur C2186 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2186
dev_langs:
- C++
helpviewer_keywords:
- C2186
ms.assetid: 284bfb7e-ab85-4fcb-9864-1ddf7f6c94ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f497cfcf0849ff5ffc46d8c9a1c8b6e1c8ceafb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167627"
---
# <a name="compiler-error-c2186"></a>Erreur du compilateur C2186
'operator' : opérande de type 'void' non conforme  
  
 L’opérateur a un opérande `void` .  
  
 L’exemple suivant génère l’erreur C2186 :  
  
```  
// C2186.cpp  
// compile with: /c  
void func1( void );  
int  func2( void );  
int i = 2 + func1();   // C2186 func1() is type void  
int j = 2 + func2();   // OK both operands are type int  
```