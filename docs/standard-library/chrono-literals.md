---
description: 'En savoir plus sur : littéraux Chrono'
title: chrono, littéraux
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: 497094d920a25635496fb0aa30295d378571418c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325153"
---
# <a name="chrono-literals"></a>chrono, littéraux

(C++ 14) L' \<chrono> en-tête définit 12 [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) pour faciliter l’utilisation de littéraux qui représentent les heures, minutes, secondes, millisecondes, microsecondes et nanosecondes. Chaque littéral défini par l'utilisateur a une intégrale et une surcharge à virgule flottante. Les littéraux sont définis dans l'espace de noms inline literals::chrono_literals qui est automatiquement mis en portée quand std::chrono est dans la portée.

## <a name="syntax"></a>Syntaxe

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>Valeur de retour

Les littéraux qui acceptent un **`long long`** argument retournent une valeur ou le type correspondant. Les littéraux qui acceptent un argument à virgule flottante retournent un objet [duration](../standard-library/duration-class.md).

## <a name="example"></a>Exemple

Les exemples suivants montrent comment utiliser les littéraux chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```
