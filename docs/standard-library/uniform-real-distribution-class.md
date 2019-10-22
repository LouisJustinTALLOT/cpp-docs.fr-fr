---
title: uniform_real_distribution, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_real_distribution
- random/std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::a
- random/std::uniform_real_distribution::b
- random/std::uniform_real_distribution::param
- random/std::uniform_real_distribution::min
- random/std::uniform_real_distribution::max
- random/std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_real_distribution [C++]
- std::uniform_real_distribution [C++], reset
- std::uniform_real_distribution [C++], a
- std::uniform_real_distribution [C++], b
- std::uniform_real_distribution [C++], param
- std::uniform_real_distribution [C++], min
- std::uniform_real_distribution [C++], max
- std::uniform_real_distribution [C++], param_type
- std::uniform_real_distribution [C++], param_type
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
ms.openlocfilehash: 1c63002db7de4ebce348505c4e757e6901861a93
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688821"
---
# <a name="uniform_real_distribution-class"></a>uniform_real_distribution, classe

Génère une distribution à virgule flottante uniforme (toutes les valeurs ont le même degré de probabilité) dans une plage de sortie qui est inclusive-exclusive.

## <a name="syntax"></a>Syntaxe

```cpp
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
};
```

### <a name="parameters"></a>Paramètres

*RealType* \
Le type de résultat à virgule flottante, par défaut, est **double**. Pour découvrir les types possibles, consultez [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Notes

Le modèle de classe décrit une distribution inclusive et exclusive qui produit des valeurs d’un type à virgule flottante intégral spécifié par l’utilisateur avec une distribution afin que chaque valeur soit également probable. Le tableau suivant contient des liens vers des articles sur différents membres.

||||
|-|-|-|
|[uniform_real_distribution](#uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[param_type](#param_type)|

Le membre de propriété `a()` retourne la limite minimale de la distribution stockée actuellement, tandis que `b()` retourne la limite maximale stockée actuellement. Pour cette classe de distribution, ces valeurs minimales et maximales sont les mêmes que celles retournées par les fonctions de propriété courantes `min()` et `max()` décrites dans la rubrique [\<random>](../standard-library/random.md).

Le membre de propriété `param()` définit ou retourne le package de paramètres de distribution stocké `param_type`.

Les fonctions membres `min()` et `max()` retournent respectivement le plus petit et le plus grand résultat possible.

La fonction membre `reset()` ignore toutes les valeurs mises en cache. Ainsi, le résultat de l’appel suivant à `operator()` ne dépend d’aucune valeur obtenue à partir du moteur avant l’appel.

Les fonctions membres `operator()` retournent la valeur générée suivante d’après le moteur URNG, à partir du package de paramètres actuel ou spécifié.

Pour plus d’informations sur les classes de distribution et leurs membres, consultez [\<random>](../standard-library/random.md).

## <a name="example"></a>Exemple

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_real_distribution<> distr(a,b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 1.0;
    double b_dist = 1.5;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```

## <a name="requirements"></a>spécifications

**En-tête :** \<random>

**Espace de noms :** std

## <a name="uniform_real_distribution"></a>  uniform_real_distribution::uniform_real_distribution

Construit la distribution.

```cpp
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```

### <a name="parameters"></a>Paramètres

*\*
Limite inférieure pour les valeurs aléatoires, valeur comprise.

*b* \
Limite supérieure pour les valeurs aléatoires, valeur non comprise.

*param* \
Structure `param_type` utilisée pour construire la distribution.

### <a name="remarks"></a>Notes

**Condition préalable :** `a < b`

Le premier constructeur construit un objet dont la valeur *stockée* contient la valeur *a* et dont la valeur *b* stockée contient la valeur *b*.

Le deuxième constructeur construit un objet dont les paramètres stockés sont initialisés à partir de *parm*. Vous pouvez obtenir et définir les paramètres actuels d'une distribution existante en appelant la fonction membre `param()`.

## <a name="param_type"></a>  uniform_real_distribution::param_type

Stocke tous les paramètres de la distribution.

```cpp
struct param_type {
   typedef uniform_real_distribution<result_type> distribution_type;
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Paramètres

*\*
Limite inférieure pour les valeurs aléatoires, valeur comprise.

*b* \
Limite supérieure pour les valeurs aléatoires, valeur non comprise.

\ *droit*
Objet `param_type` à comparer à this.

### <a name="remarks"></a>Notes

**Condition préalable :** `a < b`

Cette structure peut être passée au constructeur de classe de la distribution au moment de l'instanciation, à la fonction membre `param()` pour définir les paramètres stockés d'une distribution existante et à `operator()` pour une utilisation à la place des paramètres stockés.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)
