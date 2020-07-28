---
title: :::no-loc(switch):::Instruction (C)
ms.date: 04/25/2020
f1_keywords:
- ':::no-loc(switch):::'
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C]'
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
ms.openlocfilehash: bdd6885f67728a3c81e395f05c33191156896ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220780"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`Instruction (C)

Les **`:::no-loc(switch):::`** **`:::no-loc(case):::`** instructions et permettent de contrôler les opérations conditionnelles et de branchement complexes. L' **`:::no-loc(switch):::`** instruction transfère le contrôle à une instruction dans son corps.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(switch)::: (`**&nbsp;*`expression`* &nbsp;**`)`**&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Notes

Une **`:::no-loc(switch):::`** instruction provoque le transfert du contrôle à un *`labeled-statement`* dans son corps d’instruction, en fonction de la valeur de *`expression`* .

Les valeurs de *`expression`* et de chacune *`constant-expression`* doivent avoir un type intégral. Un *`constant-expression`* doit avoir une valeur intégrale constante non ambiguë au moment de la compilation.

Le contrôle passe à l' **`:::no-loc(case):::`** instruction dont *`constant-expression`* la valeur correspond à la valeur de *`expression`* . L' **`:::no-loc(switch):::`** instruction peut inclure un nombre quelconque d' **`:::no-loc(case):::`** instances. Toutefois, deux *`constant-expression`* valeurs au sein de la même **`:::no-loc(switch):::`** instruction ne peuvent pas avoir la même valeur. L’exécution du **`:::no-loc(switch):::`** corps de l’instruction commence à la première instruction dans ou après la correspondance *`labeled-statement`* . L’exécution se poursuit jusqu’à la fin du corps ou jusqu’à ce qu’une **`:::no-loc(break):::`** instruction transfère le contrôle hors du corps.

L’utilisation de l' **`:::no-loc(switch):::`** instruction se présente généralement comme suit :

```C
:::no-loc(switch)::: ( expression )
{
    // declarations
    // . . .
    :::no-loc(case)::: constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        :::no-loc(break):::;
    :::no-loc(default)::::
        // statements executed if expression does not equal
        // any :::no-loc(case)::: constant_expression
}
```

Vous pouvez utiliser l' **`:::no-loc(break):::`** instruction pour terminer le traitement d’une instruction étiquetée particulière dans l' **`:::no-loc(switch):::`** instruction. Il se branche à la fin de l' **`:::no-loc(switch):::`** instruction. Sans **`:::no-loc(break):::`** , le programme continue jusqu’à l’instruction étiquetée suivante, en exécutant les instructions jusqu’à ce qu’une **`:::no-loc(break):::`** ou la fin de l’instruction soit atteinte. Cette continuation peut être souhaitable dans certains cas.

L' **`:::no-loc(default):::`** instruction est exécutée si aucune **`:::no-loc(case):::`** *`constant-expression`* valeur n’est égale à la valeur de *`expression`* . S’il n’existe aucune **`:::no-loc(default):::`** instruction et qu’aucune **`:::no-loc(case):::`** correspondance n’est trouvée, aucune des instructions du **`:::no-loc(switch):::`** corps n’est exécutée. Il ne peut y avoir qu’une seule **`:::no-loc(default):::`** instruction. L' **`:::no-loc(default):::`** instruction n’a pas besoin de se trouver à la fin. Elle peut apparaître n’importe où dans le corps de l' **`:::no-loc(switch):::`** instruction. Une **`:::no-loc(case):::`** **`:::no-loc(default):::`** étiquette ou ne peut apparaître qu’à l’intérieur d’une **`:::no-loc(switch):::`** instruction.

Le type de **`:::no-loc(switch):::`** *`expression`* et **`:::no-loc(case):::`** *`constant-expression`* doit être intégral. La valeur de chaque **`:::no-loc(case):::`** *`constant-expression`* doit être unique dans le corps de l’instruction.

