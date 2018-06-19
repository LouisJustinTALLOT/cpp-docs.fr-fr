---
title: Erreur du compilateur C3269 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3269
dev_langs:
- C++
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98e4e2a2df4271a3a0213b8abedc385f22c871aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249740"
---
# <a name="compiler-error-c3269"></a>Erreur du compilateur C3269
'fonction' : une fonction membre de géré ou WinRTtype ne peut pas être déclarée avec '...'  
  
Les fonctions membres de classe managée ou WinRT ne peuvent pas déclarer des listes de paramètres de longueur variable.  
  
L'exemple suivant génère l'erreur C3269 et montre comment la corriger :  
  
```  
// C3269_2.cpp  
// compile with: /clr  
  
ref struct A  
{  
   void func(int i, ...)   // C3269  
   // try the following line instead  
   // void func(int i )  
   {  
   }  
};  
  
int main()  
{  
}  
```  
