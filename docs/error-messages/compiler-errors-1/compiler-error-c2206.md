---
title: Erreur du compilateur C2206 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2206
dev_langs:
- C++
helpviewer_keywords:
- C2206
ms.assetid: d7fba68b-aa28-4885-a9a0-27107358f066
caps.latest.revision: 8
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
ms.openlocfilehash: 30d83f6cb4547e646a7d6f02a757d07252d715fa
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2206"></a>Erreur du compilateur C2206
'fonction' : typedef ne peut pas être utilisé pour la définition d’une fonction  
  
 Un `typedef` est utilisé pour définir un type de fonction.  
  
 L’exemple suivant génère l’erreur C2206 :  
  
```  
// C2206.cpp  
typedef int functyp();  
typedef int MyInt;  
functyp func1 {};   // C2206  
int main() {  
   MyInt i = 0;   // OK  
}  
```
