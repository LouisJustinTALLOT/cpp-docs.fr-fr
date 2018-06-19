---
title: Erreur du compilateur C2130 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4484d183def04f764ae75faaa503449e7bdf9984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172074"
---
# <a name="compiler-error-c2130"></a>Erreur du compilateur C2130
\#ligne attendait une chaîne contenant le nom de fichier, a trouvé 'jeton'  
  
 Le jeton de nom de fichier facultatif [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` doit être une chaîne.  
  
 L’exemple suivant génère l’erreur C2130 :  
  
```  
// C2130.cpp  
int main() {  
   #line 1000 test   // C2130  
   #line 1000 "test"   // OK  
}  
```