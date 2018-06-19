---
title: Compilateur avertissement (niveau 3) C4686 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4686
dev_langs:
- C++
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1edbf438951644f63aae637a68f69d173ab7e1b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292777"
---
# <a name="compiler-warning-level-3-c4686"></a>Avertissement du compilateur (niveau 3) C4686
**'**   
 ***type défini par l’utilisateur* ' : changement de comportement possible, changement de retour UDT convention d’appel**  
  
 Une spécialisation de modèle de classe n’est définie avant d’être utilisé dans un type de retour. Tout ce qui instancie la classe résoudra C4686 ; déclaration d’une instance ou l’accès à un membre (C\<int > :: rien) sont également des options.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 Essayez la suivante :  
  
```  
// C4686.cpp  
// compile with: /W3  
#pragma warning (default : 4686)  
template <class T>  
class C;  
  
template <class T>  
C<T> f(T);  
  
template <class T>  
class C {};  
  
int main() {  
   f(1);   // C4686  
}  
  
template <class T>  
C<T> f(T) {  
   return C<int>();  
}  
```