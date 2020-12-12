---
description: 'En savoir plus sur : `switch` Statement (C)'
title: switch  Instruction (C)
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: f6089505ac47c657e151a60d6061a79ee0fd3cb8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114440"
---
# <a name="no-locswitch-statement-c"></a>`switch` Instruction (C)

Les **`switch`** **`case`** instructions et permettent de contrôler les opérations conditionnelles et de branchement complexes. L' **`switch`** instruction transfère le contrôle à une instruction dans son corps.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`switch (`**&nbsp;*`expression`* &nbsp;**`)`**&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`case`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`default`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Notes

Une **`switch`** instruction provoque le transfert du contrôle à un *`labeled-statement`* dans son corps d’instruction, en fonction de la valeur de *`expression`* .

Les valeurs de *`expression`* et de chacune *`constant-expression`* doivent avoir un type intégral. Un *`constant-expression`* doit avoir une valeur intégrale constante non ambiguë au moment de la compilation.

Le contrôle passe à l' **`case`** instruction dont *`constant-expression`* la valeur correspond à la valeur de *`expression`* . L' **`switch`** instruction peut inclure un nombre quelconque d' **`case`** instances. Toutefois, deux *`constant-expression`* valeurs au sein de la même **`switch`** instruction ne peuvent pas avoir la même valeur. L’exécution du **`switch`** corps de l’instruction commence à la première instruction dans ou après la correspondance *`labeled-statement`* . L’exécution se poursuit jusqu’à la fin du corps ou jusqu’à ce qu’une **`break`** instruction transfère le contrôle hors du corps.

L’utilisation de l' **`switch`** instruction se présente généralement comme suit :

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

Vous pouvez utiliser l' **`break`** instruction pour terminer le traitement d’une instruction étiquetée particulière dans l' **`switch`** instruction. Il se branche à la fin de l' **`switch`** instruction. Sans **`break`** , le programme continue jusqu’à l’instruction étiquetée suivante, en exécutant les instructions jusqu’à ce qu’une **`break`** ou la fin de l’instruction soit atteinte. Cette continuation peut être souhaitable dans certains cas.

L' **`default`** instruction est exécutée si aucune **`case`** *`constant-expression`* valeur n’est égale à la valeur de *`expression`* . S’il n’existe aucune **`default`** instruction et qu’aucune **`case`** correspondance n’est trouvée, aucune des instructions du **`switch`** corps n’est exécutée. Il ne peut y avoir qu’une seule **`default`** instruction. L' **`default`** instruction n’a pas besoin de se trouver à la fin. Elle peut apparaître n’importe où dans le corps de l' **`switch`** instruction. Une **`case`** **`default`** étiquette ou ne peut apparaître qu’à l’intérieur d’une **`switch`** instruction.

Le type de **`switch`** *`expression`* et **`case`** *`constant-expression`* doit être intégral. La valeur de chaque **`case`** *`constant-expression`* doit être unique dans le corps de l’instruction.

Les **`case`** **`default`** étiquettes et du corps de l' **`switch`** instruction sont significatives uniquement dans le test initial qui détermine où commence l’exécution dans le corps de l’instruction. **`switch`** les instructions peuvent être imbriquées. Toutes les variables statiques sont initialisées avant d’être exécutées dans des **`switch`** instructions.

> [!NOTE]
> Les déclarations peuvent apparaître à l’en-tête de l’instruction composée formant le **`switch`** corps, mais les initialisations incluses dans les déclarations ne sont pas exécutées. L' **`switch`** instruction transfère le contrôle directement à une instruction exécutable dans le corps, en ignorant les lignes qui contiennent des initialisations.

Les exemples suivants illustrent des **`switch`** instructions :

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

Les trois instructions du **`switch`** corps de cet exemple sont exécutées si `c` est égal à `'A'` , car aucune **`break`** instruction ne s’affiche avant ce qui suit **`case`** . Le contrôle d'exécution est transféré à la première instruction (`capital_a++;`) et continue dans l'ordre à travers le reste du corps. Si `c` est égal à `'a'`, `letter_a` et `total` sont incrémentés. Seul `total` est incrémenté lorsque `c` n’est pas égal à `'A'` ou `'a'` .

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

Dans cet exemple, une **`break`** instruction suit chaque instruction du **`switch`** corps. L' **`break`** instruction force une sortie à partir du corps de l’instruction après l’exécution d’une instruction. Si `i` est égal à -1, seul `n` est incrémenté. L' **`break`** instruction suivante `n++;` provoque le passage du contrôle d’exécution hors du corps d’instruction, en ignorant les instructions restantes. De même, si `i` est égal à 0, seul `z` est incrémenté ; si `i` est égal à 1, seul `p` est incrémenté. La dernière **`break`** instruction n’est pas strictement nécessaire, car le contrôle passe hors du corps à la fin de l’instruction composée. Il est inclus pour des fins de cohérence.

Une instruction unique peut comporter plusieurs **`case`** étiquettes, comme le montre l’exemple suivant :

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

Dans cet exemple, si *constant-expression* est égale à toute lettre comprise entre `'a'` et `'f'`, la fonction `convert_hex` est appelée.

### <a name="microsoft-specific"></a>Spécifique à Microsoft

Microsoft C ne limite pas le nombre de **`case`** valeurs dans une **`switch`** instruction. Le nombre est limité uniquement par la mémoire disponible. Le langage C ANSI requiert au moins 257 **`case`** étiquettes pour être autorisées dans une **`switch`** instruction.

defaultPour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

## <a name="see-also"></a>Voir aussi

[switch Instruction (C++)](../cpp/switch-statement-cpp.md)
