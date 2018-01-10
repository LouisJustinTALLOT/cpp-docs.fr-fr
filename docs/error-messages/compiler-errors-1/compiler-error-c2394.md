---
title: Erreur du compilateur C2394 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2394
dev_langs: C++
helpviewer_keywords: C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d9cdfb2ace09bfc3aae4fa4afabd0d45117a80a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2394"></a>Erreur du compilateur C2394
'your_type::operator ' op » : CLR ou WinRToperator non valide. Au moins l'un des paramètres doit avoir les types suivants : 'T^', 'T^%', 'T^&', où T = 'your_type'  
  
 Un opérateur dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type de la valeur de retour de l'opérateur.  
  
 L'exemple suivant génère l'erreur C2394 :  
  
```  
// C2394.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y^ operator -(int i, char c);   // C2394  
  
   // OK  
   static Y^ operator -(Y^ hY, char c);  
   // or  
   static Y^ operator -(int i, Y^& rhY);  
};  
```