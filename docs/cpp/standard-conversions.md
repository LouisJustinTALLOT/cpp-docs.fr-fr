---
title: Conversions standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dec0456c880fea47219dc11c509bbecac025f5d3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070581"
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
    >  Les types définis par l'utilisateur peuvent spécifier leurs propres conversions. Conversion de types définis par l’utilisateur est couverte dans [constructeurs](../cpp/constructors-cpp.md) et [Conversions](../cpp/user-defined-type-conversions-cpp.md).

Le code suivant provoque des conversions (dans cet exemple, promotions intégrales) :

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Le résultat d'une conversion est une l-value uniquement si elle produit un type référence. Par exemple, une conversion définie par l’utilisateur déclarés comme `operator int&()` retourne une référence et est une l-value. Toutefois, une conversion déclarée en tant que `operator int()`retourne un objet et n’est pas une l-value.

## <a name="integral-promotions"></a>Promotions intégrales

Les objets d'un type intégral peuvent être convertis en un autre type intégral plus large (autrement dit, un type qui peut représenter un plus grand ensemble de valeurs). Ce type étendu de conversion est appelé « promotion d'un intégral ». La promotion d'un intégral vous permet d'utiliser ce qui suit dans une expression partout où un autre type d'intégral peut être utilisé :

- Objets, des littéraux et des constantes de type **char** et **short int**

- Types d'énumération

- **int** des champs de bits

- Énumérateurs

Les promotions C++ sont de type « conservation-valeur ». Autrement dit, vous pouvez être sûr que la valeur suivent la promotion est identique à celle qui la précède. Dans les promotions de conservation-valeur, les objets de types intégraux plus courts (tels que les champs de bits ou les objets de type **char**) sont promues en type **int** si **int** peut représenter la version complète plage du type d’origine. Si **int** ne peut pas représenter la gamme complète des valeurs, puis l’objet est promu au type **unsigned int**. Bien que cette stratégie soit la même que celle utilisée par C ANSI, les conversions de type conservation-valeur ne conservent pas « l'entier non signé » de l'objet.

Les promotions de type conservation-valeur et les promotions qui conservent l'entier non signé produisent normalement les mêmes résultats. Toutefois, ils peuvent produire des résultats différents si l'objet promu est l'un des suivants :

