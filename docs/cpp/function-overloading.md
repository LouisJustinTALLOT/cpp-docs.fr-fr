---
title: Surcharge de fonction
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: a59c0e27a4500cb20ef42e9a55b4eb0004e07f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368910"
---
# <a name="function-overloading"></a>Surcharge de fonction

C++ permet la spécification de plusieurs fonctions du même nom dans la même portée. Ces fonctions sont appelées fonctions *surchargées.* Les fonctions surchargées vous permettent de fournir différentes sémantiques pour une fonction, selon les types et le nombre d’arguments.

Par exemple, `print` une fonction `std::string` qui prend un argument peut effectuer des tâches très différentes de celle qui prend un argument de type **double**. La surcharge vous évite d’avoir `print_string` à `print_double`utiliser des noms tels que ou . Au moment de la compilation, le compilateur choisit la surcharge à utiliser en fonction du type d’arguments transmis par l’appelant.  Si vous `print(42.0)`appelez, `void print(double d)` alors la fonction sera invoquée. Si vous `print("hello world")`appelez, `void print(std::string)` alors la surcharge sera invoquée.

Vous pouvez surcharger à la fois les fonctions des membres et les fonctions non membres. Le tableau suivant montre les parties qu'une déclaration de fonction C++ utilise pour différencier les groupes de fonctions portant le même nom dans la même portée.

### <a name="overloading-considerations"></a>Considérations en matière de surcharge

