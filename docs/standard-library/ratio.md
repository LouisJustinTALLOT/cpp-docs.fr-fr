---
description: 'En savoir plus sur : &lt; ratio&gt;'
title: '&lt;ratio&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ratio>
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
ms.openlocfilehash: a32a8252347de1e6d7bfd5ffd29927c779ce8489
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126557"
---
# <a name="ltratiogt"></a>&lt;ratio&gt;

Incluez l’en-tête standard \<ratio> pour définir les constantes et les modèles utilisés pour stocker et manipuler les nombres rationnels au moment de la compilation.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ratio>
```

### <a name="ratio-template"></a>Modèle de ratio

```cpp
template<std::intmax_t Numerator, std::intmax_t Denominator = 1>
struct ratio // holds the ratio of Numerator to Denominator
{
   static constexpr std::intmax_t num;
   static constexpr std::intmax_t den;
   typedef ratio<num, den> type;
}
```

Le modèle `ratio` définit les constantes statiques `num` et `den` , par exemple, `num`  /  `den` = = numérateur/dénominateur et n' `num` `den` a aucun facteur commun. `num` / `den` est la valeur représentée par le modèle de classe. Par conséquent, `type` désigne l’instanciation `ratio<num, den>` .

### <a name="specializations"></a>Spécialisations

\<ratio> définit également les spécialisations de `ratio` qui se présentent sous la forme suivante.

`template <class R1, class R2> struct ratio_specialization`

Chaque spécialisation prend deux paramètres de modèle qui doivent également être des spécialisations de `ratio`. La valeur de `type` est déterminée par une opération logique associée.

|Nom|Valeur `type`|
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

Pour plus de commodité, l’en-tête définit les ratios pour les préfixes SI standard :

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
