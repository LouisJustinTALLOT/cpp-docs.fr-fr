---
title: Erreur du compilateur C2739 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2739
dev_langs: C++
helpviewer_keywords: C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b6d2647fe6addc8f5c68ef70b91a244782f467a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2739"></a>Erreur du compilateur C2739
'nombre' : les dimensions de tableau managé ou WinRT explicites doivent être comprises entre 1 et 32  
  
 Une dimension de tableau n'était pas comprise entre 1 et 32.  
  
 L'exemple suivant génère l'erreur C2739 et montre comment la corriger :  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```