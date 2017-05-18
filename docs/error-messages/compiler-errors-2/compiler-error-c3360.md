---
title: Erreur du compilateur C3360 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3360
dev_langs:
- C++
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
caps.latest.revision: 7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: eea16e1458cd77080790730c6ccb2b9bfa48fdd9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3360"></a>Erreur du compilateur C3360
'string' : Impossible de créer le nom  
  
 La valeur qui a été passée à le [uuid](../../windows/uuid-cpp-attributes.md) attribut n’était pas valide.  
  
 L’exemple suivant génère l’erreur C3360 :  
  
```  
// C3360.cpp  
[ uuid("1") ]  
// try this line instead  
// [ uuid("12341234-1234-1234-1234-123412341234") ]  
struct A   // C3360  
{  
};  
  
int main()  
{  
}  
```
