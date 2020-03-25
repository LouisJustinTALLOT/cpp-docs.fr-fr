---
title: Conversions standard
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: 41ad348b7109451f519c44f685cea0a271f71925
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161008"
---
# <a name="standard-conversions"></a>Conversions standard

Le langage C++ définit les conversions entre ses types fondamentaux. Il définit également les conversions pour les types dérivés de pointeur, de référence et de pointeur vers membre. Ces conversions sont appelées *conversions standard*.

Cette section décrit les conversions standard suivantes :

- Promotions intégrales

- Conversions intégrales

- Conversions flottantes

- Conversions flottantes et intégrales

- Conversions arithmétiques

- Conversions de pointeurs

- Conversions de références

- Conversions de pointeur vers membre

  > [!NOTE]
  > Les types définis par l'utilisateur peuvent spécifier leurs propres conversions. La conversion de types définis par l’utilisateur est traitée dans les [constructeurs](../cpp/constructors-cpp.md) et les [conversions](../cpp/user-defined-type-conversions-cpp.md).

Le code suivant provoque des conversions (dans cet exemple, promotions intégrales) :

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Le résultat d'une conversion est une l-value uniquement si elle produit un type référence. Par exemple, une conversion définie par l’utilisateur déclarée comme `operator int&()` retourne une référence et est une l-value. Toutefois, une conversion déclarée comme `operator int()` retourne un objet et n’est pas une l-value.

## <a name="integral-promotions"></a>Promotions intégrales

Les objets d’un type intégral peuvent être convertis en un autre type intégral plus large, autrement dit un type qui peut représenter un plus grand ensemble de valeurs. Ce type étendu de conversion est appelé *promotion intégrale*. Avec la promotion intégrale, vous pouvez utiliser les types suivants dans une expression partout où un autre type intégral peut être utilisé :

- Objets, littéraux et constantes de type **char** et **short int**

- Types d'énumération

- champs de bits **int**

- Énumérateurs

C++les promotions sont « préservation de la valeur », car la valeur de la promotion est garantie comme étant la même que la valeur avant la promotion. Dans les promotions de préservation de valeurs, les objets de types intégraux plus courts (tels que les champs de bits ou les objets de type **char**) sont promus en type **int** si **int** peut représenter la plage complète du type d’origine. Si **int** ne peut pas représenter la plage complète des valeurs, l’objet est promu en type **unsigned int**.  Bien que cette stratégie soit la même que celle utilisée par le langage C standard, les conversions de conservation de valeur ne préservent pas l' « inscription » de l’objet.

Les promotions de type conservation-valeur et les promotions qui conservent l'entier non signé produisent normalement les mêmes résultats. Toutefois, ils peuvent produire des résultats différents si l’objet promu apparaît comme suit :

- Opérande de `/`, `%`, `/=`, `%=`, `<`, `<=`, `>`ou `>=`

   Ces opérateurs se basent sur un signe pour déterminer le résultat. Les promotions de préservation de la valeur et de préconservation produisent des résultats différents lorsqu’elles sont appliquées à ces opérandes.

- Opérande gauche de `>>` ou `>>=`

   Ces opérateurs traitent différemment les quantités signées et non signées dans une opération de décalage. Pour les quantités signées, une opération de décalage vers la droite propage le bit de signe dans les positions de bit libérées, tandis que les positions de bit libérées sont remplies de zéros dans des quantités non signées.

- Un argument à une fonction surchargée, ou l’opérande d’un opérateur surchargé, qui dépend de l’inscription du type d’opérande pour la correspondance d’argument. Pour plus d’informations sur la définition d’opérateurs surchargés, consultez [opérateurs surchargés](../cpp/operator-overloading.md).

## <a name="integral-conversions"></a>Conversions intégrales

Les *conversions entières* sont des conversions entre types intégraux. Les types intégraux **sont char**, **short** (ou **short int**), **int**, **long**et **long long**. Ces types peuvent être **qualifiés avec** signed ou **unsigned**, et **unsigned** peut être utilisé comme raccourci pour **unsigned int**.

### <a name="signed-to-unsigned"></a>Type signé en type non signé

Les objets de types intégraux signés peuvent être convertis en types non signés correspondants. Lorsque ces conversions se produisent, le modèle binaire réel ne change pas. Toutefois, l’interprétation des données change. Prenons le code suivant :

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

