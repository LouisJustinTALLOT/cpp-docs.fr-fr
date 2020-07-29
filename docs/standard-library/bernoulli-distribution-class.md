---
title: bernoulli_distribution, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: 8b8e433b5ea1283fb60273a2fd21106c65867c0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230257"
---
# <a name="bernoulli_distribution-class"></a>bernoulli_distribution, classe

Génère une distribution de Bernoulli.

## <a name="syntax"></a>Syntaxe

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Paramètres

*GÉNÉRATEUR URNG*\
Moteur de générateur de nombres aléatoires uniformes. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Notes

La classe décrit une distribution qui produit des valeurs de type **`bool`** , distribuées selon la fonction de probabilité discrète de distribution de Bernoulli. Le tableau suivant contient des liens vers des articles sur différents membres.

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

Le membre de propriété `p()` retourne la valeur du paramètre de distribution actuellement stocké `p`.

Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stockés `param_type`.

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.

La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.

Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.

Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md) .

Pour plus d’informations sur la fonction de probabilité discrète de la loi de Bernoulli, consultez l’article de Wolfram MathWorld [Bernoulli Distribution](https://go.microsoft.com/fwlink/p/?linkid=398467).

## <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<random>

**Espace de noms :** std

## <a name="bernoulli_distributionbernoulli_distribution"></a><a name="bernoulli_distribution"></a>bernoulli_distribution :: bernoulli_distribution

Construit la distribution.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>Paramètres

*p*\
Paramètre de distribution `p` stocké.

*Parm*\
Structure `param_type` utilisée pour construire la distribution.

### <a name="remarks"></a>Notes

**Condition préalable :**`0.0 ≤ p ≤ 1.0`

Le premier constructeur construit un objet dont la valeur `p` stockée contient la valeur *p*.

Le deuxième constructeur construit un objet dont les paramètres stockés sont initialisés à partir de *parm*. Vous pouvez obtenir et définir les paramètres actuels d'une distribution existante en appelant la fonction membre `param()`.

## <a name="bernoulli_distributionparam_type"></a><a name="param_type"></a>bernoulli_distribution ::p aram_type

Contient les paramètres de la distribution.

struct param_type {typedef bernoulli_distribution distribution_type ; param_type (double p = 0,5); double p () const ;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>Paramètres

*p*\
Paramètre de distribution `p` stocké.

### <a name="remarks"></a>Notes

**Condition préalable :**`0.0 ≤ p ≤ 1.0`

Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
