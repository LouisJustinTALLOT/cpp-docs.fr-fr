---
title: Erreur du compilateur C3152 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3152
dev_langs:
- C++
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93d1d73a5ab48ed992edafd8f6fe845e7e0f1561
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249409"
---
# <a name="compiler-error-c3152"></a>Erreur du compilateur C3152
'construction' : 'mot clé' ne peut s'appliquer qu'à une classe, une structure ou une fonction membre virtuelle  
  
 Certains mots clés ne peuvent être appliqués qu'à une classe C++.  
  
 L'exemple suivant génère l'erreur C3152 et montre comment la corriger :  
  
```  
// C3152.cpp  
// compile with: /clr /c  
ref class C {  
   int (*pfn)() sealed;   // C3152  
   virtual int g() sealed;   // OK  
};  
```  
