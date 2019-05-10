---
title: 'Déclarateur de référence rvalue : &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 663b639dbfecf9253547e1dd3b4e40480c27b470
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222046"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Déclarateur de référence rvalue : &amp;&amp;

Contient une référence à une expression rvalue.

## <a name="syntax"></a>Syntaxe

```
type-id && cast-expression
```

## <a name="remarks"></a>Notes

Les références rvalue vous permettent de différencier une lvalue d'une rvalue. Les références lvalue et rvalue sont syntaxiquement et sémantiquement semblables, mais elles suivent des règles quelque peu différentes. Pour plus d’informations sur les lvalues et rvalues, consultez [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Pour plus d’informations sur les références lvalue, consultez [déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md).

Les sections suivantes décrivent comment les références rvalue prennent en charge l’implémentation de *la sémantique de déplacement* et *un transfert parfait*.

## <a name="move-semantics"></a>Sémantique de déplacement

Références rvalue prennent en charge l’implémentation de *la sémantique de déplacement*, ce qui peut augmenter considérablement les performances de vos applications. La sémantique de déplacement vous permet d'écrire du code qui transfère des ressources (telles que la mémoire allouée de manière dynamique) d'un objet vers un autre. La sémantique de déplacement fonctionne car elle permet de transférer des ressources à partir d'objets temporaires qui ne peuvent pas être référencés ailleurs dans le programme.

Pour implémenter la sémantique de déplacement, vous fournissez généralement un *constructeur de déplacement,* et éventuellement un opérateur d’assignation déplacement (**opérateur =**), à votre classe. Les opérations de copie et d'assignation dont les sources sont des rvalues profitent ensuite automatiquement de la sémantique de déplacement. Contrairement au constructeur de copie par défaut, le compilateur ne fournit pas de constructeur de déplacement par défaut. Pour plus d’informations sur la façon d’écrire un constructeur de déplacement et comment l’utiliser dans votre application, consultez [constructeurs de déplacement et opérateurs d’assignation déplacer (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Vous pouvez aussi surcharger des fonctions et des opérateurs ordinaires pour tirer parti de la sémantique de déplacement. Visual Studio 2010 introduit la sémantique de déplacement dans le C++ bibliothèque Standard. Par exemple, la classe `string` implémente des opérations qui exécutent la sémantique de déplacement. Prenons l'exemple suivant qui concatène plusieurs chaînes et affiche le résultat :

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Avant Visual Studio 2010, chaque appel à **opérateur +** alloue et retourne un nouveau temporaire `string` objet (une rvalue). **operator +** Impossible d’ajouter une chaîne à l’autre, car il ne sait pas si les chaînes sources sont des lvalues ou rvalues. Si les chaînes sources sont toutes les deux des lvalues, elles peuvent être référencées ailleurs dans le programme et ne doivent donc pas être modifiées. À l’aide des références rvalue, **opérateur +** peut être modifiée pour accepter des rvalues, qui ne peut pas être référencées ailleurs dans le programme. Par conséquent, **opérateur +** peuvent maintenant ajouter une chaîne à un autre. Cela peut réduire considérablement le nombre d'allocations dynamiques de la mémoire que la classe `string` doit exécuter. Pour plus d’informations sur la `string` de classe, consultez [basic_string, classe](../standard-library/basic-string-class.md).

