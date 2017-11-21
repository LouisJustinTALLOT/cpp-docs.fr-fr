---
title: Compilateur avertissement (niveau 3) C4161 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4161
dev_langs: C++
helpviewer_keywords: C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a1a5ce118dc1c6a0de872ca851e59daa96f8b13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4161"></a>Avertissement du compilateur (niveau 3) C4161
\#pragma pragma(pop...) : plus de POP que de push  
  
 Étant donné que votre code source contient plus d’opérations pop que d’opérations push pour le pragma ***pragma***, la pile peut ne pas fonctionner comme prévu. Pour éviter cet avertissement, vérifiez que le nombre d’opérations pop ne dépasse pas le nombre d’opérations push.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4161 :  
  
```  
// C4161.cpp  
// compile with: /W3 /LD  
#pragma pack(push, id)  
#pragma pack(pop, id)  
#pragma pack(pop, id)   // C4161, an extra pop  
  
#pragma bss_seg(".my_data1")  
int j;  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;  
  
#pragma bss_seg(pop, stack1)  
int m;  
  
#pragma bss_seg(pop, stack1)   // C4161  
```