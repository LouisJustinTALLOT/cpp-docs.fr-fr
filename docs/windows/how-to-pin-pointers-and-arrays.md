---
title: "Comment : épingler des pointeurs et des tableaux | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68824b9fcdf2f4de47900d5b0c4b03db9e28d9fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-pin-pointers-and-arrays"></a>Comment : épingler des pointeurs et des tableaux
Épingler un sous-objet défini dans un objet managé a pour effet d’épinglage de l’objet entier.  Par exemple, si un élément d’un tableau est épinglé, la totalité du tableau est épinglé également. Il n’existe aucune extension à la langue pour déclarer un tableau épinglé. Pour épingler un tableau, déclarez un pointeur épingle à son type d’élément et épingler un de ses éléments.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
++  
```  
  
## <a name="see-also"></a>Voir aussi  
 [pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)