Dans l’exemple précédent, un **short signé**, `i`, est défini et initialisé sur un nombre négatif. L’expression `(u = i)` entraîne la conversion de `i` en valeur **unsigned short** avant l’assignation à `u`.

### <a name="unsigned-to-signed"></a>Type non signé en type signé

Les objets de types intégraux non signés peuvent être convertis en types signés correspondants. Toutefois, si la valeur non signée est en dehors de la plage représentable du type signé, le résultat n’aura pas la valeur correcte, comme illustré dans l’exemple suivant :

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

Dans l’exemple précédent, `u` est un objet entier **short non signé** qui doit être converti en une quantité signée pour évaluer l’expression `(i = u)`. Étant donné que sa valeur ne peut pas être correctement représentée dans un **short signé**, les données sont mal interprétées comme indiqué.

## <a name="floating-point-conversions"></a>Conversions de nombres à virgule flottante

Un objet de type flottant peut être converti sans risque en type flottant plus précis. Cela permet de ne pas perdre de signification lors de la conversion. Par exemple, les conversions de **float** en **double** ou de **double** en **long double** sont sûres et la valeur est inchangée.

Un objet de type flottant peut également être converti en un type moins précis, s’il se trouve dans une plage qui peut être représentée par ce type. (Consultez [limites flottantes](../cpp/floating-limits.md) pour les plages de types flottants.) Si la valeur d’origine n’est pas représentable précisément, elle peut être convertie en la valeur représentable supérieure ou inférieure suivante. Le résultat n’est pas défini si aucune valeur de ce type n’existe. Prenons l’exemple suivant :

```cpp
cout << (float)1E300 << endl;
```

La valeur maximale représentable par le type **float** est 3.402823466 E38, un nombre bien plus petit que 1E300. Par conséquent, le nombre est converti en l’infini et le résultat est « INF ».

## <a name="conversions-between-integral-and-floating-point-types"></a>Conversions entre types intégraux et à virgule flottante

Certaines expressions peuvent provoquer la conversion des objets de type flottant en types intégraux, ou vice versa. Quand un objet de type intégral est converti en type flottant et que la valeur d’origine n’est pas représentable exactement, le résultat est soit la valeur la plus élevée suivante, soit la valeur représentable suivante.

Lorsqu’un objet de type flottant est converti en type intégral, la partie fractionnaire est *tronquée*ou arrondie à zéro. Un nombre comme 1,3 est converti en 1, et-1,3 est converti en-1. Si la valeur tronquée est supérieure à la valeur représentable la plus élevée, ou inférieure à la valeur représentable la plus faible, le résultat n’est pas défini.

## <a name="arithmetic-conversions"></a>Conversions arithmétiques

De nombreux opérateurs binaires (présentés dans [expressions avec des opérateurs binaires](../cpp/expressions-with-binary-operators.md)) entraînent des conversions d’opérandes et produisent des résultats de la même façon. Les conversions provoquées par ces opérateurs sont appelées *conversions arithmétiques habituelles*. Les conversions arithmétiques des opérandes qui ont des types natifs différents sont effectuées comme indiqué dans le tableau suivant. Les types typedef se comportent selon leurs types natifs sous-jacents.

### <a name="conditions-for-type-conversion"></a>Conditions pour la conversion de type

|Conditions remplies|Conversion|
|--------------------|----------------|
|L’un des opérandes est de type **long double**.|L’autre opérande est converti en type **long double**.|
|La condition précédente n’est pas remplie et l’un des opérandes est de type **double**.|L’autre opérande est converti en type **double**.|
|Les conditions précédentes ne sont pas remplies et l’un des opérandes est de type **float**.|L’autre opérande est converti en type **float**.|
|Conditions précédentes non remplies (aucun des opérandes n’est de type flottant).|Les opérandes obtiennent des promotions intégrales comme suit :<br /><br />-Si l’un des opérandes est de type **unsigned long**, l’autre opérande est converti en type **unsigned long**.<br />-Si la condition précédente n’est pas remplie et si l’un des opérandes est de type **long** et l’autre de type **unsigned int**, les deux opérandes sont convertis en type **unsigned long**.<br />-Si les deux conditions précédentes ne sont pas remplies et si l’un des opérandes est de type **long**, l’autre opérande est converti en type **long**.<br />-Si les trois conditions précédentes ne sont pas remplies et si l’un des opérandes est de type **unsigned int**, l’autre opérande est converti en type **unsigned int**.<br />-Si aucune des conditions précédentes n’est remplie, les deux opérandes sont convertis en type **int**.|

