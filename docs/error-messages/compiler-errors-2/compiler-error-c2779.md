---
title: Erreur du compilateur C2779 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2779
dev_langs:
- C++
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1f16bd0e756895b0da98fd43d0d6b2fdee6e8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233926"
---
# <a name="compiler-error-c2779"></a>Erreur du compilateur C2779
'déclaration' : méthodes de propriété peuvent uniquement être associés à des données membres non static  
  
 Le `property` attribut étendu est appliqué correctement à une donnée membre statique.  
  
 L’exemple suivant génère l’erreur C2779 :  
  
```  
// C2779.cpp  
struct A {  
   static __declspec(property(put=PutProp))  
   // try the following line instead  
   __declspec(property(put=PutProp))  
      int prop;   // C2779  
   int PutProp(void);  
};  
```