---
title: friend (C++)
ms.date: 11/19/2018
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 769720877cc58de530791b268811d7d01adad3e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154483"
---
# <a name="friend-c"></a>friend (C++)

Dans certaines circonstances, il est plus pratique d’accorder l’accès au niveau du membre à des fonctions qui ne sont pas membres d’une classe ou à tous les membres dans une classe distincte. Seul l'implémenteur de classe peut déclarer qui sont ses fonctions friend. Une fonction ou une classe ne peut pas se déclarer elle-même en tant que fonction ou classe friend d'une classe. Dans une définition de classe, utilisez le **friend** mot clé et le nom d’une fonction non membre ou autre classe pour lui accorder l’accès aux membres privés et protégés de votre classe. Dans une définition de modèle, un paramètre de type peut être déclaré en tant qu’ami.

## <a name="syntax"></a>Syntaxe

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Déclarations friend

Si vous déclarez une fonction friend qui n'a pas été déclarée précédemment, cette fonction est exportée vers la portée englobante sans classe.

Les fonctions déclarées dans une déclaration friend sont traitées comme si elles avaient été déclarées à l’aide de la **extern** mot clé. Pour plus d’informations, consultez [extern](extern-cpp.md).

Bien que les fonctions avec une portée globale puissent être déclarées comme friends avant leurs prototypes, les fonctions membres ne peuvent pas être déclarées comme friends avant l'apparition de leur déclaration de classe complète. L'exemple de code suivant montre pourquoi cette opération échoue :

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

L'exemple précédent entre le nom de classe `ForwardDeclared` dans la portée, mais la déclaration complète (plus spécifiquement, la partie qui déclare la fonction `IsAFriend`) n'est pas connue. Par conséquent, le **friend** déclaration de classe `HasFriends` génère une erreur.

À compter de C ++ 11, il existe deux formes de déclarations friend d’une classe :

```cpp
friend class F;
friend F;
```

La première forme introduit une nouvelle classe F si aucune classe existante portant ce nom a été trouvée dans l’espace de noms plus profond. **C ++ 11**: La deuxième forme n’introduit pas une nouvelle classe ; Il peut être utilisé lors de la classe a déjà été déclarée, et il doit être utilisé lors de la déclaration d’un paramètre de type de modèle ou un typedef comme friend.

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

Dans l’exemple suivant, `friend F` fait référence à la `F` classe est déclarée en dehors de l’étendue de NS.

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

Utilisez `friend F` pour déclarer un paramètre de modèle en tant qu’ami :

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Utilisez `friend F` pour déclarer un typedef en tant que friend :

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
>  Bien que la deuxième classe entière doive être friend de la première classe, vous pouvez sélectionner les fonctions de la première classe qui sont friends de la deuxième classe.

## <a name="friend-functions"></a>friend (fonctions)

Un **friend** fonction est une fonction qui n’est pas un membre d’une classe mais a accès aux membres privés et protégés de la classe. Les fonctions friend ne sont pas considérées comme des membres de classe ; ce sont des fonctions externes normales pour lesquelles des privilèges d'accès spéciaux sont accordés. Fonctions friend ne sont pas dans la portée de la classe, et elles ne sont pas appelées via des opérateurs de sélection de membres (**.** et -**>**), sauf si elles sont membres d’une autre classe. Un **friend** fonction est déclarée par la classe qui accorde l’accès. Le **friend** déclaration peut être placée n’importe où dans la déclaration de classe. Elle n'est pas affectée par les mots clés de contrôle d'accès.

L'exemple suivant présente une classe `Point` et une fonction friend, `ChangePrivate`. Le **friend** fonction a accès aux données membres privées de le `Point` de l’objet qu’il reçoit en tant que paramètre.

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

Les fonctions membres de classe peuvent être déclarées en tant que Friends dans d'autres classes. Prenons l'exemple suivant :

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

Dans l'exemple précédent, seule la fonction `A::Func1( B& )` se voit octroyer un accès ami à la classe `B`. Par conséquent, accéder au membre privé `_b` est correct dans `Func1` de classe `A` , mais pas dans `Func2`.

Une classe `friend` est une classe dont toutes les fonctions membres sont des fonctions friend d'une classe. Autrement dit, les fonctions membres ont accès aux membres privés et protégés de l'autre classe. Supposez que la déclaration `friend` dans la classe `B` ait été :

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

Un type managé ne peut pas avoir de fonctions, de classes ou d'interfaces friend.

L'amitié n'est pas héritée, ce qui signifie que les classes dérivées de `YourOtherClass` ne peuvent pas accéder aux membres privés de `YourClass`. L'amitié n'est pas transitive, par conséquent les classes qui sont des amis de `YourOtherClass` ne peuvent pas accéder aux membres privés de `YourClass`.

L'illustration suivante montre quatre déclarations de classe : `Base`, `Derived`, `aFriend` et `anotherFriend`. Seule la classe `aFriend` a un accès direct aux membres privés de `Base` (et à tous les membres dont `Base` peut avoir hérité).

![Implications des relations d’amitié](../cpp/media/vc38v41.gif "Implications des relations d’amitié") <br/>
Implications des relations d'amitié

## <a name="inline-friend-definitions"></a>Définitions de friends inline

Les fonctions friend peuvent être définies dans les déclarations de classe. Ce sont des fonctions inline, et à l'instar des fonctions inline membres, elles se comportent comme si elles étaient définies immédiatement après la détection de tous les membres de classe mais avant la fermeture de la portée de classe (qui marque la fin de la déclaration de classe).

Les fonctions friend définies dans les déclarations de classe ne sont pas prises en compte dans la portée de la classe englobante ; elles sont dans la portée du fichier.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)