Le code suivant illustre les règles de conversion décrites dans le tableau :

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

Dans l'exemple précédent, la première instruction affiche la multiplication de deux types intégraux, `iVal` et `ulVal`. La condition remplie est qu’aucun opérande n’est de type flottant et qu’un opérande est de type **unsigned int**. Ainsi, l’autre opérande, `iVal`, est converti en type **unsigned int**. Le résultat est ensuite affecté à `dVal`. La condition remplie ici est que l’un des opérandes est de type **double**. par conséquent, le résultat de la valeur **int non signé** de la multiplication est converti en type **double**.

La deuxième instruction de l’exemple précédent illustre l’ajout d’un **float** et d’un type intégral : `fVal` et `ulVal`. La variable `ulVal` est convertie en type **float** (troisième condition dans le tableau). Le résultat de l’addition est converti en type **double** (deuxième condition dans la table) et affecté à `dVal`.

## <a name="pointer-conversions"></a>Conversions de pointeurs

Les pointeurs peuvent être convertis durant l'assignation, l'initialisation, la comparaison et d'autres expressions.

### <a name="pointer-to-classes"></a>Pointeur vers classes

Il existe deux cas dans lesquels un pointeur vers une classe peut être converti en un pointeur vers une classe de base.

Dans le premier cas, la classe de base spécifiée est accessible et la conversion est n'est pas ambiguë. Pour plus d’informations sur les références de classe de base ambiguës, consultez [plusieurs classes de base](../cpp/multiple-base-classes.md).

L'accessibilité d'une classe de base dépend du type d'héritage utilisé dans la dérivation. Prenons l'héritage illustré dans l'illustration suivante.

