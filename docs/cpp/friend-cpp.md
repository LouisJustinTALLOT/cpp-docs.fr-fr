---
description: 'En savoir plus sur : Friend (C++)'
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 6e25beb10a727d0dcefce15e96059b49c5661601
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337737"
---
# <a name="friend-c"></a>friend (C++)

Dans certains cas, il est plus pratique d’accorder un accès au niveau du membre aux fonctions qui ne sont pas membres d’une classe ou à tous les membres d’une classe distincte. Seul l'implémenteur de classe peut déclarer qui sont ses fonctions friend. Une fonction ou une classe ne peut pas se déclarer elle-même en tant que fonction ou classe friend d'une classe. Dans une définition de classe, utilisez le **`friend`** mot clé et le nom d’une fonction non membre ou d’une autre classe pour lui accorder l’accès aux membres privés et protégés de votre classe. Dans une définition de modèle, un paramètre de type peut être déclaré comme Friend.

## <a name="syntax"></a>Syntaxe

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Déclarations friend

Si vous déclarez une fonction friend qui n'a pas été déclarée précédemment, cette fonction est exportée vers la portée englobante sans classe.

Les fonctions déclarées dans une déclaration Friend sont traitées comme si elles avaient été déclarées à l’aide du **`extern`** mot clé. Pour plus d’informations, consultez [extern](extern-cpp.md).

Bien que les fonctions avec une portée globale puissent être déclarées comme friends avant leurs prototypes, les fonctions membres ne peuvent pas être déclarées comme friends avant l'apparition de leur déclaration de classe complète. L'exemple de code suivant montre pourquoi cette opération échoue :

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

L'exemple précédent entre le nom de classe `ForwardDeclared` dans la portée, mais la déclaration complète (plus spécifiquement, la partie qui déclare la fonction `IsAFriend`) n'est pas connue. Par conséquent, la **`friend`** déclaration dans la classe `HasFriends` génère une erreur.

À partir de C++ 11, il existe deux formes de déclarations Friend pour une classe :

```cpp
friend class F;
friend F;
```

La première forme introduit une nouvelle classe F Si aucune classe existante portant ce nom n’a été trouvée dans l’espace de noms le plus profond. **C++ 11**: le deuxième formulaire n’introduit pas de nouvelle classe ; elle peut être utilisée lorsque la classe a déjà été déclarée, et elle doit être utilisée lors de la déclaration d’un paramètre de type de modèle ou d’un typedef comme Friend.

Utilisez `class friend F` lorsque le type référencé n’a pas encore été déclaré :

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

Dans l’exemple suivant, `friend F` fait référence à la `F` classe déclarée en dehors de la portée de NS.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Utilisez `friend F` pour déclarer un paramètre de modèle en tant que Friend :

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Utilisez `friend F` pour déclarer un typedef comme Friend :

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Pour déclarer deux classes qui sont friends l'une de l'autre, la deuxième classe entière doit être spécifiée comme friend de la première classe. La raison de cette restriction est que le compilateur a suffisamment d'informations pour déclarer les fonctions friend uniquement au point où la deuxième classe est déclarée.

> [!NOTE]
> Bien que la deuxième classe entière doive être friend de la première classe, vous pouvez sélectionner les fonctions de la première classe qui sont friends de la deuxième classe.

## <a name="friend-functions"></a>friend (fonctions)

Une **`friend`** fonction est une fonction qui n’est pas membre d’une classe, mais qui a accès aux membres privés et protégés de la classe. Les fonctions friend ne sont pas considérées comme des membres de classe ; ce sont des fonctions externes normales pour lesquelles des privilèges d'accès spéciaux sont accordés. Les amis ne sont pas dans la portée de la classe et ne sont pas appelés à l’aide des opérateurs de sélection de membres (**.** et- **>** ) sauf s’ils sont membres d’une autre classe. Une **`friend`** fonction est déclarée par la classe qui accorde l’accès. La **`friend`** déclaration peut être placée n’importe où dans la déclaration de classe. Elle n'est pas affectée par les mots clés de contrôle d'accès.

L'exemple suivant présente une classe `Point` et une fonction friend, `ChangePrivate`. La **`friend`** fonction a accès aux données membres privées de l' `Point` objet qu’elle reçoit en tant que paramètre.

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>Membres de classes en tant que friends

Les fonctions membres de classe peuvent être déclarées en tant que Friends dans d'autres classes. Prenons l’exemple suivant :

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

Dans l'exemple précédent, seule la fonction `A::Func1( B& )` se voit octroyer un accès ami à la classe `B`. Par conséquent, l’accès au membre privé `_b` est correct dans `Func1` de la classe, `A` mais pas dans `Func2` .

Une **`friend`** classe est une classe dont toutes les fonctions membres sont des fonctions Friend d’une classe, c’est-à-dire dont les fonctions membres ont accès aux membres privés et protégés de l’autre classe. Supposons que la **`friend`** déclaration dans la classe `B` avait été :

```cpp
friend class A;
```

Dans ce cas, toutes les fonctions membres dans la classe `A` auraient bénéficié d'un accès ami à la classe `B`. Le code suivant est un exemple d'une classe Friend :

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

L'amitié n'est pas mutuelle à moins qu'elle soit spécifiée explicitement comme telle. Dans l'exemple ci-dessus, les fonctions membres de `YourClass` ne peuvent pas accéder aux membres privés de `YourOtherClass`.

Un type managé (en C++/CLI) ne peut pas avoir de fonctions Friend, de classes Friend ou d’interfaces Friend.

L'amitié n'est pas héritée, ce qui signifie que les classes dérivées de `YourOtherClass` ne peuvent pas accéder aux membres privés de `YourClass`. L'amitié n'est pas transitive, par conséquent les classes qui sont des amis de `YourOtherClass` ne peuvent pas accéder aux membres privés de `YourClass`.

L'illustration suivante montre quatre déclarations de classe : `Base`, `Derived`, `aFriend` et `anotherFriend`. Seule la classe `aFriend` a un accès direct aux membres privés de `Base` (et à tous les membres dont `Base` peut avoir hérité).

![Implications des relations d'amitié](../cpp/media/vc38v41.gif "Implications des relations d'amitié") <br/>
Implications des relations d'amitié

## <a name="inline-friend-definitions"></a>Définitions de friends inline

Les fonctions Friend peuvent être définies (à partir d’un corps de fonction) dans les déclarations de classe. Ce sont des fonctions inline, et à l'instar des fonctions inline membres, elles se comportent comme si elles étaient définies immédiatement après la détection de tous les membres de classe mais avant la fermeture de la portée de classe (qui marque la fin de la déclaration de classe). Les fonctions Friend qui sont définies dans les déclarations de classe se trouvent dans la portée de la classe englobante.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