|Élément de déclaration de fonction|Utilisé pour la surcharge ?|
|----------------------------------|---------------------------|
|Type de retour de fonction|Non|
|Nombre d’arguments|Oui|
|Type d’arguments|Oui|
|Présence ou absence de points de suspension|Oui|
|Utilisation de noms **dactylographes**|Non|
|Limites de tableau non spécifiées|Non|
|**const** ou **volatile**|Oui, lorsqu’il est appliqué à l’ensemble de la fonction|
|[Réf-qualificatifs](#ref-qualifiers)|Oui|

## <a name="example"></a>Exemple

L'exemple suivant illustre comment utiliser la surcharge.

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

Le code précédent illustre la surcharge de la fonction `print` dans la portée de fichier.

L’argument par défaut n’est pas considéré comme faisant partie du type de fonction. Par conséquent, il n’est pas utilisé dans la sélection des fonctions surchargées. Deux fonctions qui diffèrent uniquement de par leurs arguments par défaut sont considérées comme des définitions distinctes plutôt que comme des fonctions surchargées.

Les arguments par défaut ne peuvent pas être fournis pour les opérateurs surchargés.

## <a name="argument-matching"></a>Correspondance d’arguments

Les fonctions surchargées sont sélectionnées pour la meilleure correspondance des déclarations de fonction de la portée actuelle avec les arguments fournis dans l'appel de fonction. Si une fonction appropriée est trouvée, elle est appelée. « Approprié » dans ce contexte signifie soit :

- Une correspondance exacte a été trouvée.

- Une conversion ordinaire a été exécutée.

- Une promotion intégrale a été exécutée.

- Une conversion standard vers le type d’argument souhaité existe.

- Une conversion définie par l'utilisateur (opérateur de conversion ou constructeur) vers le type d'argument souhaité existe.

- Des arguments représentés par une ellipse ont été détectés.

Le compilateur crée un ensemble de fonctions candidates pour chaque argument. Les fonctions candidates sont des fonctions dans lesquelles l’argument réel dans cette position peut être converti vers le type de l’argument formel.

Un ensemble des « meilleures fonctions correspondantes » est généré pour chaque argument, et la fonction sélectionnée correspond à l’intersection de tous les ensembles. Si l'intersection contient plusieurs fonctions, la surcharge est ambiguë et génère une erreur. La fonction qui est sélectionnée en finalité constitue toujours une meilleure correspondance que chaque autre fonction du groupe pour au moins un argument. S’il n’y a pas de gagnant clair, l’appel de fonction génère une erreur.

Prenons les déclarations suivantes (les fonctions sont marquées `Variant 1`, `Variant 2` et `Variant 3`, afin de les identifier dans la discussion suivante) :

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Prenons l'instruction suivante :

```cpp
F1 = Add( F2, 23 );
```

L'instruction précédente génère deux ensembles :

|Ensemble 1 : Fonctions candidates qui comportent le premier argument de type fraction|Set 2: Fonctions candidates dont le deuxième argument peut être converti en type **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Variant 1|Variante 1 **(int** peut être converti en **long** à l’aide d’une conversion standard)|
|Variant 3||

Les fonctions dans l’ensemble 2 sont des fonctions pour lesquelles il existe des conversions implicites du type de paramètre réel au type de paramètre formel, et parmi ces fonctions il y a une fonction pour laquelle le «coût» de la conversion du type de paramètre réel à son type de paramètre formel est le plus petit.

L'intersection de ces deux ensembles est Variant 1. Voici un exemple d'appel de fonction ambigu :

```cpp
F1 = Add( 3, 6 );
```

L'appel de fonction précédent génère les ensembles suivants :

|Ensemble 1 : Fonctions candidates qui ont le premier argument de type **int**|Set 2: Fonctions des candidats qui ont un deuxième argument de type **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variante 2 **(int** peut être converti en **long** à l’aide d’une conversion standard)|Variante 1 **(int** peut être converti en **long** à l’aide d’une conversion standard)|

Parce que l’intersection de ces deux ensembles est vide, le compilateur génère un message d’erreur.

Pour l’appariement des arguments, une fonction avec des arguments par défaut *n* est traitée comme *n*'1 fonctions distinctes, chacune avec un nombre différent d’arguments.

L’ellipse (...) fait office de caractère générique ; elle correspond à n’importe quel argument réel. Il peut conduire à de nombreux ensembles ambigus, si vous ne concevez pas vos ensembles de fonction surchargés avec un soin extrême.

> [!NOTE]
> L’ambiguïté des fonctions surchargées ne peut être déterminée tant qu’un appel de fonction n’est pas rencontré. À ce stade, les ensembles sont générés pour chaque argument dans l'appel de fonction, et vous pouvez déterminer si une surcharge non équivoque existe. Cela signifie que les ambiguïtés peuvent rester dans votre code jusqu'à ce qu'elles soient évoquées par un appel de fonction particulier.

## <a name="argument-type-differences"></a>Différences de type d’argument

Les fonctions surchargées distinguent les types d’arguments qui acceptent différents initialiseurs. Par conséquent, un argument d’un type donné et une référence à ce type sont considérés comme identiques pour les besoins de la surcharge. Ils sont considérés comme identiques car ils acceptent les mêmes initialiseurs. Par exemple, `max( double, double )` est considéré comme identique à `max( double &, double & )`. La déclaration de deux de ces fonctions provoque une erreur.

Pour la même raison, les arguments de fonction d’un type modifié par **const** ou **volatil** ne sont pas traités différemment du type de base aux fins de la surcharge.

Cependant, le mécanisme de surcharge de fonction peut distinguer entre les références qui sont qualifiées par **const** et **volatile** et les références au type de base. Il rend le code tel que le suivant possible:

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>Output

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

Les pointeurs aux objets **const** et **volatils** sont également considérés comme différents des pointeurs au type de base aux fins de surcharge.

## <a name="argument-matching-and-conversions"></a>Correspondance et conversions d'argument

Lorsque le compilateur tente de mettre en correspondance les arguments réels et les arguments des déclarations de fonction, il peut fournir des conversions standard ou définies par l’utilisateur pour obtenir le type correct si aucune correspondance exacte n’est trouvée. L'application des conversions est soumise aux règles ci-dessous.

- Les séquences de conversions qui contiennent plusieurs conversions définies par l'utilisateur ne sont pas prises en compte.

- Les séquences de conversions qui peuvent être abrégées en supprimant les conversions intermédiaires ne sont pas prises en compte.

La séquence de conversions résultante éventuelle est qualifiée de meilleure séquence correspondante. Il existe plusieurs façons de convertir un objet de type **int** pour taper **longtemps non signé** en utilisant des conversions standard (décrites dans Les [conversions standard](../cpp/standard-conversions.md)) :

- Convertir de **l’int** à **long,** puis de **long** à **non signé long**.

- Convertir de **l’int** à **non signé longtemps**.

La première séquence, bien qu’elle atteigne l’objectif souhaité, n’est pas la meilleure séquence correspondante — une séquence plus courte existe.

Le tableau ci-dessous présente un groupe de conversions, appelées conversions ordinaires, qui ont un effet limité sur la détermination de la séquence qui représente la meilleure correspondance. Les instances dans lesquelles les conversions ordinaires affectent le choix de la séquence sont présentées dans la liste située après le tableau.

### <a name="trivial-conversions"></a>Conversions ordinaires

|Conversion depuis le type|Conversion vers le type|
|-----------------------|---------------------|
|*nom de type*|*nom de type***&**|
|*nom de type***&**|*nom de type*|
|*nom de type* **[ ]**|*nom de type*__\*__|
|*nom de type* *(argument-liste* **)** **(**|**(** __\*__ *nom de type* ) **(** *argument-liste* **)**|
|*nom de type*|**const** *type-nom*|
|*nom de type*|**nom de** *type* volatil|
|*nom de type*__\*__|**const** *type-nom*__\*__|
|*nom de type*__\*__|**nom de** *type* volatil__\*__|

La séquence dans laquelle les conversions sont tentées est la suivante :

1. Correspondance exacte. Une correspondance exacte entre les types avec lesquels la fonction est appelée et les types déclarés dans le prototype de fonction est toujours la meilleure correspondance. Les séquences de conversions ordinaires sont classées comme correspondances exactes. Cependant, les séquences qui ne font aucune de ces conversions sont considérées comme meilleures que les séquences qui convertissent :

   - Du pointeur, au pointeur à **const** (à`type` <strong>\*</strong> **const** `type` <strong>\*</strong>).

   - Du pointeur, au`type` <strong>\*</strong> pointeur à **volatile** (à **volatile** `type` <strong>\*</strong>).

   - De la référence, à`type` **&** la référence à **la const** (à **const** `type` **&**).

   - De la référence, à`type` **&** la référence à **volatile** (à **volatile** `type` **&**).

1. Correspondance avec des promotions. Toute séquence non classée comme un match exact qui ne contient que des promotions intégrales, des conversions de **flottement** à **double,** et des conversions triviales est classée comme un match en utilisant des promotions. Bien qu'elle ne soit pas aussi appropriée qu'une correspondance exacte, une correspondance avec des promotions est meilleure qu'une correspondance avec des conversions standard.

1. Correspondance avec des conversions standard. Toute séquence non classée comme correspondance exacte ou correspondance avec des promotions et qui contient uniquement des conversions standard et des conversions ordinaires est classée comme correspondance avec des conversions standard. Dans cette catégorie, les règles ci-dessous s'appliquent.

   - La conversion d’un pointeur à une classe dérivée, à un pointeur à une classe de base directe ou indirecte est préférable à la conversion à `void *` ou `const void *`.

   - La conversion d'un pointeur vers une classe dérivée, vers un pointeur vers une classe de base génère une correspondance d'autant meilleure que la classe de base est proche d'une classe de base directe. Supposons que la hiérarchie de classes s'apparente à celle de l'illustration ci-dessous.

![Graphique des conversions préférées](../cpp/media/vc391t1.gif "Graphique des conversions préférées") <br/>
Graphique montrant les conversions préférées

La conversion du type `D*` vers le type `C*` est préférable à une conversion du type `D*` vers le type `B*`. De même, la conversion du type `D*` vers le type `B*` est préférable à une conversion du type `D*` vers le type `A*`.

Cette même règle s'applique aux conversions de référence. La conversion du type `D&` vers le type `C&` est préférable à une conversion du type `D&` vers le type `B&`, et ainsi de suite.

Cette même règle s'applique aux conversions de pointeur vers membre. La conversion du type `T D::*` vers le type `T C::*` est préférable à une conversion du type `T D::*` vers le type `T B::*`, et ainsi de suite (où `T` est le type du membre).

La règle précédente s’applique uniquement à un chemin de dérivation donné. Examinez le graphique présenté dans l'illustration ci-dessous.

![Héritage&#45;multiple qui montre les conversions préférées](../cpp/media/vc391t2.gif "Héritage&#45;multiple qui montre les conversions préférées") <br/>
Graphique multi-héritage qui montre les conversions préférées

La conversion du type `C*` vers le type `B*` est préférable à une conversion du type `C*` vers le type `A*`. Cela provient du fait qu’ils se trouvent dans le même chemin et que `B*` est plus proche. Cependant, la `C*` conversion `D*` du type au type n’est pas préférable à la conversion en type `A*`; il n’y a pas de préférence parce que les conversions suivent des chemins différents.

1. Correspondance avec des conversions définies par l'utilisateur. Cette séquence ne peut pas être classée comme un match exact, un match à l’aide de promotions, ou un match à l’aide de conversions standard. La séquence doit contenir uniquement des conversions définies par l'utilisateur, des conversions standard ou des conversions ordinaires à classer comme correspondance avec des conversions définies par l'utilisateur. Une correspondance avec des conversions définies par l'utilisateur est considérée meilleure qu'une correspondance avec des points de suspension, mais pas aussi bonne qu'une correspondance avec des conversions standard.

1. Correspondance avec des points de suspension. Toute séquence qui correspond à des points de suspension dans la déclaration est classée comme correspondance avec des points de suspension. C’est considéré comme le match le plus faible.

Les conversions définies par l'utilisateur sont appliquées s'il n'existe aucune promotion ou conversion intégrée. Ces conversions sont sélectionnées en fonction du type de l’argument qui est mis en correspondance. Examinons le code ci-dessous.

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

Les conversions disponibles définies par l’utilisateur pour la classe `UDC` sont de type **int** et type **long**. Par conséquent, le compilateur considère les conversions pour le type de l'objet qui est mis en correspondance : `UDC`. Une conversion **à int** existe, et elle est sélectionnée.

Pendant le processus de mise en correspondance d’arguments, les conversions standard peuvent être appliquées à l’argument et au résultat d’une conversion définie par l’utilisateur. Par conséquent, le code suivant fonctionne :

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

Dans l’exemple précédent, la conversion définie par l’utilisateur, **opérateur long,** est invoquée pour convertir `udc` au type **long**. Si aucune conversion définie par l’utilisateur en type n’avait été `UDC` définie **depuis longtemps,** la conversion aurait été commée comme suit : le type aurait été converti en **int** de type à l’aide de la conversion définie par l’utilisateur. Ensuite, la conversion standard de type **int** au type **long** aurait été appliquée pour correspondre à l’argument dans la déclaration.

Si des conversions définies par l’utilisateur sont nécessaires pour correspondre à un argument, les conversions standard ne sont pas utilisées lors de l’évaluation du meilleur match. Même si plus d’une fonction candidate nécessite une conversion définie par l’utilisateur, les fonctions sont considérées comme égales. Par exemple :

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

Les deux `Func` versions de nécessitent une conversion définie par l’utilisateur pour convertir **int** type à l’argument de type de classe. Les conversions possibles sont indiquées ci-dessous.

- Convertir de type **int** en type `UDC1` (une conversion définie par l’utilisateur).

- Convertir de type **int** à type **long**; puis convertir `UDC2` en type (une conversion en deux étapes).

Même si la seconde nécessite à la fois une conversion standard et la conversion définie par l’utilisateur, les deux conversions sont toujours considérées comme égales.

> [!NOTE]
> Les conversions définies par l'utilisateur sont considérées comme des conversions par construction ou des conversions par initialisation (fonction de conversion). Les deux méthodes sont considérées comme égales lorsqu'il s'agit d'évaluer la meilleure correspondance.

## <a name="argument-matching-and-the-this-pointer"></a>Correspondance d’argument et pointeur this

Les fonctions des membres du groupe sont traitées différemment, selon qu’elles sont déclarées **statiques.** Étant donné que les fonctions nonstatiques ont un argument implicite qui fournit **ce** pointeur, les fonctions nonstatiques sont considérées comme ayant un argument de plus que les fonctions statiques; autrement, ils sont déclarés à l’identique.

Ces fonctions de membre nonstatiques exigent que le **pointeur** implicite corresponde au type d’objet par lequel la fonction est appelée, ou, pour les opérateurs surchargés, ils exigent que le premier argument corresponde à l’objet sur lequel l’opérateur est appliqué. (Pour plus d’informations sur les opérateurs surchargés, voir [Opérateurs surchargés](../cpp/operator-overloading.md).)

Contrairement à d’autres arguments dans les fonctions surchargées, aucun objet temporaire n’est introduit et aucune conversion n’est tentée en essayant de faire correspondre **l’argument** de ce pointeur.

Lorsque `->` l’opérateur de sélection des membres est `class_name`utilisé pour accéder à `class_name * const`une fonction membre de la classe, l’argument de **ce** pointeur a un type de . Si les membres sont déclarés comme **const** ou **volatils,** les types sont `const class_name * const` et, `volatile class_name * const`respectivement.

L'opérateur de sélection de membres `.` fonctionne exactement de la même façon, sauf qu'un opérateur (d'adresse) `&` implicite est préfixé au nom de l'objet. L'exemple suivant illustre cela :

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

L'opérande gauche des opérateurs (pointeur vers membre) `->*` et `.*` est traité de la même façon que les opérateurs (sélection de membres) `.` et `->` en ce qui concerne la correspondance d'arguments.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Réf-qualifications sur les fonctions des membres

Les qualifications réf permettent de surcharger une fonction de membre sur la base de si l’objet pointé par **cela** est une rvalue ou une lvalue.  Cette fonctionnalité peut être utilisée pour éviter les opérations de copie inutiles dans les scénarios où vous choisissez de ne pas fournir l’accès pointeur aux données. Par exemple, `C` supposons que la classe initialise certaines données dans son `get_data()`constructeur et retourne une copie de ces données dans la fonction des membres . Si un objet `C` de type est une rvalue qui est sur le `get_data() &&` point d’être détruite, alors le compilateur choisira la surcharge, qui déplace les données plutôt que de la copier.

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>Restrictions sur la surcharge

Plusieurs restrictions régissent un ensemble acceptable de fonctions surchargées :

- Deux fonctions d’un ensemble de fonctions surchargées doivent avoir des listes d’arguments différentes.

- Le surchargement de fonctions avec des listes d'arguments de même type, basées uniquement sur le type de retour, est une erreur.

     **Microsoft Spécifique**

Vous pouvez surcharger **l’opérateur nouveau** uniquement sur la base du type de retour — en particulier, sur la base du modificateur de modèle de mémoire spécifié.

**END Microsoft Spécifique**

- Les fonctions des membres ne peuvent pas être surchargées uniquement sur la base de l’un étant statique et l’autre nonstatique.

- les déclarations **de tapdef** ne définissent pas les nouveaux types; ils introduisent des synonymes pour les types existants. Ils n’affectent pas le mécanisme de surcharge. Examinons le code ci-dessous.

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Les deux fonctions précédentes ont des listes d’arguments identiques. `PSTR`est un synonyme `char *`de type . Dans la portée du membre, ce code génère une erreur.

- Les types énumérés sont des types distincts et peuvent être utilisés pour établir une distinction entre les fonctions surchargées.

- Les types " tableau de " et " pointeur à " sont considérés comme identiques dans le but de distinguer les fonctions surchargées, mais seulement pour les tableaux dimensionnés. C’est pourquoi ces fonctions surchargées entrent en conflit et génèrent un message d’erreur :

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Pour les tableaux dimensionnés de façon multiple, la deuxième et toutes les dimensions suivantes sont considérées comme faisant partie du type. Par conséquent, elles sont utilisées pour établir une distinction entre les fonctions surchargées :

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Surcharge, dépassement et dissimulation

Deux déclarations de fonction du même nom dans la même portée peuvent faire référence à la même fonction ou à deux fonctions distinctes qui sont surchargées. Si les listes d’arguments des déclarations contiennent des arguments de types équivalents (comme décrit dans la section précédente), les déclarations de fonction font référence à la même fonction. Sinon, elles font référence à deux fonctions différentes qui sont sélectionnées à l'aide de la surcharge.

La portée de la classe est strictement observée; par conséquent, une fonction déclarée dans une classe de base n’est pas dans la même portée qu’une fonction déclarée dans une classe dérivée. Si une fonction dans une classe dérivée est déclarée avec le même nom qu’une fonction virtuelle dans la classe de base, la fonction de classe dérivée *l’emporte sur* la fonction de classe de base. Pour plus d’informations, voir [Fonctions virtuelles](../cpp/virtual-functions.md).

Si la fonction de classe de base n’est pas déclarée « virtuelle », alors on dit que la fonction de classe dérivée la *cache.* Les deux prépondérer et se cacher sont distincts de la surcharge.

La portée du bloc est strictement observée; par conséquent, une fonction déclarée dans la portée du fichier n’est pas dans la même portée qu’une fonction déclarée localement. Si une fonction déclarée localement a le même nom qu'une fonction déclarée avec portée de fichier, la fonction déclarée localement masque la fonction déclarée avec portée de fichier au lieu de provoquer la surcharge. Par exemple :

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

Le code précédent montre deux définitions de la fonction `func`. La définition qui prend `char *` un argument `main` de type est locale à cause de la déclaration **de l’arrière.** Par conséquent, la définition qui prend un argument de type `func` **int** est caché, et le premier appel à est dans l’erreur.

Pour les fonctions membres surchargées, différents privilèges d'accès peuvent être accordés à différentes versions de la fonction. Elles sont encore considérées comme étant dans la portée de la classe englobante et sont donc des fonctions surchargées. Prenons le code suivant, dans lequel la fonction membre `Deposit` est surchargée ; une version est publique, l'autre privée.

Cet exemple sert à fournir une classe `Account` dans laquelle un mot de passe correct est requis pour effectuer des dépôts. C’est fait en utilisant la surcharge.

L’appel `Deposit` `Account::Deposit` à des appels la fonction de membre privé. Cet appel est `Account::Deposit` correct parce qu’il s’agit d’une fonction de membre et qu’il a accès aux membres privés de la classe.

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>Voir aussi

[Fonctions (C++)](../cpp/functions-cpp.md)
