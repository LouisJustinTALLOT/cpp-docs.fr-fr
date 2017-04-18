---
title: Erreur du compilateur C3283 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3283
dev_langs:
- C++
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 19cb583eedb95295ed2a2bc33d4d390e4cd3cf79
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3283"></a>Erreur du compilateur C3283
'type' : une interface ne peut pas avoir de constructeur d’instance  
  
 Un type CLR [interface](../../windows/interface-class-cpp-component-extensions.md) ne peut pas avoir un constructeur d’instance.  Un constructeur statique est autorisé.  
  
 L’exemple suivant génère l’erreur C3283 :  
  
```  
// C3283.cpp  
// compile with: /clr  
interface class I {  
   I();   // C3283  
};  
```  
  
 Résolution possible :  
  
```  
// C3283b.cpp  
// compile with: /clr /c  
interface class I {  
   static I(){}  
};  
```
