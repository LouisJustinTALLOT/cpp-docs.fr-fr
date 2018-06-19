---
title: Erreur du compilateur C3672 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3672
dev_langs:
- C++
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aaea09d89c192a1820c2a384144ce758fde90476
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263945"
---
# <a name="compiler-error-c3672"></a>Erreur du compilateur C3672
l’expression pseudo-destructeur peut uniquement être utilisée dans le cadre d’un appel de fonction  
  
 Un destructeur a été appelé de façon incorrecte.  Pour plus d’informations, consultez [destructeurs](../../cpp/destructors-cpp.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3672.  
  
```  
// C3672.cpp  
template<typename T>  
void f(T* pT) {  
   &pT->T::~T;   // C3672  
   pT->T::~T();   // OK  
};  
  
int main() {  
   int i;  
   f(&i);  
}  
```