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
ms.openlocfilehash: 5858447602a28dcc5573aa3138e869d106b5aa23
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587365"
---
# <a name="switch-statement-c"></a>`switch`Instruction (C)

Les __`switch`__ instructions __`case`__ et permettent de contrôler les opérations conditionnelles et de branchement complexes. L' __`switch`__ instruction transfère le contrôle à une instruction dans son corps.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Notes 

Une __`switch`__ instruction provoque le transfert du contrôle à *`labeled-statement`* un dans son corps d’instruction, en fonction de la *`expression`* valeur de.

Les valeurs de *`expression`* et de *`constant-expression`* chacune doivent avoir un type intégral. Un *`constant-expression`* doit avoir une valeur intégrale constante non ambiguë au moment de la compilation.

Le contrôle passe à **`case`** l’instruction *`constant-expression`* dont la valeur correspond à *`expression`* la valeur de. L' __`switch`__ instruction peut inclure un nombre quelconque __`case`__ d’instances. Toutefois, deux *`constant-expression`* valeurs au sein de la __`switch`__ même instruction ne peuvent pas avoir la même valeur. L’exécution du __`switch`__ corps de l’instruction commence à la première instruction dans ou après *`labeled-statement`* la correspondance. L’exécution se poursuit jusqu’à la fin du corps ou jusqu' __`break`__ à ce qu’une instruction transfère le contrôle hors du corps.

L’utilisation de __`switch`__ l’instruction se présente généralement comme suit :

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

Vous pouvez utiliser l' __`break`__ instruction pour terminer le traitement d’une instruction étiquetée particulière __`switch`__ dans l’instruction. Il se branche à la fin de __`switch`__ l’instruction. Sans __`break`__, le programme continue jusqu’à l’instruction étiquetée suivante, en exécutant les instructions __`break`__ jusqu’à ce qu’une ou la fin de l’instruction soit atteinte. Cette continuation peut être souhaitable dans certains cas.

L' __`default`__ instruction est exécutée si __`case`__ *`constant-expression`* aucune valeur n’est égale à la *`expression`* valeur de. S’il n’existe __`default`__ aucune instruction et qu' __`case`__ aucune correspondance n’est trouvée, aucune des instructions du __`switch`__ corps n’est exécutée. Il ne peut y avoir qu' __`default`__ une seule instruction. L' __`default`__ instruction n’a pas besoin de se trouver à la fin. Elle peut apparaître n’importe où dans le corps __`switch`__ de l’instruction. Une __`case`__ étiquette __`default`__ ou ne peut apparaître qu’à __`switch`__ l’intérieur d’une instruction.

Le type de __`switch`__ *`expression`* et __`case`__ *`constant-expression`* doit être intégral. La valeur de chaque __`case`__ *`constant-expression`* doit être unique dans le corps de l’instruction.

Les __`case`__ étiquettes __`default`__ et du corps __`switch`__ de l’instruction sont significatives uniquement dans le test initial qui détermine où commence l’exécution dans le corps de l’instruction. __`switch`__ les instructions peuvent être imbriquées. Toutes les variables statiques sont initialisées avant d’être __`switch`__ exécutées dans des instructions.

> [!NOTE]
> Les déclarations peuvent apparaître à l’en-tête de l’instruction __`switch`__ composée formant le corps, mais les initialisations incluses dans les déclarations ne sont pas exécutées. L' __`switch`__ instruction transfère le contrôle directement à une instruction exécutable dans le corps, en ignorant les lignes qui contiennent des initialisations.

Les exemples suivants illustrent __`switch`__ des instructions :

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

__`switch`__ Les trois instructions du corps de cet exemple sont exécutées si `c` est égal à `'A'`, car aucune __`break`__ instruction ne s’affiche avant __`case`__ ce qui suit. Le contrôle d'exécution est transféré à la première instruction (`capital_a++;`) et continue dans l'ordre à travers le reste du corps. Si `c` est égal à `'a'`, `letter_a` et `total` sont incrémentés. Seul `total` est incrémenté lorsque `c` n’est `'A'` pas `'a'`égal à ou.

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

Dans cet exemple, une __`break`__ instruction suit chaque instruction du __`switch`__ corps. L' __`break`__ instruction force une sortie à partir du corps de l’instruction après l’exécution d’une instruction. Si `i` est égal à -1, seul `n` est incrémenté. L' __`break`__ instruction `n++;` suivante provoque le passage du contrôle d’exécution hors du corps d’instruction, en ignorant les instructions restantes. De même, si `i` est égal à 0, seul `z` est incrémenté ; si `i` est égal à 1, seul `p` est incrémenté. La dernière __`break`__ instruction n’est pas strictement nécessaire, car le contrôle passe hors du corps à la fin de l’instruction composée. Il est inclus pour des fins de cohérence.

Une instruction unique peut comporter plusieurs __`case`__ étiquettes, comme le montre l’exemple suivant :

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

Microsoft C ne limite pas le nombre __`case`__ de valeurs dans __`switch`__ une instruction. Le nombre est limité uniquement par la mémoire disponible. Le langage C ANSI requiert au __`case`__ moins 257 étiquettes pour être __`switch`__ autorisées dans une instruction.

default Pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

## <a name="see-also"></a>Voir aussi

[switchInstruction (C++)](../cpp/switch-statement-cpp.md)
