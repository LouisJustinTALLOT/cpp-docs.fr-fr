---
title: Fonctions inline (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f3d74a7b640e203a8a5882710849c98ba5b40f
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163586"
---
# <a name="inline-functions-c"></a>Fonctions inline (C++)

Une fonction définie dans le corps d'une déclaration de classe est une fonction inline.

## <a name="example"></a>Exemple

Dans la déclaration de classe suivante, le constructeur `Account` est une fonction inline. Les fonctions membres `GetBalance`, `Deposit`, et `Withdraw` ne sont pas spécifiés en tant que **inline** mais peut être implémentée en tant que fonctions inline.

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
>  Dans la déclaration de classe, les fonctions ont été déclarées sans le **inline** mot clé. Le **inline** mot clé peut être spécifié dans la déclaration de classe, le résultat est identique.

Une fonction membre inline donnée doit être déclarée de la même manière dans chaque unité de compilation. Cette contrainte entraîne les fonctions inline à se comporter comme si elles étaient des fonctions instanciées. En outre, il doit exister une seule définition d'une fonction inline.

Une fonction membre de classe par défaut est une liaison externe, sauf si une définition de cette fonction contient le **inline** spécificateur. L’exemple précédent montre que ces fonctions ne doivent pas explicitement déclarées avec le **inline** spécificateur ; à l’aide de **inline** dans la fonction de définition devient une fonction inline. Toutefois, il est non conforme de redéclarer une fonction en tant que **inline** après un appel à cette fonction.

## <a name="inline-inline-and-forceinline"></a>Inline, __inline, et \__forceinline

Le **inline** et **__inline** spécificateurs indiquer au compilateur d’insérer une copie du corps de la fonction dans chaque emplacement où la fonction est appelée.

L'insertion (appelée expansion inline ou incorporation) se produit uniquement si l'analyse des coûts-avantages du compilateur montre qu'elle est rentable. L'expansion inline allège la surcharge des appels de fonction au coût potentiel d'une plus grande taille de code.

Le **__forceinline** mot clé substitue l’analyse coût/bénéfice et s’appuie sur le jugement du programmeur à la place. Soyez prudent lorsque vous utilisez **__forceinline**. L’utilisation intempestive de **__forceinline** peut entraîner un code plus volumineux avec uniquement les gains de performance marginaux ou, dans certains cas, pertes de performance (en raison d’une pagination accrue d’un fichier exécutable plus volumineux, par exemple).

L'utilisation des fonctions inline permet accélérer l'exécution de votre programme, car celles-ci éliminent la surcharge associée aux appels de fonction. Les fonctions développées inline sont soumises à des optimisations de code non disponibles pour les fonctions normales.

Le compilateur traite les options d'expansion inline et les mots clés comme des suggestions. Rien ne garantit que les fonctions seront incorporées. Vous ne pouvez pas forcer le compilateur à incorporer une fonction particulière, même avec le **__forceinline** mot clé. Lors de la compilation avec **/CLR**, le compilateur n’incorpore pas une fonction s’il existe des attributs de sécurité appliqués à la fonction.

Le **inline** mot clé est disponible uniquement en C++. Le **__inline** et **__forceinline** mots clés sont disponibles en C et C++. Pour assurer la compatibilité avec les versions précédentes, **_inline** et **_forceinline** sont synonymes de **__inline**, et **__forceinline** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

Le **inline** mot clé indique au compilateur que l’expansion inline est recommandée. Toutefois, le compilateur peut créer une instance séparée de la fonction (instanciation) et créer des liaisons d'appel standard au lieu d'insérer le code inline. Les deux cas où cela peut se produire sont :

- Fonctions récursives.

- Fonctions référencées par l'intermédiaire d'un pointeur ailleurs dans l'unité de traduction.

Ces raisons peuvent interférer avec incorporation, *ainsi que d’autres*, à la discrétion du compilateur ; vous ne devez pas prévoir de le **inline** spécificateur pour qu’une fonction être inline.

Comme avec les fonctions normales, il n’existe aucun ordre défini d’évaluation des arguments d’une fonction inline. En pratique, il peut être différent de l’ordre dans lequel les arguments sont évalués lorsqu’ils sont passés à l’aide d’un protocole d’appel de fonction normal.

Le [/Ob](../build/reference/ob-inline-function-expansion.md) option d’optimisation du compilateur permet de déterminer si expansion des fonctions inline se produit réellement.

[/ LTCG](../build/reference/ltcg-link-time-code-generation.md) effectue entre modules incorporation (inlining) indépendamment de si elle a été demandée dans le code source.

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

Fonctions de membre d’une classe peuvent être déclarées inline en utilisant le **inline** mot clé ou en plaçant la définition de fonction au sein de la définition de classe.

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

### <a name="microsoft-specific"></a>Section spécifique à Microsoft

Le **__inline** mot clé est équivalente à **inline**.

Même avec **__forceinline**, le compilateur ne peut pas le code inline dans toutes les circonstances. Le compilateur ne peut pas incorporer une fonction dans les cas suivants :

- La fonction ou son appelant est compilé avec /Ob0 (option par défaut pour les versions debug).

- La fonction et l'appelant utilisent différents types de gestion des exceptions (gestion des exceptions C++ dans l'un, gestion structurée des exceptions dans l'autre).

- La fonction a une liste d'arguments variable.

- La fonction utilise l'assembly inline, sauf si elle est compilée avec /Og, /Ox, /O1 ou /O2.

- La fonction est récursive et non accompagnée **inline_recursion (on) #pragma**. Avec le pragma, les fonctions récursives sont incorporées à une profondeur par défaut de 16 appels. Pour réduire la profondeur d’incorporation, utilisez [inline_depth](../preprocessor/inline-depth.md) pragma.

- La fonction est virtuelle et est appelée virtuellement. Les appels directs aux fonctions virtuelles peuvent être incorporés.

- Le programme prend l'adresse de la fonction et l'appel est effectué via le pointeur vers la fonction. Les appels directs aux fonctions dont l'adresse est acceptée peuvent être incorporés.

- La fonction est également marquée avec le [naked](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) modificateur.

Si le compilateur ne peut pas incorporer une fonction déclarée avec **__forceinline**, il génère un avertissement de niveau 1, sauf quand :

- La fonction est compilée à l’aide de /Od ou/Ob0. N’incorporation (inlining) est attendu dans ces cas.

- La fonction est définie en externe, dans une bibliothèque ou une autre unité de traduction, ou est une cible d’appel virtuel ou d’une cible d’appel indirect. Le compilateur ne peut pas identifier le code non inline qui il ne trouve pas dans l’unité de traduction actuelle.

Fonctions récursives peuvent être substituées inline à une profondeur spécifiée par le [inline_depth](../preprocessor/inline-depth.md) pragma, avec un maximum de 16 appels. Au-delà de cette profondeur, les appels de fonction récursive sont traités comme des appels à une instance de la fonction.  La profondeur à laquelle les fonctions récursives sont examinées par l’heuristique inline ne peut pas dépasser 16. Le [inline_recursion](../preprocessor/inline-recursion.md) pragma contrôle l’expansion inline d’une fonction en cours d’expansion. Consultez le [Expansion des fonctions Inline](../build/reference/ob-inline-function-expansion.md) (/ Ob) option de compilateur pour obtenir des informations connexes.

**FIN de la section spécifique à Microsoft**

Pour plus d’informations sur l’utilisation de la **inline** spécificateur, consultez :

- [Fonctions de membre de classe inline](../cpp/inline-functions-cpp.md)

- [Définition de fonctions C++ incorporées avec dllexport et dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Quand utiliser les fonctions inline

Les fonctions inline sont utilisées de façon optimale pour les petites fonctions telles que l'accès aux membres de données privées. L'objectif principal de ces fonctions d'accesseur à une ou deux lignes est de retourner des informations d'état sur les objets. Les fonctions courtes sont sensibles aux charges mémoire des appels de fonction. Les fonctions longues passent proportionnellement moins de temps dans la séquence d'appel/retour et bénéficient moins de l'inlining.

Un `Point` classe peut être définie comme suit :

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

En supposant que la manipulation des coordonnées est une opération relativement courante dans un client d’une telle classe, en spécifiant les deux fonctions d’accesseur (`x` et `y` dans l’exemple précédent) en tant que **inline** stocke généralement les charge sur :

- Appels de fonction (notamment le paramètre passe et place l'adresse de l'objet dans la pile)

- Conservation du frame de pile de l'appelant

- Nouvelle installation du frame de pile

- Communication de la valeur de retour

- Restauration de l'ancien frame de pile

- Retourner

## <a name="inline-functions-vs-macros"></a>Fonctions inline et macros

Bien que les fonctions inline soient similaires aux macros (car le code de fonction est développé au point de l’appel au moment de la compilation), les fonctions inline sont analysées par le compilateur, alors que les macros sont développées par le préprocesseur. Par conséquent, il existe plusieurs différences importantes :

- Les fonctions inline suivent tous les protocoles de sécurité de type appliqués sur les fonctions normales.

- Fonctions inline sont spécifiées à l’aide de la même syntaxe comme toute autre fonction sauf qu’ils incluent le **inline** mot clé dans la déclaration de fonction.

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

L’intention de l’expression `toupper(getc(stdin))` est qu’un caractère doit être lu à partir de l’appareil de console (`stdin`) et, si nécessaire, être converti en majuscules.

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