La sémantique de déplacement est également utile lorsque le compilateur ne peut pas utiliser l'optimisation de la valeur de retour (RVO) ou l'optimisation de la valeur de retour nommée (NRVO). Dans ces cas-là, le compilateur appelle le constructeur de déplacement si le type le définit. Pour plus d’informations sur l’optimisation de valeur de retour nommée, consultez [l’optimisation de la valeur de retour nommée dans Visual Studio 2005](https://msdn.microsoft.com/library/ms364057.aspx).

Pour mieux comprendre la sémantique de déplacement, prenez comme exemple l'insertion d'un élément dans un objet `vector`. Si la capacité de l'objet `vector` est dépassée, l'objet `vector` doit réallouer de la mémoire pour ses éléments puis copier chaque élément vers un autre emplacement de mémoire pour libérer de l'espace pour l'élément inséré. Lorsqu'une opération d'insertion copie un élément, elle crée un nouvel élément, appelle le constructeur de copie pour copier les données de l'élément précédent dans le nouvel élément, puis supprime l'élément précédent. La sémantique de déplacement vous permet de déplacer directement des objets sans qu'il soit nécessaire d'exécuter des opérations d'allocation de mémoire et de copie coûteuses.

Pour tirer parti de la sémantique de déplacement dans l'exemple `vector`, vous pouvez écrire un constructeur de déplacement pour déplacer des données d'un objet vers un autre.

Pour plus d’informations sur l’introduction de la sémantique de déplacement dans le C++ bibliothèque Standard dans Visual Studio 2010, consultez [ C++ bibliothèque Standard](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Transfert parfait

Le transfert parfait réduit le besoin en fonctions surchargées et permet d'éviter le problème de transfert. Le *problème de transfert* peut se produire lorsque vous écrivez une fonction générique qui accepte des références en tant que ses paramètres et de transmettre (ou *transfère*) ces paramètres à une autre fonction. Par exemple, si la fonction générique accepte un paramètre de type `const T&`, la fonction appelée ne peut pas modifier la valeur de ce paramètre. Si la fonction générique accepte un paramètre de type `T&`, elle ne peut pas être appelée en utilisant une rvalue (telle qu'un objet temporaire ou un littéral d'entier).

Normalement, pour résoudre ce problème, vous devez fournir des versions surchargées de la fonction générique qui acceptent `T&` et `const T&` pour chacun de ses paramètres. Par conséquent, le nombre de fonctions surchargées augmente de façon exponentielle avec le nombre de paramètres. Les références rvalue vous permettent d'écrire une version d'une fonction qui accepte des arguments arbitraires et les transfère à une autre fonction comme si celle-ci avait été appelée directement.

Prenez l'exemple suivant qui déclare quatre types, `W`, `X`, `Y` et `Z`. Le constructeur pour chaque type accepte une combinaison différente de **const** et non-**const** références lvalue comme paramètres.

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

Supposez que vous souhaitez écrire une fonction générique qui génère des objets. L'exemple suivant montre une manière d'écrire cette fonction :

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

L'exemple suivant montre un appel valide à la fonction `factory` :

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Toutefois, l'exemple suivant ne contient pas d'appel valide à la fonction `factory`, car `factory` accepte des références lvalue qui sont modifiables comme paramètres, mais elle est appelée à l'aide de rvalues :

```cpp
Z* pz = factory<Z>(2, 2);
```

Normalement, pour résoudre ce problème, vous devez créer une version surchargée de la fonction `factory` pour chaque combinaison de paramètres `A&` et `const A&`. Les références rvalue vous permettent d'écrire une version de la fonction `factory`, comme indiqué dans l'exemple suivant :

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

Cet exemple utilise des références rvalue comme paramètres de la fonction `factory`. L’objectif de la [std::forward](../standard-library/utility-functions.md#forward) fonction consiste à transférer les paramètres de la fonction de fabrique au constructeur de la classe de modèle.

L'exemple suivant illustre la fonction `main` qui utilise la fonction modifiée `factory` pour créer des instances des classes `W`, `X`, `Y` et `Z`. La fonction `factory` modifiée transfère ses paramètres (lvalues ou rvalues) au constructeur de classe approprié.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>Propriétés supplémentaires des références rvalue

**Vous pouvez surcharger une fonction prenne une référence lvalue et une référence rvalue.**

En surchargeant une fonction de prendre un **const** référence lvalue ou une référence rvalue, vous pouvez écrire du code qui fait la distinction entre des objets non modifiables (lvalues) et des valeurs temporaires modifiables (rvalues). Vous pouvez passer un objet à une fonction qui accepte une référence rvalue, sauf si l’objet est marqué comme **const**. L'exemple suivant illustre la fonction `f`, qui est surchargée pour accepter une référence lvalue et une référence rvalue. La fonction `main` appelle `f` avec des lvalues et une rvalue.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

Cet exemple génère la sortie suivante :

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

Dans cet exemple, le premier appel à `f` passe une variable locale (une lvalue) comme argument. Le deuxième appel à `f` passe un objet temporaire comme argument. L'objet temporaire ne pouvant pas être référencé ailleurs dans le programme, l'appel crée une liaison à la version surchargée de `f` qui accepte une référence rvalue, qui est libre de modifier l'objet.

**Le compilateur traite une référence rvalue nommée comme une lvalue et une référence rvalue sans nom comme une rvalue.**

Lorsque vous écrivez une fonction qui accepte une référence rvalue comme paramètre, ce paramètre est traité comme une lvalue dans le corps de la fonction. Le compilateur traite une référence rvalue nommée comme une lvalue car un objet nommé peut être référencé par plusieurs parties d'un programme ; il serait dangereux d'autoriser plusieurs parties d'un programme à modifier ou à supprimer des ressources de cet objet. Par exemple, si plusieurs parties d'un programme tentent de transférer des ressources à partir du même objet, seule la première partie transfère correctement la ressource.

L'exemple suivant illustre la fonction `g`, qui est surchargée pour accepter une référence lvalue et une référence rvalue. La fonction `f` accepte une référence rvalue comme paramètre (une référence rvalue nommée) et retourne une référence rvalue (une référence rvalue sans nom). Dans l'appel à `g` à partir de `f`, la résolution de surcharge sélectionne la version de `g` qui accepte une référence lvalue, car le corps de `f` traite son paramètre comme une lvalue. Dans l’appel à `g` à partir de `main`, la résolution de surcharge sélectionne la version de `g` qui accepte une référence rvalue car `f` retourne une référence rvalue.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

Cet exemple génère la sortie suivante :

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

Dans cet exemple, la fonction `main` passe une rvalue à `f`. Le corps de `f` traite son paramètre nommé comme une lvalue. L'appel de `f` à `g` lie le paramètre à une référence lvalue (première version surchargée de `g`).

- **Vous pouvez convertir une lvalue en référence rvalue.**

La bibliothèque Standard C++ [std::move](../standard-library/utility-functions.md#move) fonction vous permet de convertir un objet en une référence rvalue à cet objet. Vous pouvez également utiliser le **static_cast** mot clé à convertir une lvalue en référence rvalue, comme indiqué dans l’exemple suivant :

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

Cet exemple génère la sortie suivante :

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Modèles de fonction déduire leurs types d’arguments de modèle, puis utilisent les règles de réduction de référence.**

Il est courant d’écrire un modèle de fonction qui passe (ou *transfère*) ses paramètres à une autre fonction. Il est important de comprendre comment la déduction de type de modèle fonctionne pour les modèles de fonction qui acceptent des références rvalue.

Si l'argument de fonction est une rvalue, le compilateur déduit l'argument comme étant une référence rvalue. Par exemple, si vous passez une référence rvalue à un objet de type `X` à une fonction de modèle qui accepte le type `T&&` comme paramètre, la déduction d'argument template déduit `T` comme étant `X`. Par conséquent, le paramètre est de type `X&&`. Si l’argument de fonction est une lvalue ou **const** lvalue, le compilateur déduit son type doit être une référence lvalue ou **const** référence lvalue de ce type.

L'exemple suivant déclare un modèle de structure, puis le spécialise pour différents types de références. La fonction `print_type_and_value` accepte une référence rvalue comme paramètre et la transfère à la version spécialisée appropriée de la méthode `S::print`. La fonction `main` illustre les différentes façons d'appeler la méthode `S::print`.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

Cet exemple génère la sortie suivante :

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Pour résoudre chaque appel à la fonction `print_type_and_value`, le compilateur effectue d’abord une déduction de l’argument template. Il applique ensuite des règles de réduction de référence lorsqu’il remplace les types de paramètres par les arguments template déduits. Par exemple, le passage de la variable locale `s1` à la fonction `print_type_and_value` provoque la production par le compilateur de la signature de fonction suivante :

```cpp
print_type_and_value<string&>(string& && t)
```

Le compilateur utilise des règles de réduction de référence pour réduire la signature comme suit :

```cpp
print_type_and_value<string&>(string& t)
```

Cette version de la fonction `print_type_and_value` transfère ensuite son paramètre à la version spécialisée appropriée de la méthode `S::print`.

Le tableau suivant résume les règles de réduction de référence pour la déduction du type d'argument template :

|||
|-|-|
|Type développé|Type réduit|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

La déduction d’argument template est un élément important de l’implémentation du transfert parfait. La section Transfert parfait, présentée plus haut dans cette rubrique, décrit le transfert parfait plus en détail.

## <a name="summary"></a>Récapitulatif

Les références rvalue différencient les lvalues des rvalues. Elles peuvent vous aider à améliorer les performances de vos applications en évitant de faire appel à des allocations de la mémoire et des opérations de copie inutiles. Elles vous permettent également d’écrire une version d’une fonction qui accepte des arguments arbitraires et les transfère à une autre fonction comme si celle-ci avait été appelée directement.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Constructeurs de déplacement et opérateurs d’assignation de déplacement (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
