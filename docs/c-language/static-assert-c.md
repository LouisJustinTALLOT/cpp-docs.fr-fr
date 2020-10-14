---
title: Mot clé _Static_assert et macro static_assert (C11)
description: Décrit le mot clé C11 _Static_assert et la macro static_assert C11.
ms.date: 10/13/2020
f1_keywords:
- static_assert_c
- _Static_assert
helpviewer_keywords:
- assertions [C], _Static_assert, static_assert
ms.openlocfilehash: dbe49b1dcbb8dd4e0d9df678f4456bc605e01c3f
ms.sourcegitcommit: 651348f8cd92ab0d52f09e9225a7eb41562559db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92061018"
---
# <a name="_static_assert-keyword-and-static_assert-macro-c11"></a>Mot clé _Static_assert et macro static_assert (C11)

Teste une assertion au moment de la compilation. Si l’expression constante spécifiée est **`false`** , le compilateur affiche le message spécifié et la compilation échoue avec l’erreur C2338 ; sinon, il n’y a aucun effet. Nouveauté dans C11.

**`_Static_assert`** est un mot clé introduit dans C11.
**`static_assert`** est une macro, introduite dans C11, qui correspond au **`_Static_assert`** mot clé.

## <a name="syntax"></a>Syntaxe

```C
_Static_assert(constant-expression, string-literal);
static_assert(constant-expression, string-literal);
```

### <a name="parameters"></a>Paramètres

*constant-expression*\
Expression constante intégrale qui peut être évaluée au moment de la compilation. Si l’expression est égale à zéro (false), affiche le paramètre de *littéral de chaîne* et la compilation échoue avec une erreur. Si l’expression est différente de zéro (true), il n’y a aucun effet.

*littéral de chaîne*\
Message affiché si *constant-expression* a la valeur zéro (false). Le message doit être créé à l’aide du [jeu de caractères de base](../c-language/ascii-character-set.md) du compilateur. Les caractères ne peuvent pas être des [caractères multioctets ou larges](../c-language/multibyte-and-wide-characters.md).

## <a name="remarks"></a>Remarques

Le **`_Static_assert`** mot clé et la **`static_assert`** macro testent tous deux une assertion logicielle au moment de la compilation. Elles peuvent être utilisées au niveau de la portée globale ou de la fonction.

En revanche, la [macro Assert et les fonctions _ASSERT et _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) testent une assertion logicielle au moment de l’exécution et entraînent un coût d’exécution.

**Comportement spécifique à Microsoft**

En C, lorsque vous n’incluez pas `<assert.h>` , le compilateur Microsoft Visual C/C++ traite **`static_assert`** comme un mot clé mappé à **`_Static_assert`** . L’utilisation **`static_assert`** de est préférable, car le même code fonctionnera à la fois en C et en C++.

## <a name="example-of-a-compile-time-assert"></a>Exemple d’assertion au moment de la compilation

Dans l’exemple suivant, **`static_assert`** et **`_Static_assert`** sont utilisés pour vérifier le nombre d’éléments dans une énumération et les entiers sont de 32 bits de largeur.

```C
// requires /std:c11 or higher
#include <assert.h>

enum Items
{
    A,
    B,
    C,
    LENGTH
};

int main()
{
    // _Static_assert is a C11 keyword
    _Static_assert(LENGTH == 3, "Expected Items enum to have three elements");

    // Preferred: static_assert maps to _Static_Assert and is compatible with C++
    static_assert(sizeof(int) == 4, "Expecting 32 bit integers"); 

    return 0;
}
```

## <a name="requirements"></a>Configuration requise

|Macro|En-tête requis|
|-------------|---------------------|
|**`static_assert`**|\<assert.h>|

## <a name="see-also"></a>Voir également

[Macro _STATIC_ASSERT](../c-runtime-library/reference/static-assert-macro.md)\
[macro Assert et _ASSERT et fonctions _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 
 [/STD (spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)