---
title: "C3246 d’erreur du compilateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3246
dev_langs:
- C++
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
caps.latest.revision: 10
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ac8458487d9ed500420f2e687f8eb7c37bf053da
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3246"></a>Erreur du compilateur C3246
'classe' : ne peut pas hériter de 'type', car il a été déclaré comme 'sealed'  
  
Une classe qui est marquée en tant que [scellé](../../windows/sealed-cpp-component-extensions.md) ne peut pas être la classe de base pour toutes les autres classes.  
  
L’exemple suivant génère l’erreur C3246 :  
  
```  
// C3246_2.cpp  
// compile with: /clr /LD  
ref class X sealed {};  
  
ref class Y : public X {}; // C3246  
```  

