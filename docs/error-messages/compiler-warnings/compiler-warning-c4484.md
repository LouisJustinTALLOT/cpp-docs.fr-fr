---
title: Avertissement du compilateur C4484 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75531c207f0136f16109b4d69d689b883998aae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274753"
---
# <a name="compiler-warning-c4484"></a>Avertissement du compilateur C4484
'fonction_substitution' : correspond à la méthode de classe ref de base 'fonction_classe_base', mais n’est pas marqué comme 'virtual', 'new' ou 'override' ; 'new' (et non 'virtual') sont supposé.  
  
 Lors de la compilation avec **/CLR**, le compilateur ne substitue pas implicitement une fonction de classe de base, ce qui signifie que la fonction aura un nouvel emplacement dans vtable. Pour résoudre, spécifiez explicitement si une fonction est un remplacement.  
  
 Pour plus d'informations, voir :  
  
-   [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [New (nouvel emplacement dans vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484 est toujours émis en tant qu’erreur. Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer l’erreur C4484.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4484.  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```