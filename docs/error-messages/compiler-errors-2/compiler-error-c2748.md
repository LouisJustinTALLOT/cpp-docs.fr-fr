---
title: Erreur du compilateur C2748 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2748
dev_langs: C++
helpviewer_keywords: C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7db053bf9aef4db18b937292821c18d42508b881
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2748"></a>Erreur du compilateur C2748
La création de tableau managé ou WinRT doit posséder une taille de tableau ou un initialiseur de tableau  
  
 Un tableau managé ou WinRT était incorrect. Pour plus d'informations, consultez [tableau](../../windows/arrays-cpp-component-extensions.md).  
  
 L'exemple suivant génère l'erreur C2748 et montre comment la corriger :  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```