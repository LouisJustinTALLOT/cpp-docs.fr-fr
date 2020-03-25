---
title: Erreur du compilateur C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: 843676638037aab9544f1fbd8c5c6d56d351e485
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206546"
---
# <a name="compiler-error-c2248"></a>Erreur du compilateur C2248

'*membre*' : impossible d’accéder au membre'*access_level*'déclaré dans la classe'*classe*'

Les membres d’une classe dérivée ne peuvent pas accéder `private` membres d’une classe de base. Vous ne pouvez pas accéder aux membres `private` ou `protected` des instances de classe.

## <a name="example"></a>Exemple

L’exemple suivant génère C2248 lorsque des membres privés ou protégés d’une classe sont accessibles à partir de l’extérieur de la classe. Pour résoudre ce problème, n’accédez pas à ces membres directement en dehors de la classe. Utilisez les données membres publiques et les fonctions membres pour interagir avec la classe.

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

Un autre problème de conformité qui expose C2248 est l’utilisation d’amis et de spécialisations de modèles. Pour résoudre ce problème, déclarez les fonctions de modèle Friend à l’aide d’une liste de paramètres de modèle vide < > ou des paramètres de modèle spécifiques.

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

Un autre problème de conformité qui expose C2248 est lorsque vous tentez de déclarer un Friend d’une classe et lorsque la classe n’est pas visible par la déclaration Friend dans l’étendue de la classe. Pour résoudre ce problème, accordez l’amitié à la classe englobante.

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
