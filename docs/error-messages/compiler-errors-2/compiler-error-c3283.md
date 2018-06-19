---
title: Erreur du compilateur C3283 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3283
dev_langs:
- C++
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bc23270d70a2fec1c0ac9cc5f6b96541085cfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249098"
---
# <a name="compiler-error-c3283"></a>Erreur du compilateur C3283
'type' : une interface ne peut pas avoir de constructeur d’instance  
  
 Une [interface](../../windows/interface-class-cpp-component-extensions.md) CLR ne peut pas avoir de constructeur d’instance.  Un constructeur statique est autorisé.  
  
 L’exemple suivant génère l’erreur C3283 :  
  
```  
// C3283.cpp  
// compile with: /clr  
interface class I {  
   I();   // C3283  
};  
```  
  
 Solution possible :  
  
```  
// C3283b.cpp  
// compile with: /clr /c  
interface class I {  
   static I(){}  
};  
```