Les **`:::no-loc(case):::`** **`:::no-loc(default):::`** étiquettes et du corps de l' **`:::no-loc(switch):::`** instruction sont significatives uniquement dans le test initial qui détermine où commence l’exécution dans le corps de l’instruction. **`:::no-loc(switch):::`** les instructions peuvent être imbriquées. Toutes les variables statiques sont initialisées avant d’être exécutées dans des **`:::no-loc(switch):::`** instructions.

> [!NOTE]
> Les déclarations peuvent apparaître à l’en-tête de l’instruction composée formant le **`:::no-loc(switch):::`** corps, mais les initialisations incluses dans les déclarations ne sont pas exécutées. L' **`:::no-loc(switch):::`** instruction transfère le contrôle directement à une instruction exécutable dans le corps, en ignorant les lignes qui contiennent des initialisations.

Les exemples suivants illustrent des **`:::no-loc(switch):::`** instructions :

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'A':
        capital_a++;
    :::no-loc(case)::: 'a':
        letter_a++;
    :::no-loc(default)::: :
        total++;
}
```

Les trois instructions du **`:::no-loc(switch):::`** corps de cet exemple sont exécutées si `c` est égal à `'A'` , car aucune **`:::no-loc(break):::`** instruction ne s’affiche avant ce qui suit **`:::no-loc(case):::`** . Le contrôle d'exécution est transféré à la première instruction (`capital_a++;`) et continue dans l'ordre à travers le reste du corps. Si `c` est égal à `'a'`, `letter_a` et `total` sont incrémentés. Seul `total` est incrémenté lorsque `c` n’est pas égal à `'A'` ou `'a'` .

```C
:::no-loc(switch):::( i )
{
    :::no-loc(case)::: -1:
        n++;
        :::no-loc(break):::;
    :::no-loc(case)::: 0 :
        z++;
        :::no-loc(break):::;
    :::no-loc(case)::: 1 :
        p++;
        :::no-loc(break):::;
}
```

Dans cet exemple, une **`:::no-loc(break):::`** instruction suit chaque instruction du **`:::no-loc(switch):::`** corps. L' **`:::no-loc(break):::`** instruction force une sortie à partir du corps de l’instruction après l’exécution d’une instruction. Si `i` est égal à -1, seul `n` est incrémenté. L' **`:::no-loc(break):::`** instruction suivante `n++;` provoque le passage du contrôle d’exécution hors du corps d’instruction, en ignorant les instructions restantes. De même, si `i` est égal à 0, seul `z` est incrémenté ; si `i` est égal à 1, seul `p` est incrémenté. La dernière **`:::no-loc(break):::`** instruction n’est pas strictement nécessaire, car le contrôle passe hors du corps à la fin de l’instruction composée. Il est inclus pour des fins de cohérence.

Une instruction unique peut comporter plusieurs **`:::no-loc(case):::`** étiquettes, comme le montre l’exemple suivant :

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'a' :
    :::no-loc(case)::: 'b' :
    :::no-loc(case)::: 'c' :
    :::no-loc(case)::: 'd' :
    :::no-loc(case)::: 'e' :
    :::no-loc(case)::: 'f' :  convert_hex(c);
}
```

Dans cet exemple, si *constant-expression* est égale à toute lettre comprise entre `'a'` et `'f'`, la fonction `convert_hex` est appelée.

### <a name="microsoft-specific"></a>Spécifique à Microsoft

Microsoft C ne limite pas le nombre de **`:::no-loc(case):::`** valeurs dans une **`:::no-loc(switch):::`** instruction. Le nombre est limité uniquement par la mémoire disponible. Le langage C ANSI requiert au moins 257 **`:::no-loc(case):::`** étiquettes pour être autorisées dans une **`:::no-loc(switch):::`** instruction.

:::no-loc(default):::Pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

## <a name="see-also"></a>Voir aussi

[:::no-loc(switch):::Instruction (C++)](../cpp/:::no-loc(switch):::-statement-cpp.md)
