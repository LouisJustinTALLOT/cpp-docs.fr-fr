---
title: Mots clés C
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 1b49da349a6552022dfd9e8e66e85634f4694645
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838774"
---
# <a name="c-keywords"></a>Mots clés C

Les « mots clés » sont des mots qui ont une signification spéciale pour le compilateur C. Dans les phases de traduction 7 et 8, un identificateur ne peut pas avoir la même orthographe et la même casse qu'un mot clé C. (Voir une description des [phases de traduction](../preprocessor/phases-of-translation.md) dans la *Référence du préprocesseur*; pour plus d’informations sur les identificateurs, consultez [identificateurs](../c-language/c-identifiers.md).) Le langage C utilise les mots clés suivants :

:::row:::
    :::column:::
        **`auto`**\
        **`double`**\
        **`int`**\
        **`struct`**\
        **`break`**\
        **`else`**\
        **`long`**\
        **`switch`**
    :::column-end:::
    :::column:::
        **`case`**\
        **`enum`**\
        **`register`**\
        **`typedef`**\
        **`char`**\
        **`extern`**\
        **`return`**\
        **`union`**
    :::column-end:::
    :::column:::
        **`const`**\
        **`float`**\
        **`short`**\
        **`unsigned`**\
        **`continue`**\
        **`for`**\
        **`signed`**\
        **`void`**
    :::column-end:::
    :::column:::
        **`default`**\
        **`goto`**\
        **`sizeof`**\
        **`volatile`**\
        **`do`**\
        **`if`**\
        **`static`**\
        **`while`**
    :::column-end:::
:::row-end:::

Vous ne pouvez pas redéfinir les mots clés. Toutefois, vous pouvez spécifier du texte à substituer pour des mots clés avant la compilation, à l’aide des [directives de préprocesseur](../preprocessor/preprocessor-directives.md) C.

**Spécifique à Microsoft**

La norme ANSI C permet de réserver les identificateurs avec deux traits de soulignement à gauche pour les implémentations du compilateur. Par conséquent, la convention Microsoft est de faire précéder les noms des mots clés spécifiques à Microsoft de deux traits de soulignement. Ces mots ne peuvent pas être utilisés en tant que noms d'identificateurs. Pour obtenir une description des règles ANSI d’attribution de noms aux identificateurs, y compris l’utilisation de deux traits de soulignement, consultez [Identificateurs](../c-language/c-identifiers.md).

Les mots clés et les identificateurs spéciaux ci-dessous sont reconnus par le compilateur Microsoft C :

:::row:::
    :::column:::
        **`__asm`**<sup>1,3</sup>\
        **`dllimport`**<sup>2</sup>\
        **`__int8`**<sup>1,3</sup>\
        **`naked`**<sup>2</sup>\
        **`__based`**<sup>1, 3</sup>
    :::column-end:::
    :::column:::
        **`__except`**<sup>1,3</sup>\
        **`__int16`**<sup>1,3</sup>\
        **`__stdcall`**<sup>1,3</sup>\
        **`__cdecl`**<sup>1,3</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`**<sup>1,3</sup>\
        **`thread`**<sup>2</sup>\
        **`__declspec`**<sup>1,3</sup>\
        **`__finally`**<sup>1,3</sup>\
        **`__int64`**<sup>1,3</sup>
    :::column-end:::
    :::column:::
        **`__try`**<sup>1,3</sup>\
        **`dllexport`**<sup>2</sup>\
        **`__inline`**<sup>1,3</sup>\
        **`__leave`**<sup>1,3</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup> le **`__based`** mot clé a des utilisations limitées pour les compilations cibles 32 bits et 64 bits.

<sup>2</sup> il s’agit d’identificateurs spéciaux lorsqu’ils sont utilisés avec **`__declspec`** ; leur utilisation dans d’autres contextes n’est pas restreinte.

<sup>3</sup> Pour assurer la compatibilité avec les versions précédentes, ces mots clés sont disponibles à la fois avec deux traits de soulignement de début et un seul trait de soulignement de fin lorsque les extensions Microsoft sont activées.

Les extensions Microsoft sont activées par défaut. Pour garantir la portabilité totale de vos programmes, vous pouvez désactiver les extensions Microsoft en spécifiant l'option  [/Za \(Désactiver les extensions de langage](../build/reference/za-ze-disable-language-extensions.md) pendant la compilation. Dans ce cas, certains mots clés spécifiques à Microsoft sont désactivés.

Lorsque les extensions Microsoft sont activées, vous pouvez utiliser les mots clés répertoriés ci-dessus dans vos programmes. Pour la compatibilité ANSI, la plupart de ces mots clés sont précédés de deux traits de soulignement. Les quatre exceptions,,, **`dllexport`** **`dllimport`** **`naked`** et **`thread`** , sont utilisées uniquement avec **`__declspec`** et, par conséquent, ne nécessitent pas de trait de soulignement double de début. Pour assurer la compatibilité descendante, des versions à un seul trait de soulignement sont prises en charge pour les autres mots clés.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Éléments de C](../c-language/elements-of-c.md)
