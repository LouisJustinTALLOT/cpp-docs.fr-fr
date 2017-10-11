---
title: Erreur du compilateur C3464 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3464
dev_langs:
- C++
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 69ddfd70c92c306a9e68d5eacc568b24b07c9745
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3464"></a>Erreur du compilateur C3464
'type' : impossible de transmettre un type imbriqué  
  
 Le transfert de type ne fonctionne pas sur les types imbriqués.  
  
 Pour plus d’informations, consultez [transfert de Type (C + c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un composant.  
  
```  
// C3464.cpp  
// compile with: /LD /clr  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3464.  
  
```  
// C3464_b.cpp  
// compile with: /clr /c  
#using "C3464.dll"  
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464  
[assembly:TypeForwardedTo(R::typeid)];   // OK  
```
