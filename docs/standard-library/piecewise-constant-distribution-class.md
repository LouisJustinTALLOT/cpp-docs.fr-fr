---
title: piecewise_constant_distribution, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
ms.openlocfilehash: 6764e37b994ed76d27f88e3bdc8ec137d5e2f600
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232987"
---
# <a name="piecewise_constant_distribution-class"></a>piecewise_constant_distribution, classe

Génère une distribution constante par morceaux qui présente des intervalles de largeur variable avec une probabilité uniforme dans chaque intervalle.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Paramètres

*RealType*\
Le type de résultat à virgule flottante a comme valeur par défaut **`double`** . Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

Cette distribution d'échantillonnage présente des intervalles de largeur variable avec une probabilité uniforme dans chaque intervalle. Pour plus d’informations sur les autres distributions d’échantillonnage, consultez [piecewise_linear_distribution, classe](../standard-library/piecewise-linear-distribution-class.md) et [discrete_distribution](../standard-library/discrete-distribution-class.md).

Le tableau suivant contient des liens vers des articles sur différents membres :

||||
|-|-|-|
|[piecewise_constant_distribution](#piecewise_constant_distribution)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[param_type](#param_type)|

La fonction de propriété `intervals()` retourne un `vector<result_type>` avec l'ensemble d'intervalles stockés de la distribution.

La fonction de propriété `densities()` retourne un `vector<result_type>` avec les densités stockées pour chaque ensemble d'intervalles, qui sont calculées en fonction des poids fournis dans les paramètres du constructeur.

Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stockés `param_type`.

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.

La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.

Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.

Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md) .

## <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<random>

**Espace de noms :** std

## <a name="piecewise_constant_distributionpiecewise_constant_distribution"></a><a name="piecewise_constant_distribution"></a>piecewise_constant_distribution ::p iecewise_constant_distribution

Construit la distribution.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>Paramètres

*premieri*\
Itérateur d'entrée du premier élément de la plage de distribution.

*dernier*\
Itérateur d'entrée du dernier élément de la plage de distribution.

*firstW*\
Itérateur d'entrée du premier élément de la plage de poids.

*intervalles*\
Un [initializer_list](../cpp/initializers.md) avec les intervalles de la distribution.

*saut*\
Nombre d'éléments dans la plage de distribution.

*xmin*\
Valeur la plus faible de la plage de distribution.

*xmax*\
Valeur la plus élevée de la plage de distribution. Doit être supérieure à *xmin*.

*weightfunc*\
Objet représentant la fonction de probabilité pour la distribution. Le paramètre et la valeur de retour doivent être convertibles en **`double`** .

*Parm*\
Structure de paramètre utilisée pour construire la distribution.

### <a name="remarks"></a>Notes

Le constructeur par défaut définit les paramètres stockés pour qu'il y ait un intervalle, de 0 à 1, avec une densité de probabilité de 1.

Le constructeur de plage d'itérateurs

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

construit un objet de distribution avec des intervalles à partir des itérateurs sur la séquence [ `firstI`, `lastI`) et une séquence de poids correspondante commençant à `firstW`.

Le constructeur de listes d'initialiseurs

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

construit un objet de distribution avec des intervalles à partir des *intervalles* de la liste d’initialiseurs et des poids générés à partir de la fonction *weightfunc*.

Le constructeur défini en tant que

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

construit un objet de distribution avec des intervalles de *nombre* répartis uniformément sur [ `xmin,xmax` ], en assignant chaque pondération d’intervalle conformément à la fonction *weightfunc*, et *weightfunc* doit accepter un paramètre et avoir une valeur de retour, les deux étant convertibles en **`double`** . **Condition préalable :**`xmin < xmax`

Le constructeur défini en tant que

```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

construit un objet de distribution à l’aide de *param* comme structure de paramètre stockée.

## <a name="piecewise_constant_distributionparam_type"></a><a name="param_type"></a>piecewise_constant_distribution ::p aram_type

Stocke tous les paramètres de la distribution.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Paramètres

Consultez les paramètres de constructeur pour [piecewise_constant_distribution](#piecewise_constant_distribution).

### <a name="remarks"></a>Notes

**Condition préalable :**`xmin < xmax`

Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)\
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)
