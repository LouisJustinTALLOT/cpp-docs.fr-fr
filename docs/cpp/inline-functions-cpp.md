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
ms.openlocfilehash: b13007211857d84e4f3b33c80ed6b5beaf6f0bcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178235"
---
# <a name="inline-functions-c"></a>Fonctions inline (C++)

Une fonction définie dans le corps d'une déclaration de classe est une fonction inline.

## <a name="example"></a>Exemple

Dans la déclaration de classe suivante, le constructeur `Account` est une fonction inline. Les fonctions membres `GetBalance`, `Deposit`et `Withdraw` ne sont pas spécifiées comme **inline** , mais peuvent être implémentées en tant que fonctions inline.

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
>  Dans la déclaration de classe, les fonctions ont été déclarées sans le mot clé **inline** . Le mot clé **inline** peut être spécifié dans la déclaration de classe ; le résultat est le même.

Une fonction membre inline donnée doit être déclarée de la même manière dans chaque unité de compilation. Cette contrainte entraîne les fonctions inline à se comporter comme si elles étaient des fonctions instanciées. En outre, il doit exister une seule définition d'une fonction inline.

Une fonction membre de classe A par défaut une liaison externe, sauf si une définition de cette fonction contient le spécificateur **inline** . L’exemple précédent montre que ces fonctions n’ont pas besoin d’être déclarées explicitement avec le spécificateur **inline** ; l’utilisation de **inline** dans la définition de fonction provoque l’utilisation d’une fonction Inline. Toutefois, il est illégal de redéclarer une fonction comme **inline** après un appel à cette fonction.

## <a name="inline-__inline-and-__forceinline"></a>Inline, __inline et \__forceinline

Les spécificateurs **inline** et **__inline** indiquent au compilateur d’insérer une copie du corps de la fonction à chaque emplacement où la fonction est appelée.

L'insertion (appelée expansion inline ou incorporation) se produit uniquement si l'analyse des coûts-avantages du compilateur montre qu'elle est rentable. L'expansion inline allège la surcharge des appels de fonction au coût potentiel d'une plus grande taille de code.

Le mot clé **__forceinline** remplace l’analyse coût/avantage et s’appuie plutôt sur le jugement du programmeur. Soyez prudent lors de l’utilisation de **__forceinline**. L’utilisation non discriminatoire de **__forceinline** peut entraîner une augmentation du code avec des gains de performances marginaux ou, dans certains cas, même des pertes de performances (en raison de l’augmentation de la pagination d’un exécutable plus volumineux, par exemple).

L'utilisation des fonctions inline permet accélérer l'exécution de votre programme, car celles-ci éliminent la surcharge associée aux appels de fonction. Les fonctions développées inline sont soumises à des optimisations de code non disponibles pour les fonctions normales.

Le compilateur traite les options d'expansion inline et les mots clés comme des suggestions. Rien ne garantit que les fonctions seront incorporées. Vous ne pouvez pas forcer le compilateur à incorporer une fonction particulière, même avec le mot clé **__forceinline** . Lors de la compilation avec **/CLR**, le compilateur n’incorpore pas une fonction si des attributs de sécurité sont appliqués à la fonction.

Le mot clé **inline** est uniquement disponible C++dans. Les mots clés **__inline** et **__forceinline** sont disponibles à la fois C++dans C et. Pour la compatibilité avec les versions précédentes, **_inline** et **_forceinline** sont des synonymes pour **__inline**et **__forceinline** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Le mot clé **inline** indique au compilateur que l’expansion Inline est préférée. Toutefois, le compilateur peut créer une instance séparée de la fonction (instanciation) et créer des liaisons d'appel standard au lieu d'insérer le code inline. Les deux cas où cela peut se produire sont :

- Fonctions récursives.

- Fonctions référencées par l'intermédiaire d'un pointeur ailleurs dans l'unité de traduction.

Ces raisons peuvent interférer avec l’incorporation, *comme les autres*, à la discrétion du compilateur. vous ne devez pas dépendre du spécificateur **inline** pour provoquer l’Inline d’une fonction.

Comme avec les fonctions normales, il n’existe aucun ordre défini d’évaluation des arguments d’une fonction inline. En pratique, il peut être différent de l’ordre dans lequel les arguments sont évalués lorsqu’ils sont passés à l’aide d’un protocole d’appel de fonction normal.

L’option d’optimisation du compilateur [/ob](../build/reference/ob-inline-function-expansion.md) permet de déterminer si l’expansion des fonctions inline se produit réellement.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) effectue une incorporation entre modules, qu’elle ait été demandée ou non dans le code source.

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

Les fonctions membres d’une classe peuvent être déclarées Inline à l’aide du mot clé **inline** ou en plaçant la définition de fonction dans la définition de classe.

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

**Section spécifique de Microsoft**

