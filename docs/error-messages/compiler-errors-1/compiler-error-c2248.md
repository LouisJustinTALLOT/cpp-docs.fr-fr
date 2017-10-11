---
title: Erreur du compilateur C2248 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2248
dev_langs:
- C++
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a6023532a7644753f1aaff957232fde70d01426f
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2248"></a>Erreur du compilateur C2248
'*membre*' : Impossible d’accéder à '*access_level*'membre déclaré dans la classe'*classe*'  
  
Membres d’une classe dérivée ne peut pas accéder aux `private` membres d’une classe de base. Vous ne pouvez pas accéder aux `private` ou `protected` membres d’instances de classe.  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant génère C2248 lorsque privé ou protégé des membres d’une classe sont accessibles à partir en dehors de la classe. Pour résoudre ce problème, n’accédez pas ces membres directement à l’extérieur de la classe. Utiliser les données membres publiques et les fonctions membres pour interagir avec la classe.  
  
```cpp  
// C2248_access.cpp 
// compile with: cl /EHsc /W4 C2248_access.cpp 
#include <stdio.h>  

class X {  
public:  
    int  m_publicMember;  
    void setPrivateMember( int i ) {  
        m_privateMember = i;  
        printf_s("\n%d", m_privateMember);  
    }  
protected:  
    int  m_protectedMember;  
  
private:  
    int  m_privateMember;  
} x;  
  
int main() {  
    x.m_publicMember = 4;  
    printf_s("\n%d", x.m_publicMember);  
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected  
    x.m_privateMember = 3;   // C2248  m_privMemb is private  
    x.setPrivateMember(0);   // OK uses public access function  
}  
```  
  
Un autre problème de conformité qui expose l’erreur C2248 est l’utilisation de friends de modèle et de spécialisation. Pour résoudre ce problème, déclarez friend fonctions de modèle à l’aide d’un <> de liste de paramètre de modèle vide ou de paramètres de modèle spécifique.  
  
```cpp  
// C2248_template.cpp 
// compile with: cl /EHsc /W4 C2248_template.cpp 
template<class T>  
void f(T t) {  
    t.i;   // C2248  
}  
  
struct S {  
private:  
    int i;  
  
public:  
    S() {}  
    friend void f(S);   // refer to the non-template function void f(S)  
    // To fix, comment out the previous line and
    // uncomment the following line.  
    // friend void f<S>(S);  
};  
  
int main() {  
    S s;  
    f<S>(s);  
}  
```  
  
Un autre problème de conformité qui expose l’erreur C2248 est lorsque vous tentez de déclarer une fonction friend d’une classe, et lorsque la classe n’est pas visible à la déclaration friend dans la portée de la classe. Pour résoudre ce problème, accordez l’amitié à la classe englobante.  
  
```cpp  
// C2248_enclose.cpp  
// compile with: cl /W4 /c C2248_enclose.cpp  
class T {  
    class S {  
        class E {};  
    };  
    friend class S::E;   // C2248  
};  
  
class A {  
    class S {  
        class E {};  
        friend class A;  // grant friendship to enclosing class  
    };  
    friend class S::E;   // OK  
};  
```
