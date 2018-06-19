---
title: Erreur du compilateur C2137 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2137
dev_langs:
- C++
helpviewer_keywords:
- C2137
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1d546270b5f3edd71dbc0c68f2f40a6e7ba6343
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164383"
---
# <a name="compiler-error-c2137"></a>Erreur du compilateur C2137
constante caractère vide  
  
 La constante caractère vide (' ') n’est pas autorisée.  
  
 L’exemple suivant génère l’erreur C2137 :  
  
```  
// C2137.cpp  
int main() {  
   char c = '';   // C2137  
   char d = ' ';   // OK  
}  
```