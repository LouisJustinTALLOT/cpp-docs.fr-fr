---
title: discrete_distribution, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: 5bf5deec5820976c742efa490bf02d0c0d830a09
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464894"
---
# <a name="discretedistribution-class"></a>discrete_distribution, classe

Génère une distribution d'entiers discrète qui présente des intervalles de largeur uniforme avec une probabilité uniforme dans chaque intervalle.

## <a name="syntax"></a>Syntaxe

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Paramètres

*IntType*<br/>
Le type de résultat entier, valeur par défaut est **int**. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Cette distribution d'échantillonnage présente des intervalles de largeur uniforme avec une probabilité uniforme dans chaque intervalle. Pour plus d’informations sur les autres distributions d’échantillonnage, consultez [piecewise_linear_distribution, classe](../standard-library/piecewise-linear-distribution-class.md) et [piecewise_constant_distribution, classe](../standard-library/piecewise-constant-distribution-class.md).

Le tableau suivant contient des liens vers des articles sur différents membres :

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

La fonction de propriété `vector<double> probabilities()` retourne les probabilités individuelles pour chaque entier généré.

Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md).

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

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
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
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
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
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution

Construit la distribution.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Paramètres

*firstW*<br/>
Premier itérateur dans la liste à partir duquel construire la distribution.

*lastW*<br/>
Dernier itérateur dans la liste à partir duquel construire la distribution (non compris car les itérateurs utilisent un élément vide pour la fin).

*weightlist*<br/>
[initializer_list](../cpp/initializers.md) à partir duquel construire la distribution.

*count*<br/>
Nombre d'éléments dans la plage de distribution. Si `count==0`, équivalent au constructeur par défaut (génère toujours zéro).

*low*<br/>
Valeur la plus faible de la plage de distribution.

*high*<br/>
Valeur la plus élevée de la plage de distribution.

*weightfunc*<br/>
Objet représentant la fonction de probabilité pour la distribution. Le paramètre et la valeur de retour doivent être convertibles en **double**.

*parm*<br/>
Structure `param_type` utilisée pour construire la distribution.

### <a name="remarks"></a>Notes

Le constructeur par défaut construit un objet dont la valeur de probabilité stockée a un élément avec la valeur 1. Cela aboutit à une distribution qui génère toujours zéro.

Le constructeur de plage d’itérateurs qui a les paramètres *firstW* et *lastW* construit un objet de distribution à l’aide de valeurs de poids prises dans les itérateurs sur la séquence d’intervalle [*firstW*, *lastW*).

Le constructeur de liste d’initialiseurs qui a un paramètre *weightlist* construit un objet de distribution avec des poids de la liste d’initialiseurs *weightlist*.

Le constructeur qui a les paramètres *ount*, *low*, *igh* et *weightfunc* construit un objet de distribution initialisé selon ces règles :

- Si *count* < 1, **n** = 1 et, par conséquent, est équivalent au constructeur par défaut qui génère toujours zéro.
- Si *count* > 0, **n** = *count*. Fourni **d** = (*haute* - *faible*) / **n** est supérieur à zéro, à l’aide de **d** uniforme sous-plages, chaque poids est affecté comme suit : `weight[k] = weightfunc(x)`, où **x** = *faible* + **k**  *  **d** + **d** / 2, pour **k** = 0,..., **n** - 1.

Le constructeur qui a un paramètre `param_type` *parm* construit un objet de distribution qui utilise *parm* comme structure de paramètre stockée.

## <a name="param_type"></a>  discrete_distribution::param_type

Stocke tous les paramètres de la distribution.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Paramètres

*firstW*<br/>
Premier itérateur dans la liste à partir duquel construire la distribution.

*lastW*<br/>
Dernier itérateur dans la liste à partir duquel construire la distribution (non compris car les itérateurs utilisent un élément vide pour la fin).

*weightlist*<br/>
[initializer_list](../cpp/initializers.md) à partir duquel construire la distribution.

*count*<br/>
Nombre d'éléments dans la plage de distribution. Si *count* a la valeur 0, il est équivalent au constructeur par défaut (génère toujours zéro).

*low*<br/>
Valeur la plus faible de la plage de distribution.

*high*<br/>
Valeur la plus élevée de la plage de distribution.

*weightfunc*<br/>
Objet représentant la fonction de probabilité pour la distribution. Le paramètre et la valeur de retour doivent être convertibles en **double**.

*right*<br/>
Objet `param_type` à comparer à this.

### <a name="remarks"></a>Notes

Ce package de paramètres peut être passé à `operator()` pour générer la valeur de retour.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
