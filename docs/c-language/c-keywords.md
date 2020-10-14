---
title: Mots clés C
description: Mots clés dans les extensions de compilateur C et Microsoft C standard.
ms.date: 10/12/2020
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: cb255e1d7ce6bc15bf13bc1e3152bc3464ea5ec2
ms.sourcegitcommit: 651348f8cd92ab0d52f09e9225a7eb41562559db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92059793"
---
# <a name="c-keywords"></a>Mots clés C

Les *Mots clés* sont des mots qui ont une signification spéciale pour le compilateur C. Dans les phases de traduction 7 et 8, un identificateur ne peut pas avoir la même orthographe et la même casse qu’un mot clé C. Pour plus d’informations, consultez [phases de traduction](../preprocessor/phases-of-translation.md) dans Référence du *préprocesseur*. Pour plus d’informations sur les identificateurs, consultez [identificateurs](../c-language/c-identifiers.md).

## <a name="standard-c-keywords"></a>Mots clés C standard

Le langage C utilise les mots clés suivants :

:::row:::
    :::column:::
        **`auto`**\
        **`break`**\
        **`case`**\
        **`char`**\
        **`const`**\
        **`continue`**\
        **`default`**\
        **`do`**\
        **`double`**\
        **`else`**\
        **`enum`**
    :::column-end:::
    :::column:::
        **`extern`**\
        **`float`**\
        **`for`**\
        **`goto`**\
        **`if`**\
        **`inline`**<sup>1, un</sup>\
        **`int`**\
        **`long`**\
        **`register`**\
        **`restrict`**<sup>1, un</sup>\
        **`return`**
    :::column-end:::
    :::column:::
        **`short`**\
        **`signed`**\
        **`sizeof`**\
        **`static`**\
        **`struct`**\
        **`switch`**\
        **`typedef`**\
        **`union`**\
        **`unsigned`**\
        **`void`**\
        **`volatile`**
    :::column-end:::
    :::column:::
        **`while`**\
        **`_Alignas`**<sup>2, un</sup>\
        **`_Alignof`**<sup>2, un</sup>\
        **`_Atomic`**<sup>2, b</sup>\
        **`_Bool`**<sup>1, un</sup>\
        **`_Complex`**<sup>1, b</sup>\
        **`_Generic`**<sup>2, un</sup>\
        **`_Imaginary`**<sup>1, b</sup>\
        **`_Noreturn`**<sup>2, un</sup>\
        **`_Static_assert`**<sup>2, un</sup>\
        **`_Thread_local`**<sup>2, b</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup>  Mots clés introduits dans ISO C99.

<sup>2</sup>   Mots clés introduits dans ISO C11.

à <sup>partir de</sup> Visual Studio 2019 version 16,8, ces mots clés sont pris en charge dans le code compilé en tant que C lorsque les **`/std:c11`** **`/std:c17`** Options du compilateur ou sont spécifiées.

<sup>b</sup>  depuis la version 16,8 de Visual Studio 2019, ces mots clés sont reconnus mais ne sont pas pris en charge par le compilateur dans le code compilé en tant que C lorsque les **`/std:c11`** **`/std:c17`** Options du compilateur ou sont spécifiées.

Vous ne pouvez pas redéfinir les mots clés. Toutefois, vous pouvez spécifier du texte pour remplacer des mots clés avant la compilation à l’aide de [directives de préprocesseur](../preprocessor/preprocessor-directives.md)C.

## <a name="microsoft-specific-c-keywords"></a>Mots clés C spécifiques à Microsoft

Les normes ANSI et ISO C autorisent la réservation des identificateurs avec deux traits de soulignement à gauche pour les implémentations du compilateur. La Convention Microsoft consiste à précéder les noms de mots clés spécifiques à Microsoft de doubles traits de soulignement. Ces mots ne peuvent pas être utilisés en tant que noms d’identificateurs. Pour obtenir une description des règles d’attribution de noms aux identificateurs, y compris l’utilisation de doubles traits de soulignement, consultez [identificateurs](../c-language/c-identifiers.md).

Les mots clés et les identificateurs spéciaux ci-dessous sont reconnus par le compilateur Microsoft C :

:::row:::
    :::column:::
        **`__asm`**<sup>5,5</sup>\
        **`dllimport`**<sup>4</sup>\
        **`__int8`**<sup>5,5</sup>\
        **`naked`**<sup>4</sup>\
        **`__based`**<sup>3, 5</sup>
    :::column-end:::
    :::column:::
        **`__except`**<sup>5,5</sup>\
        **`__int16`**<sup>5,5</sup>\
        **`__stdcall`**<sup>5,5</sup>\
        **`__cdecl`**<sup>5,5</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`**<sup>5,5</sup>\
        **`thread`**<sup>4</sup>\
        **`__declspec`**<sup>5,5</sup>\
        **`__finally`**<sup>5,5</sup>\
        **`__int64`**<sup>5,5</sup>
    :::column-end:::
    :::column:::
        **`__try`**<sup>5,5</sup>\
        **`dllexport`**<sup>4</sup>\
        **`__inline`**<sup>5,5</sup>\
        **`__leave`**<sup>5,5</sup>\
        **`static_assert`**<sup>6,3</sup>
    :::column-end:::
:::row-end:::

<sup>3</sup> le **`__based`** mot clé a des utilisations limitées pour les compilations cibles 32 bits et 64 bits.

<sup>4</sup> il s’agit d’identificateurs spéciaux lorsqu’ils sont utilisés avec **`__declspec`** ; leur utilisation dans d’autres contextes est illimitée.

<sup>5</sup> pour la compatibilité avec les versions précédentes, ces mots clés sont disponibles à la fois avec deux traits de soulignement de début et un trait de soulignement simple lorsque les extensions Microsoft sont activées.

<sup>6</sup> lorsque <Assert. h> n’est pas inclus, le compilateur Microsoft Visual C est mappé **`static_assert`** au **`_Static_assert`** mot clé C11.

Les extensions Microsoft sont activées par défaut. Pour faciliter la création de code portable, vous pouvez désactiver les extensions Microsoft en spécifiant l’option [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) pendant la compilation. Lorsque vous utilisez cette option, certains mots clés spécifiques à Microsoft sont désactivés.

Lorsque les extensions Microsoft sont activées, vous pouvez utiliser les mots clés répertoriés ci-dessus dans vos programmes. Pour la conformité aux normes, la plupart de ces mots clés sont précédés d’un trait de soulignement double. Les quatre exceptions,,, **`dllexport`** **`dllimport`** **`naked`** et **`thread`** , sont utilisées uniquement avec **`__declspec`** et ne nécessitent pas de trait de soulignement double de début. Pour assurer la compatibilité descendante, des versions à un seul trait de soulignement sont prises en charge pour les autres mots clés.

## <a name="see-also"></a>Voir également

[Éléments de C](../c-language/elements-of-c.md)