- Un opérande de **/**, `%`, `/=`, `%=`, **<**, **\< =**, **>**, ou **>=**

   Ces opérateurs se basent sur un signe pour déterminer le résultat. Par conséquent, les promotions de type conservation-valeur et conservation-signe produisent des résultats différents lorsqu’elles sont appliquées à ces opérandes.

- L’opérande gauche de **>>** ou **>>=**

   Ces opérateurs traitent les quantités signées et non signées différemment en effectuant une opération de décalage. Pour les quantités signées, le déplacement de la quantité vers la droite provoque la propagation du bit de signe dans les positions binaires libérées. Pour les quantités non signées, les positions binaires libérées sont vides.

- Argument vers une fonction ou un opérande surchargé d’un opérateur surchargé qui dépend de l’entier non signé du type de l’opérande pour la correspondance d’argument. (Consultez [opérateurs surchargés](../cpp/operator-overloading.md) pour plus d’informations sur la définition des opérateurs surchargés.)

## <a name="integral-conversions"></a>Conversions intégrales

Des conversions intégrales sont effectuées entre les types intégraux. Les types intégraux sont **char**, **int**, et **long** (et le **court**, **signé**et **non signé** versions de ces types).

**Signé en non signé**

Les objets de types intégraux signés peuvent être convertis en types non signés correspondants. Lorsque ces conversions ont lieu, le modèle binaire réel ne change pas. Toutefois, l'interprétation des données change. Prenons le code suivant :

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

Dans l’exemple précédent, un **signés short**, `i`, est défini et initialisé à un nombre négatif. L’expression `(u = i)` provoque `i` à convertir en un **unsigned short** avant l’assignation à `u`.

**Non signé en signé**

Les objets de types intégraux non signés peuvent être convertis en types signés correspondants. Toutefois, cette conversion peut entraîner une erreur d'interprétation des données si la valeur de l'objet non signé se situe en dehors de la plage qui peut être représentée par le type signé, comme illustré dans l'exemple suivant :

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

Dans l’exemple précédent, `u` est un **unsigned short** objet intégral qui doit être convertie en une quantité signée pour évaluer l’expression `(i = u)`. Étant donné que sa valeur ne peut pas être correctement représentée dans un **signés short**, les données soit interprété à tort comme indiqué.

## <a name="floating-point-conversions"></a>Conversions de nombres à virgule flottante

Un objet de type flottant peut être converti sans risque en type flottant plus précis. Cela permet de ne pas perdre de signification lors de la conversion. Par exemple, les conversions de **float** à **double** ou à partir de **double** à **long double** sont sécurisées et la valeur est inchangée.

Un objet de type flottant peut également être converti en type moins précis, s'il se trouve dans une plage qui peut être représentée par ce type. (Consultez [limites flottantes](../cpp/floating-limits.md) pour les plages de type flottant.) Si la valeur d'origine ne peut pas être représentée précisément, elle peut être convertie à la valeur représentable inférieure ou supérieure suivante. Si aucune valeur de ce type n'existe, le résultat n'est pas défini. Prenons l'exemple suivant :

```cpp
cout << (float)1E300 << endl;
```

La valeur maximale représentable par type **float** est 3.402823466E38 — un nombre largement inférieur à 1E300. Par conséquent, le nombre est converti à l’infini, et le résultat est « inf ».

## <a name="conversions-between-integral-and-floating-point-types"></a>Conversions entre types intégraux et à virgule flottante

Certaines expressions peuvent provoquer la conversion des objets de type flottant en types intégraux, ou vice versa. Lorsqu'un objet de type intégral est converti en type flottant et que la valeur d'origine ne peut pas être représentée précisément, elle peut être convertie à la valeur représentable inférieure ou supérieure suivante.

Lorsqu'un objet de type flottant est converti en type intégral, la partie fractionnaire est tronquée. Aucun arrondi n'est effectué pendant le processus de conversion. Troncation signifie qu’un nombre 1,3 est converti à 1 et-1.3 est converti en -1.

## <a name="arithmetic-conversions"></a>Conversions arithmétiques

De nombreux opérateurs binaires (présentés dans [Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)) effectuent les conversions d’opérandes et produire des résultats de la même façon. La façon dont ces opérateurs effectuent les conversions s'appelle « conversions arithmétiques habituelles ». Les conversions arithmétiques des opérandes de différents types natifs sont exécutées comme indiqué dans le tableau suivant. Les types typedef se comportent selon leurs types natifs sous-jacents.

### <a name="conditions-for-type-conversion"></a>Conditions pour la conversion de type

|Conditions remplies|Conversion|
|--------------------|----------------|
|Des opérandes est de type **long double**.|Autre opérande est converti en type **long double**.|
|Précédant la condition non remplie et des opérandes est de type **double**.|Autre opérande est converti en type **double**.|
|Précédant les conditions non remplies et des opérandes est de type **float**.|Autre opérande est converti en type **float**.|
|Conditions précédentes non remplies (aucun des opérandes n’est de type flottant).|Les promotions intégrales sont exécutées sur les opérandes comme suit :<br /><br />-Si des opérandes est de type **long non signé**, l’autre opérande est converti en type **unsigned long**.<br />-Si la condition précédente non remplie et si des opérandes est de type **long** et l’autre de type **unsigned int**, les deux opérandes sont convertis en type **unsigned long**.<br />-Si les deux conditions précédentes ne sont pas remplies et si des opérandes est de type **long**, l’autre opérande est converti en type **long**.<br />-Si les trois conditions précédentes ne sont pas remplies et si des opérandes est de type **unsigned int**, l’autre opérande est converti en type **unsigned int**.<br />-Si aucune des conditions précédentes sont remplies, les deux opérandes sont convertis en type **int**.|

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

Dans l'exemple précédent, la première instruction affiche la multiplication de deux types intégraux, `iVal` et `ulVal`. La condition remplie est qu’aucun des opérandes est de type flottant et un opérande est de type **unsigned int**. Par conséquent, l’autre opérande, `iVal`, est converti en type **unsigned int**. Le résultat est assigné à `dVal`. La condition remplie est qu’un opérande est de type **double**; par conséquent, le **unsigned int** résultat de la multiplication est converti en type **double**.

La deuxième instruction dans l’exemple précédent montre l’ajout d’un **float** et un type intégral, `fVal` et `ulVal`. Le `ulVal` variable est convertie en type **float** (troisième condition dans le tableau). Le résultat de l’addition est converti en type **double** (seconde condition dans la table) et assignée à `dVal`.

## <a name="pointer-conversions"></a>Conversions de pointeurs

Les pointeurs peuvent être convertis durant l'assignation, l'initialisation, la comparaison et d'autres expressions.

### <a name="pointer-to-classes"></a>Pointeur vers classes

Il existe deux cas dans lesquels un pointeur vers une classe peut être converti en un pointeur vers une classe de base.

Dans le premier cas, la classe de base spécifiée est accessible et la conversion est n'est pas ambiguë. (Consultez [plusieurs Classes de Base](../cpp/multiple-base-classes.md) pour plus d’informations sur les références de classe de base ambiguës.)

L'accessibilité d'une classe de base dépend du type d'héritage utilisé dans la dérivation. Prenons l'héritage illustré dans l'illustration suivante.

![Graphique d’héritage base&#45;d’accessibilité de classe](../cpp/media/vc38xa1.gif "vc38XA1") graphique d’héritage pour une Illustration de l’accessibilité de classe de Base

Le tableau suivant indique l'accessibilité de la classe de base d'après la situation illustrée.

### <a name="base-class-accessibility"></a>Accessibilité de la classe de base

|Type de fonction|Dérivation|Conversion de<br /><br /> B * à A\* juridique ?|
|----------------------|----------------|-------------------------------------------|
|Fonction externe (hors portée de classe)|Private|Non|
||Protected|Non|
||Public|Oui|
|Fonction membre B (dans la portée B)|Private|Oui|
||Protected|Oui|
||Public|Oui|
|Fonction membre C (dans la portée C)|Private|Non|
||Protected|Oui|
||Public|Oui|

Dans le second cas, un pointeur vers une classe peut être converti en pointeur vers une classe de base lorsque vous utilisez une conversion de type explicite. (Consultez [opérateur de Conversion de Type explicite](explicit-type-conversion-operator-parens.md) pour plus d’informations sur les conversions de type explicite.)

Le résultat de ce type de conversion est un pointeur vers le « sous-objet », la partie de l'objet qui est complètement décrite par la classe de base.

Le code suivant définit deux classes, `A` et `B`, où `B` est dérivée de `A`. (Pour plus d’informations sur l’héritage, consultez [les Classes dérivées](../cpp/inheritance-cpp.md).) Il définit ensuite , un objet de type `bObject`, et deux pointeurs (`B` et `pB`) qui pointent vers l'objet.

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

Le pointeur `pA` est de type `A *`, ce qui peut être interprété comme suit : « pointeur vers un objet de type `A` ». Membres de `bObject` `(`comme `BComponent` et `BMemberFunc`) sont propres au type `B` et sont donc inaccessibles via `pA`. Le pointeur `pA` autorise l'accès uniquement aux caractéristiques (fonctions membres et données) de l'objet définies dans la classe `A`.

### <a name="pointer-to-function"></a>Pointeur vers fonction

Un pointeur vers une fonction peut être converti en type `void *`, si type `void *` est assez grand pour contenir ce pointeur.

### <a name="pointer-to-void"></a>Pointeur vers void

Des pointeurs en type **void** peuvent être convertis en pointeurs vers un autre type, mais uniquement avec un cast de type explicite (contrairement à c). Un pointeur vers n’importe quel type peut être converti implicitement vers un pointeur vers un type **void**. Un pointeur vers un objet incomplet d’un type peut être converti en un pointeur vers **void** (implicitement) et inversement (explicitement). Le résultat de ce type de conversion est égal à la valeur du pointeur d'origine. Un objet est considéré incomplet s'il est déclaré, mais que les informations sont insuffisantes pour déterminer sa taille ou sa classe de base.

Un pointeur vers n’importe quel objet qui n’est pas **const** ou **volatile** peut être implicitement converti en un pointeur de type `void *`.

### <a name="const-and-volatile-pointers"></a>Pointeurs const et volatile

C++ ne fournit pas une conversion standard à partir d’un **const** ou **volatile** type en un type qui n’est pas **const** ou **volatile**. Cependant, toute sorte de conversion peut être spécifiée à l'aide de casts de type explicite (y compris les conversions qui ne sont pas sécurisées).

> [!NOTE]
>  Les pointeurs C++ vers des membres, à l'exception des pointeurs vers des membres statiques, sont différents des pointeurs normaux et n'ont pas les mêmes conversions standard. Les pointeurs vers des membres statiques sont des pointeurs normaux et ils ont les mêmes conversions que les pointeurs normaux.

### <a name="null-pointer-conversions"></a>Conversions de pointeurs null

Une expression constante intégrale qui correspond à zéro ou cette expression casté en un type pointeur, est convertie en un pointeur appelé pointeur null. Ce pointeur est assuré de ne pas être considéré comme égal à un pointeur désignant un objet ou une fonction valide quelconque (à l'exception des pointeurs désignant des objets basés, qui peuvent avoir le même décalage et pointer néanmoins sur des objets différents).

Dans C ++ 11 les [nullptr](../cpp/nullptr.md) type doit être préféré au pointeur null de style C.

### <a name="pointer-expression-conversions"></a>Conversions d'expression de pointeur

Toute expression avec un type de tableau peut être convertie en un pointeur du même type. Le résultat de la conversion est un pointeur vers le premier élément du tableau. L'exemple suivant illustre cette conversion :

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Une expression qui entraîne une fonction qui retourne un type particulier est convertie en un pointeur vers une fonction qui retourne ce type, sauf lorsque :

- L’expression est utilisée en tant qu’opérande pour l’opérateur address-of (**&**).

- L’expression est utilisée comme opérande de l’opérateur d’appel de fonction.

## <a name="reference-conversions"></a>Conversions de références

Une référence à une classe peut être convertie en une référence à une classe de base dans les cas suivants :

- La classe de base spécifiée n’est accessible.

- La conversion n'est pas ambiguë. (Consultez [plusieurs Classes de Base](../cpp/multiple-base-classes.md) pour plus d’informations sur les références de classe de base ambiguës.)

Le résultat de la conversion est un pointeur vers le sous-objet qui représente la classe de base.

## <a name="pointer-to-member"></a>Pointeur vers membre

Les pointeurs vers des membres de classe peuvent être convertis durant l'assignation, l'initialisation, la comparaison et d'autres expressions. Cette section décrit les conversions de pointeur vers membre suivantes :

## <a name="pointer-to-base-class-member"></a>Pointeur vers membre de classe de base

Un pointeur vers un membre d'une classe de base peut être converti en un pointeur vers un membre d'une classe dérivée de cette classe lorsque les conditions suivantes sont remplies :

- La conversion inverse, du pointeur vers la classe dérivée vers le pointeur de classe de base, est accessible.

- La classe dérivée n'hérite pratiquement pas de la classe de base.

Lorsque l'opérande gauche est un pointeur vers membre, l'opérande droite doit être de type pointeur vers membre ou une expression constante qui correspond à 0. Cette assignation est valide uniquement dans les cas suivants :

- L'opérande droite est un pointeur vers un membre de la même classe que l'opérande gauche.

- L'opérande gauche est un pointeur vers un membre d'une classe dérivée de façon publique et non ambiguë de la classe de l'opérande droite.

## <a name="integral-constant-conversions"></a>Conversions de constantes intégrales

Une expression constante intégrale qui correspond à la valeur zéro est convertie en un pointeur appelé « pointeur null ». Ce pointeur est assuré de ne pas être considéré comme égal à un pointeur désignant un objet ou une fonction valide quelconque (à l'exception des pointeurs désignant des objets basés, qui peuvent avoir le même décalage et pointer néanmoins sur des objets différents).

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

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)