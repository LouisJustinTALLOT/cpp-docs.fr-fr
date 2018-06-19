---
title: Erreur du compilateur C3764 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3764
dev_langs:
- C++
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c214fcf40f442c35d754db64c8443c328d50ae10
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273626"
---
# <a name="compiler-error-c3764"></a>Erreur du compilateur C3764
'fonction_substitution' : ne peut pas substituer la méthode de classe de base 'fonction_classe_base'  
  
 Le compilateur a détecté une substitution incorrecte. Par exemple, la fonction de la classe de base n’était pas `virtual`. Pour plus d’informations, consultez [remplacer](../../windows/override-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3764.  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## <a name="example"></a>Exemple  
 C3764 peut également se produire lorsqu’une méthode de classe de base est explicitement et nommée substituée. L’exemple suivant génère C3764.  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```