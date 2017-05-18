---
title: "Erreur irrécupérable C1020 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1020
dev_langs:
- C++
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 54108a74ac23d20480bfd61abcd7fb5b7c7b4694
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1020"></a>Erreur irrécupérable C1020
#endif inattendu  
  
 La directive `#endif` n’a aucune directive `#if`, `#ifdef`ou `#ifndef` correspondante. Vérifiez que chaque `#endif` a une directive correspondante.  
  
 L’exemple suivant génère l’erreur C1020 :  
  
```  
// C1020.cpp  
#endif     // C1020  
```  
  
 Solution possible :  
  
```  
// C1020b.cpp  
// compile with: /c  
#if 1  
#endif  
```
