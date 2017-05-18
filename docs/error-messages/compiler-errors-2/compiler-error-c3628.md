---
title: Erreur du compilateur C3628 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: e8723f85289d1094a6969d2bf26c30a85ccf382b
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3628"></a>Erreur du compilateur C3628
'base' classe' : gérés ou WinRTclasses prennent uniquement en charge l’héritage public  
  
Une tentative a été effectuée pour utiliser géré ou WinRT classe en tant qu’un [privé](../../cpp/private-cpp.md) ou [protégé](../../cpp/protected-cpp.md) classe de base. Managé ou WinRT classe peut uniquement être utilisée comme classe de base avec [public](../../cpp/public-cpp.md) accès.  
  
L'exemple suivant génère l'erreur C3628 et montre comment la corriger :  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  

