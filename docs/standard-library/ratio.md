---
title: '&lt;ratio&gt;'
ms.date: 11/04/2016
f1_keywords:
- ratio/std::mega
- ratio/std::peta
- ratio/std::ratio_greater
- ratio/std::micro
- ratio/std::ratio_add
- ratio/std::ratio_not_equal
- ratio/std::hecto
- ratio/std::nano
- ratio/std::ratio_less_equal
- ratio/std::ratio_less
- ratio/std::centi
- ratio/std::ratio_greater_equal
- ratio/std::ratio_subtract
- <ratio>
- ratio/std::atto
- ratio/std::tera
- ratio/std::milli
- ratio/std::ratio_multiply
- ratio/std::kilo
- ratio/std::ratio_divide
- ratio/std::giga
- ratio/std::pico
- ratio/std::femto
- ratio/std::ratio_equal
- ratio/std::ratio
- ratio/std::exa
- ratio/std::deci
- ratio/std::deca
ms.assetid: 8543e912-2d84-45ea-b3c0-bd7bfacee405
ms.openlocfilehash: 4279aa75bf4e9b8a0c7a86f102f70164bbb620e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609002"
---
# <a name="ltratiogt"></a>&lt;ratio&gt;

La structure ratio fournit l’en-tête standard \<ratio> qui permet de définir les constantes et les modèles qui sont utilisés pour stocker et manipuler des nombres rationnels au moment de la compilation.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ratio>
```

### <a name="ratio-template"></a>Modèle de rapport

```cpp
template<std::intmax_t Numerator, std::intmax_t Denominator = 1>
struct ratio // holds the ratio of Numerator to Denominator
{
   static constexpr std::intmax_t num;
   static constexpr std::intmax_t den;
   typedef ratio<num, den> type;
}
```

Le modèle `ratio` définit les constantes statiques `num` et `den` telles que `num`  /  `den` == Numérateur / Dénominateur et `num` et `den` n’ont aucuns facteurs communs. `num` / `den` est la valeur qui est représentée par la classe de modèle. Par conséquent, `type` désigne l’instanciation `ratio<num, den>`.

### <a name="specializations"></a>Spécialisations

\<ratio> définit également des spécialisations de `ratio` qui ont la forme suivante.

`template <class R1, class R2> struct ratio_specialization`

Chaque spécialisation prend deux paramètres de modèle qui doivent également être des spécialisations de `ratio`. La valeur de `type` est déterminée par une opération logique associée.

|Name|Valeur `type`|
|----------|------------------|
|`ratio_add`|`R1 + R2`|
|`ratio_divide`|`R1 / R2`|
|`ratio_equal`|`R1 == R2`|
|`ratio_greater`|`R1 > R2`|
|`ratio_greater_equal`|`R1 >= R2`|
|`ratio_less`|`R1 < R2`|
|`ratio_less_equal`|`R1 <= R2`|
|`ratio_multiply`|`R1 * R2`|
|`ratio_not_equal`|`!(R1 == R2)`|
|`ratio_subtract`|`R1 - R2`|

### <a name="typedefs"></a>typedefs

Pour plus de commodité, l’en-tête définit des rapports pour les préfixes SI standards :

```cpp
typedef ratio<1, 1000000000000000000> atto;
typedef ratio<1, 1000000000000000> femto;
typedef ratio<1, 1000000000000> pico;
typedef ratio<1, 1000000000> nano;
typedef ratio<1, 1000000> micro;
typedef ratio<1, 1000> milli;
typedef ratio<1, 100> centi;
typedef ratio<1, 10> deci;
typedef ratio<10, 1> deca;
typedef ratio<100, 1> hecto;
typedef ratio<1000, 1> kilo;
typedef ratio<1000000, 1> mega;
typedef ratio<1000000000, 1> giga;
typedef ratio<1000000000000, 1> tera;
typedef ratio<1000000000000000, 1> peta;
typedef ratio<1000000000000000000, 1> exa;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
