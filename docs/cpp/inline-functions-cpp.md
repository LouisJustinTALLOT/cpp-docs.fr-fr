---
title: Fonctions inline (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374085"
---
# <a name="inline-functions-c"></a>Fonctions inline (C++)

Une fonction définie dans le corps d'une déclaration de classe est une fonction inline.

## <a name="example"></a>Exemple

Dans la déclaration de classe suivante, le constructeur `Account` est une fonction inline. Les fonctions `GetBalance` `Deposit`du `Withdraw` membre, et ne sont pas spécifiées comme **inline,** mais peuvent être implémentées comme fonctions inline.

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> Dans la déclaration de classe, les fonctions ont été déclarées sans le mot clé **inline.** Le mot clé **en ligne** peut être spécifié dans la déclaration de classe; le résultat est le même.

Une fonction membre inline donnée doit être déclarée de la même manière dans chaque unité de compilation. Cette contrainte entraîne les fonctions inline à se comporter comme si elles étaient des fonctions instanciées. En outre, il doit exister une seule définition d'une fonction inline.

Une fonction de membre de classe par défaut à la liaison externe à moins qu’une définition pour cette fonction ne contienne le spécificateur **inline.** L’exemple précédent montre que ces fonctions n’ont pas besoin d’être explicitement déclarées avec le spécificateur **inline;** **l’utilisation de l’inline** dans la définition de fonction fait qu’il s’agit d’une fonction inline. Cependant, il est illégal de redéclarer une fonction comme **inline** après un appel à cette fonction.

## <a name="inline-__inline-and-__forceinline"></a>En ligne, __inline et \__forceinline

Les spécificateurs **en ligne** et **en __inline** instruisent le compilateur d’insérer une copie du corps de fonction dans chaque endroit où la fonction est appelée.

L'insertion (appelée expansion inline ou incorporation) se produit uniquement si l'analyse des coûts-avantages du compilateur montre qu'elle est rentable. L'expansion inline allège la surcharge des appels de fonction au coût potentiel d'une plus grande taille de code.

Le mot clé **__forceinline** l’emporte sur l’analyse coûts/avantages et s’appuie plutôt sur le jugement du programmeur. Faites preuve de prudence lorsque vous utilisez **__forceinline**. L’utilisation aveugle de **__forceinline** peut entraîner un code plus grand avec seulement des gains de performance marginaux ou, dans certains cas, même des pertes de performance (en raison de l’augmentation de la recherche d’un plus grand exécutable, par exemple).

L'utilisation des fonctions inline permet accélérer l'exécution de votre programme, car celles-ci éliminent la surcharge associée aux appels de fonction. Les fonctions développées inline sont soumises à des optimisations de code non disponibles pour les fonctions normales.

Le compilateur traite les options d'expansion inline et les mots clés comme des suggestions. Rien ne garantit que les fonctions seront incorporées. Vous ne pouvez pas forcer le compilateur à inline une fonction particulière, même avec le mot clé **__forceinline.** Lors de la compilation avec **/clr**, le compilateur ne sera pas en ligne une fonction s’il ya des attributs de sécurité appliquées à la fonction.

Le mot clé **en ligne** n’est disponible que dans le C. Les mots-clés **__inline** et **__forceinline** sont disponibles en C et en C. Pour la compatibilité avec les versions précédentes, **_inline** et **_forceinline** sont synonymes pour **__inline**, et **__forceinline** à moins que l’option compilateur [/Za \(Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Le mot clé **en ligne** indique au compilateur que l’expansion en ligne est préférée. Toutefois, le compilateur peut créer une instance séparée de la fonction (instanciation) et créer des liaisons d'appel standard au lieu d'insérer le code inline. Les deux cas où cela peut se produire sont :

- Fonctions récursives.

- Fonctions référencées par l'intermédiaire d'un pointeur ailleurs dans l'unité de traduction.

Ces motifs peuvent interférer avec l’inlining, *comme d’autres,* à la discrétion du compilateur; vous ne devez pas dépendre du spécificateur **inline** pour provoquer l’inlinité d’une fonction.

Comme avec les fonctions normales, il n’existe aucun ordre défini d’évaluation des arguments d’une fonction inline. En pratique, il peut être différent de l’ordre dans lequel les arguments sont évalués lorsqu’ils sont passés à l’aide d’un protocole d’appel de fonction normal.

L’option d’optimisation du compilateur [/Ob](../build/reference/ob-inline-function-expansion.md) permet de déterminer si l’expansion de la fonction en ligne se produit réellement.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) effectue l’inlining multi-module indépendamment du fait qu’il a été demandé dans le code source.

### <a name="example-1"></a>Exemple 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

Les fonctions des membres d’une classe peuvent être déclarées en ligne soit en utilisant le mot clé **en ligne,** soit en plaçant la définition de fonction dans la définition de la classe.

### <a name="example-2"></a>Exemple 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Microsoft Spécifique**

Le mot clé **__inline** est équivalent à **inline**.

Même avec **__forceinline,** le compilateur ne peut pas code en ligne en toutes circonstances. Le compilateur ne peut pas incorporer une fonction dans les cas suivants :

- La fonction ou son appelant est compilé avec /Ob0 (option par défaut pour les versions debug).

- La fonction et l'appelant utilisent différents types de gestion des exceptions (gestion des exceptions C++ dans l'un, gestion structurée des exceptions dans l'autre).

- La fonction a une liste d'arguments variable.

- La fonction utilise l'assembly inline, sauf si elle est compilée avec /Og, /Ox, /O1 ou /O2.

- La fonction est récursive et n’est pas accompagnée de **#pragma inline_recursion (sur)**. Avec le pragma, les fonctions récursives sont incorporées à une profondeur par défaut de 16 appels. Pour réduire la profondeur d’inlinisation, utilisez [inline_depth](../preprocessor/inline-depth.md) pragma.

- La fonction est virtuelle et est appelée virtuellement. Les appels directs aux fonctions virtuelles peuvent être incorporés.

- Le programme prend l'adresse de la fonction et l'appel est effectué via le pointeur vers la fonction. Les appels directs aux fonctions dont l'adresse est acceptée peuvent être incorporés.

- La fonction est également marquée avec le modificateur [nu](../cpp/naked-cpp.md) [__declspec.](../cpp/declspec.md)

Si le compilateur ne peut pas inlimiter une fonction déclarée avec **__forceinline,** il génère un avertissement de niveau 1, sauf lorsque :

- La fonction est compilée en utilisant /Od ou /Ob0. Aucun inlining n’est prévu dans ces cas.

- La fonction est définie à l’extérieur, dans une bibliothèque incluse ou une autre unité de traduction, ou est une cible d’appel virtuel ou une cible d’appel indirecte. Le compilateur ne peut pas identifier le code non-inlined qu’il ne peut pas trouver dans l’unité de traduction actuelle.

Les fonctions récursives peuvent être substituées en ligne à une profondeur spécifiée par le [pragma inline_depth,](../preprocessor/inline-depth.md) jusqu’à un maximum de 16 appels. Au-delà de cette profondeur, les appels de fonction récursive sont traités comme des appels à une instance de la fonction.  La profondeur à laquelle les fonctions récursives sont examinées par l’heuristique inline ne peut pas dépasser 16. Le [pragma inline_recursion](../preprocessor/inline-recursion.md) contrôle l’expansion en ligne d’une fonction actuellement en expansion. Consultez l’option [compilateur Inline-Function Expansion](../build/reference/ob-inline-function-expansion.md) (/Ob) pour obtenir des informations connexes.

**END Microsoft Spécifique**

Pour plus d’informations sur l’utilisation du spécificateur **en ligne,** voir :

- [Fonctions membres des classes inline](../cpp/inline-functions-cpp.md)

- [Définir les fonctions Inline CMD avec dllexport et dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Quand utiliser les fonctions inline

Les fonctions inline sont utilisées de façon optimale pour les petites fonctions telles que l'accès aux membres de données privées. L’objectif principal de ces fonctions d’accesseur à une ou deux lignes est de retourner des informations d’état sur les objets. Les fonctions courtes sont sensibles aux charges mémoire des appels de fonction. Les fonctions longues passent proportionnellement moins de temps dans la séquence d'appel/retour et bénéficient moins de l'inlining.

Une `Point` classe peut être définie comme suit :

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

En supposant que la manipulation de coordonnées est une opération relativement courante`x` chez `y` un client d’une telle classe, en spécifiant les deux fonctions d’accesseur (et dans l’exemple précédent) comme **en ligne** enregistre généralement les frais généraux sur :

- Appels de fonction (notamment le paramètre passe et place l'adresse de l'objet dans la pile)

- Conservation du frame de pile de l'appelant

- Nouvelle installation du frame de pile

- Communication de la valeur de retour

- Restauration de l'ancien frame de pile

- Renvoie

## <a name="inline-functions-vs-macros"></a>Fonctions inlines vs macros

Bien que les fonctions inline soient similaires aux macros (car le code de fonction est développé au point de l’appel au moment de la compilation), les fonctions inline sont analysées par le compilateur, alors que les macros sont développées par le préprocesseur. Par conséquent, il existe plusieurs différences importantes :

- Les fonctions inline suivent tous les protocoles de sécurité de type appliqués sur les fonctions normales.

- Les fonctions inlines sont spécifiées à l’aide de la même syntaxe que toute autre fonction, sauf qu’elles incluent le mot clé **en ligne** dans la déclaration de fonction.

- Les expressions passées comme arguments aux fonctions inline sont évaluées une fois. Dans certains cas, les expressions passées comme arguments aux macros peuvent être évaluées plusieurs fois.

L'exemple suivant montre une macro qui convertit les minuscules en majuscules :

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

L’intention de `toupper(getc(stdin))` l’expression est qu’un personnage`stdin`doit être lu à partir de l’appareil de console ( ) et, si nécessaire, converti en uppercase.

Grâce à l'implémentation de la macro, `getc` est exécuté une fois pour déterminer si le caractère est supérieur ou égal à « a », et une fois pour déterminer s'il est inférieur ou égal à « z ». S'il est dans cette plage, `getc` est à nouveau exécuté pour convertir le caractère en majuscules. Cela signifie que le programme attend deux ou trois caractères lorsque, idéalement, il doit en attendre qu'un seul.

Les fonctions inline remédient au problème décrit auparavant :

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>Voir aussi

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)
