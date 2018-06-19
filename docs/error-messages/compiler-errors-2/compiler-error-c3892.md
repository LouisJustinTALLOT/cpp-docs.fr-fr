---
title: Erreur du compilateur C3892 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3892
dev_langs:
- C++
helpviewer_keywords:
- C3892
ms.assetid: 83fff42c-ea48-442f-bc2e-b33a6b99d890
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81e1613cb05fafe799b4eb4e09dc0a58016e0f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268812"
---
# <a name="compiler-error-c3892"></a>Erreur du compilateur C3892
'var' : vous ne pouvez pas attribuer à une variable const  
  
 Une variable const ne peut pas être modifiée une fois qu’il est déclaré et initialisé.  
  
 L’exemple suivant génère l’erreur C3892 :  
  
```  
// C3892.cpp  
// compile with: /clr  
ref struct Y1 {  
   static const int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3892  
}  
```