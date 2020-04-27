---
title: switchInstruction (C)
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
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167674"
---
# <a name="opno-locswitch-statement-c"></a>switchInstruction (C)

Les **switch** instructions **case** et permettent de contrôler les opérations conditionnelles et de branchement complexes. L' **switch** instruction transfère le contrôle à une instruction dans son corps.

## <a name="syntax"></a>Syntaxe

*instruction de sélection*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***expression* **`)`** *instruction* d’expression

*instruction étiquetée*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *instruction constant-expression***`:`***statement*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *gestion*

Le contrôle passe à l’instruction dont **case** *constant-expression* correspond à la valeur de ** switch (** *expression* **)**. L' **switch** instruction peut inclure un nombre quelconque **case** d’instances. Toutefois, deux case constantes au sein de la **switch** même instruction ne peuvent pas avoir la même valeur. L’exécution du corps de l’instruction commence à l’instruction sélectionnée. Elle continue jusqu’à la fin du corps ou jusqu’à ce **break** qu’une instruction transfère le contrôle hors du corps.

L’utilisation de **switch** l’instruction se présente généralement comme suit :

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

Vous pouvez utiliser l' **break** instruction pour terminer le traitement d’une instruction étiquetée particulière **switch** dans l’instruction. Il se branche à la fin de **switch** l’instruction. Sans **break**, le programme continue jusqu’à l’instruction étiquetée suivante, en exécutant les instructions **break** jusqu’à ce qu’une ou la fin de l’instruction soit atteinte. Cette continuation peut être souhaitable dans certains cas.

L' **default** instruction est exécutée si **case** *expression constante* n’est égale à la valeur de ** switch (** *expression* **)**. S’il n’existe **default** aucune instruction et qu' **case** aucune correspondance n’est trouvée, aucune des instructions du **switch** corps n’est exécutée. Il ne peut y avoir qu' **default** une seule instruction. L' **default** instruction n’a pas besoin de se trouver à la fin. Elle peut apparaître n’importe où dans le corps **switch** de l’instruction. Une **case** étiquette **default** ou ne peut apparaître qu’à **switch** l’intérieur d’une instruction.

Le type d' **switch** *expression* et **case** de *constant-expression* doit être intégral. La valeur de chaque **case** *expression constante* doit être unique dans le corps de l’instruction.

Les **case** étiquettes **default** et du corps **switch** de l’instruction sont significatives uniquement dans le test initial qui détermine où commence l’exécution dans le corps de l’instruction. **switch** les instructions peuvent être imbriquées. Toutes les variables statiques sont initialisées avant d’être **switch** exécutées dans des instructions.

> [!NOTE]
> Les déclarations peuvent apparaître à l’en-tête de l’instruction **switch** composée formant le corps, mais les initialisations incluses dans les déclarations ne sont pas exécutées. L' **switch** instruction transfère le contrôle directement à une instruction exécutable dans le corps, en ignorant les lignes qui contiennent des initialisations.

Les exemples suivants illustrent **switch** des instructions :

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

**switch** Les trois instructions du corps de cet exemple sont exécutées si `c` est égal à `'A'`, car aucune **break** instruction ne s’affiche avant casece qui suit. Le contrôle d'exécution est transféré à la première instruction (`capital_a++;`) et continue dans l'ordre à travers le reste du corps. Si `c` est égal à `'a'`, `letter_a` et `total` sont incrémentés. Seul `total` est incrémenté lorsque `c` n’est `'A'` pas `'a'`égal à ou.

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

Dans cet exemple, une **break** instruction suit chaque instruction du **switch** corps. L' **break** instruction force une sortie à partir du corps de l’instruction après l’exécution d’une instruction. Si `i` est égal à -1, seul `n` est incrémenté. L' **break** instruction `n++;` suivante provoque le passage du contrôle d’exécution hors du corps d’instruction, en ignorant les instructions restantes. De même, si `i` est égal à 0, seul `z` est incrémenté ; si `i` est égal à 1, seul `p` est incrémenté. La dernière **break** instruction n’est pas strictement nécessaire, car le contrôle passe hors du corps à la fin de l’instruction composée. Il est inclus pour des fins de cohérence.

Une instruction unique peut comporter plusieurs **case** étiquettes, comme le montre l’exemple suivant :

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

Microsoft C ne limite pas le nombre case de valeurs dans **switch** une instruction. Le nombre est limité uniquement par la mémoire disponible. Le langage C ANSI requiert au case moins 257 étiquettes pour être **switch** autorisées dans une instruction.

default Pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

## <a name="see-also"></a>Voir aussi

[switchInstruction (C++)](../cpp/switch-statement-cpp.md)