Le mot clé **__inline** est équivalent à **inline**.

Même avec **__forceinline**, le compilateur ne peut pas incorporer le code dans toutes les circonstances. Le compilateur ne peut pas incorporer une fonction dans les cas suivants :

- La fonction ou son appelant est compilé avec /Ob0 (option par défaut pour les versions debug).

- La fonction et l'appelant utilisent différents types de gestion des exceptions (gestion des exceptions C++ dans l'un, gestion structurée des exceptions dans l'autre).

- La fonction a une liste d'arguments variable.

- La fonction utilise l'assembly inline, sauf si elle est compilée avec /Og, /Ox, /O1 ou /O2.

- La fonction est récursive et n’est pas accompagnée de **#pragma inline_recursion (on)** . Avec le pragma, les fonctions récursives sont incorporées à une profondeur par défaut de 16 appels. Pour réduire la profondeur d’incorporation, utilisez [inline_depth](../preprocessor/inline-depth.md) pragma.

- La fonction est virtuelle et est appelée virtuellement. Les appels directs aux fonctions virtuelles peuvent être incorporés.

- Le programme prend l'adresse de la fonction et l'appel est effectué via le pointeur vers la fonction. Les appels directs aux fonctions dont l'adresse est acceptée peuvent être incorporés.

- La fonction est également marquée avec le modificateur [__declspec](../cpp/declspec.md) [Naked](../cpp/naked-cpp.md) .

Si le compilateur ne peut pas incorporer une fonction déclarée avec **__forceinline**, il génère un avertissement de niveau 1, sauf dans les cas suivants :

- La fonction est compilée à l’aide de/OD ou/Ob0. Dans ces cas, aucune incorporation n’est attendue.

- La fonction est définie en externe, dans une bibliothèque incluse ou une autre unité de traduction, ou est une cible d’appel virtuel ou une cible d’appel indirect. Le compilateur ne peut pas identifier le code non inline qu’il ne peut pas trouver dans l’unité de traduction actuelle.

Les fonctions récursives peuvent être substituées Inline à une profondeur spécifiée par le pragma [inline_depth](../preprocessor/inline-depth.md) , jusqu’à un maximum de 16 appels. Au-delà de cette profondeur, les appels de fonction récursive sont traités comme des appels à une instance de la fonction.  La profondeur à laquelle les fonctions récursives sont examinées par l’heuristique inline ne peut pas dépasser 16. Le pragma [inline_recursion](../preprocessor/inline-recursion.md) contrôle l’expansion Inline d’une fonction actuellement en expansion. Pour obtenir des informations connexes, consultez l’option de compilateur/ob ( [inline-function expansion](../build/reference/ob-inline-function-expansion.md) ).

**Fin de la section spécifique de Microsoft**

Pour plus d’informations sur l’utilisation du spécificateur **inline** , consultez :

- [Fonctions membres de classe Inline](../cpp/inline-functions-cpp.md)

- [Définition de fonctions C++ incorporées avec dllexport et dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Quand utiliser les fonctions inline

Les fonctions inline sont utilisées de façon optimale pour les petites fonctions telles que l'accès aux membres de données privées. L’objectif principal de ces fonctions d’accesseur à une ou deux lignes est de retourner des informations d’état sur les objets. Les fonctions courtes sont sensibles aux charges mémoire des appels de fonction. Les fonctions longues passent proportionnellement moins de temps dans la séquence d'appel/retour et bénéficient moins de l'inlining.

Une classe `Point` peut être définie comme suit :

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

En supposant que la manipulation de coordonnées est une opération relativement courante dans un client d’une telle classe, la spécification des deux fonctions d’accesseur (`x` et `y` dans l’exemple précédent) comme **inline** enregistre généralement la surcharge sur :

- Appels de fonction (notamment le paramètre passe et place l'adresse de l'objet dans la pile)

- Conservation du frame de pile de l'appelant

- Nouvelle installation du frame de pile

- Communication de la valeur de retour

- Restauration de l'ancien frame de pile

- Renvoie

## <a name="inline-functions-vs-macros"></a>Fonctions inline et macros

Bien que les fonctions inline soient similaires aux macros (car le code de fonction est développé au point de l’appel au moment de la compilation), les fonctions inline sont analysées par le compilateur, alors que les macros sont développées par le préprocesseur. Par conséquent, il existe plusieurs différences importantes :

- Les fonctions inline suivent tous les protocoles de sécurité de type appliqués sur les fonctions normales.

- Les fonctions inline sont spécifiées à l’aide de la même syntaxe que toute autre fonction, sauf qu’elles incluent le mot clé **inline** dans la déclaration de la fonction.

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

L’objectif de l’expression `toupper(getc(stdin))` est qu’un caractère doit être lu à partir de l’appareil de la console (`stdin`) et, si nécessaire, converti en majuscules.

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