![Graphique d’héritage représentant&#45;l’accessibilité de la classe de base](../cpp/media/vc38xa1.gif "Graphique d’héritage représentant&#45;l’accessibilité de la classe de base") <br/>
Graphique d'héritage pour l'illustration de l'accessibilité de la classe de base

Le tableau suivant indique l'accessibilité de la classe de base d'après la situation illustrée.

|Type de fonction|Dérivation|Conversion de<br /><br /> B * à un\* légal ?|
|----------------------|----------------|-------------------------------------------|
|Fonction externe (hors portée de classe)|Privé|Non|
||Protected|Non|
||Public|Oui|
|Fonction membre B (dans la portée B)|Privé|Oui|
||Protected|Oui|
||Public|Oui|
|Fonction membre C (dans la portée C)|Privé|Non|
||Protected|Oui|
||Public|Oui|

Dans le second cas, un pointeur vers une classe peut être converti en pointeur vers une classe de base lorsque vous utilisez une conversion de type explicite. Pour plus d’informations sur les conversions de types explicites, consultez [opérateur de conversion de type explicite](explicit-type-conversion-operator-parens.md).

Le résultat de cette conversion est un pointeur vers le sous- *objet*, la partie de l’objet qui est complètement décrite par la classe de base.

Le code suivant définit deux classes, `A` et `B`, où `B` est dérivée de `A`. (Pour plus d’informations sur l’héritage, consultez [classes dérivées](../cpp/inheritance-cpp.md).) Il définit ensuite `bObject`, un objet de type `B`et deux pointeurs (`pA` et `pB`) qui pointent vers l’objet.

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

Le pointeur `pA` est de type `A *`, ce qui peut être interprété comme suit : « pointeur vers un objet de type `A` ». Les membres de `bObject` (tels que `BComponent` et `BMemberFunc`) sont uniques au type `B` et sont donc inaccessibles par le biais de `pA`. Le pointeur `pA` autorise l'accès uniquement aux caractéristiques (fonctions membres et données) de l'objet définies dans la classe `A`.

### <a name="pointer-to-function"></a>Pointeur vers fonction

Un pointeur vers une fonction peut être converti en type `void *`, si le type `void *` est suffisamment grand pour contenir ce pointeur.

### <a name="pointer-to-void"></a>Pointeur vers void

Les pointeurs vers le type **void** peuvent être convertis en pointeurs vers tout autre type, mais uniquement avec un cast de type explicite (contrairement à en C). Un pointeur vers n’importe quel type peut être converti implicitement en pointeur vers le type **void**. Un pointeur vers un objet incomplet d’un type peut être converti en pointeur vers **void** (implicitement) et inversement (explicitement). Le résultat de ce type de conversion est égal à la valeur du pointeur d'origine. Un objet est considéré comme incomplet s’il est déclaré, mais il n’y a pas suffisamment d’informations disponibles pour déterminer sa taille ou sa classe de base.

Un pointeur vers un objet qui n’est pas **const** ou **volatile** peut être converti implicitement en un pointeur de type `void *`.

### <a name="const-and-volatile-pointers"></a>Pointeurs const et volatile

C++ne fournit pas de conversion standard d’un type **const** ou **volatile** en un type qui n’est pas **const** ou **volatile**. Cependant, toute sorte de conversion peut être spécifiée à l'aide de casts de type explicite (y compris les conversions qui ne sont pas sécurisées).

> [!NOTE]
> C++les pointeurs vers des membres, à l’exception des pointeurs vers des membres statiques, sont différents des pointeurs normaux et n’ont pas les mêmes conversions standard. Les pointeurs vers des membres statiques sont des pointeurs normaux et ils ont les mêmes conversions que les pointeurs normaux.

### <a name="null-pointer-conversions"></a>Conversions de pointeurs null

Une expression constante intégrale qui prend la valeur zéro, ou une expression castée en type pointeur, est convertie en un pointeur appelé le *pointeur null*. Ce pointeur compare toujours le non-égal à un pointeur vers un objet ou une fonction valide. Une exception est des pointeurs vers des objets basés, qui peuvent avoir le même offset et pointent toujours vers des objets différents.

En C++ 11, le type [nullptr](../cpp/nullptr.md) doit être préféré au pointeur null de style C.

### <a name="pointer-expression-conversions"></a>Conversions d'expression de pointeur

Toute expression avec un type de tableau peut être convertie en un pointeur du même type. Le résultat de la conversion est un pointeur vers le premier élément du tableau. L'exemple suivant illustre cette conversion :

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Une expression qui entraîne une fonction qui retourne un type particulier est convertie en un pointeur vers une fonction qui retourne ce type, sauf lorsque :

- L’expression est utilisée comme opérande de l’opérateur d’adresse ( **&** ).

- L'expression est utilisée comme opérande de l'opérateur d'appel de fonction.

## <a name="reference-conversions"></a>Conversions de références

Une référence à une classe peut être convertie en une référence à une classe de base dans les cas suivants :

- La classe de base spécifiée est accessible.

- La conversion n'est pas ambiguë. (Pour plus d’informations sur les références de classe de base ambiguës, consultez [plusieurs classes de base](../cpp/multiple-base-classes.md).)

Le résultat de la conversion est un pointeur vers le sous-objet qui représente la classe de base.

## <a name="pointer-to-member"></a>Pointeur vers membre

Les pointeurs vers des membres de classe peuvent être convertis durant l'assignation, l'initialisation, la comparaison et d'autres expressions. Cette section décrit les conversions de pointeur vers membre suivantes :

### <a name="pointer-to-base-class-member"></a>Pointeur vers membre de classe de base

Un pointeur vers un membre d'une classe de base peut être converti en un pointeur vers un membre d'une classe dérivée de cette classe lorsque les conditions suivantes sont remplies :

- La conversion inverse, du pointeur vers la classe dérivée vers le pointeur de classe de base, est accessible.

- La classe dérivée n'hérite pratiquement pas de la classe de base.

Lorsque l’opérande gauche est un pointeur vers membre, l’opérande droite doit être de type pointeur vers membre ou une expression constante qui correspond à 0. Cette assignation est valide uniquement dans les cas suivants :

- L’opérande droite est un pointeur vers un membre de la même classe que l’opérande gauche.

- L’opérande gauche est un pointeur vers un membre d’une classe dérivée de façon publique et non ambiguë de la classe de l’opérande droite.

### <a name="null-pointer-to-member-conversions"></a>conversions de pointeur null en membres

Une expression constante intégrale qui prend la valeur zéro est convertie en pointeur null. Ce pointeur compare toujours le non-égal à un pointeur vers un objet ou une fonction valide. Une exception est des pointeurs vers des objets basés, qui peuvent avoir le même offset et pointent toujours vers des objets différents.

Le code suivant illustre la définition d'un pointeur désignant le membre `i` dans la classe `A`. Le pointeur, `pai`, est initialisé à 0, qui est le pointeur null.

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[C++Référence du langage](../cpp/cpp-language-reference.md)
