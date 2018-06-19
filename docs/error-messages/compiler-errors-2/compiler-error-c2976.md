---
title: Erreur du compilateur C2976 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2976
dev_langs:
- C++
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2ff5fd23d02e835cfaa36b96ce75a1c74d16bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244808"
---
# <a name="compiler-error-c2976"></a>Erreur du compilateur C2976
'identificateur' : les arguments de type insuffisants  
  
 Un générique ou modèle il manque un ou plusieurs arguments réels. Vérifiez la déclaration du générique ou du modèle pour connaître le nombre de paramètres approprié.  
  
 Cette erreur peut être dû à l’absence d’arguments template dans les composants de la bibliothèque C++ Standard.  
  
 L’exemple suivant génère l’erreur C2976 :  
  
```  
// C2976.cpp  
template <class T>   
struct TC {  
   T t;  
};  
int main() {  
   TC<>* t;   // C2976  
   TC<int>* t2;   // OK  
}  
```  
  
 L’erreur C2976 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C2976b.cpp  
// compile with: /clr  
generic <class T>  
ref struct GC {  
   T t;  
};  
  
int main() {  
   GC<>^ g;   // C2976  
   GC<int>^ g2;   // OK  
}  
```