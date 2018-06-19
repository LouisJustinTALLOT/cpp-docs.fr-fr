---
title: Erreur du compilateur C2951 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0883b0942fdfbe3d55a540fbed35a0affc73be5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241534"
---
# <a name="compiler-error-c2951"></a>Erreur du compilateur C2951
déclarations de type sont uniquement autorisées au niveau de l’espace de noms global, ou portée de classe  
  
 Vous ne pouvez pas déclarer un générique ou la classe de modèle à l’extérieur global ou la portée espace de noms. Si vous apportez vos déclarations générique ou de modèle dans un fichier include, assurez-vous que le fichier include est dans une portée globale.  
  
 L’exemple suivant génère l’erreur C2951 :  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 L’erreur C2951 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```