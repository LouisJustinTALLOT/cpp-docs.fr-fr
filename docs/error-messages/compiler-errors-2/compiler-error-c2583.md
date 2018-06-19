---
title: Erreur du compilateur C2583 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2583
dev_langs:
- C++
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae9ef120d3dba9bc3c337d02aac302fce85f3905
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228305"
---
# <a name="compiler-error-c2583"></a>Erreur du compilateur C2583
'identificateur' : ' const/volatile' pointeur 'this' est non conforme pour les constructeurs/destructeurs  
  
 Un constructeur ou un destructeur est déclaré `const` ou `volatile`. Cette opération n’est pas autorisée.  
  
 L’exemple suivant génère l’erreur C2583 :  
  
```  
// C2583.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
   A() const;   // C2583  
  
   // try the following line instead  
   // A();  
};  
```