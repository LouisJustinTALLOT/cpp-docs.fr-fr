---
title: '#define, directive (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: e9e5b7a02ee55c05aa44278fbceb9c42f372c443
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506673"
---
# <a name="define-directive-cc"></a>#define, directive (C/C++)

L' **#define** crée une *macro*, qui est l’Association d’un identificateur ou d’un identificateur paramétré avec une chaîne de jeton. Une fois la macro définie, le compilateur peut substituer la chaîne de jeton pour chaque occurrence de l'identificateur dans le fichier source.

## <a name="syntax"></a>Syntax

> **#define** *identificateur* *de #define jeton-chaîne*<sub>OPT</sub>\
> **#define** *identificateur* **de #define (** *identificateur*<sub>OPT</sub>**,** ... **,** *identificateur*<sub>OPT</sub> **)** *jeton-chaîne*<sub>OPT</sub>

## <a name="remarks"></a>Remarques

La directive **#define** oblige le compilateur à substituer la *chaîne de jeton* pour chaque occurrence de l' *identificateur* dans le fichier source. L' *identificateur* est remplacé uniquement lorsqu’il forme un jeton. Autrement dit, l' *identificateur* n’est pas remplacé s’il apparaît dans un commentaire, dans une chaîne ou dans le cadre d’un identificateur plus long. Pour plus d’informations, consultez [jetons](../cpp/character-sets.md).

L’argument *Token-String* se compose d’une série de jetons, tels que des mots clés, des constantes ou des instructions complètes. Un ou plusieurs espaces blancs doivent séparer *Token-String* de l' *identificateur*. Cet espace blanc n'est pas considéré comme faisant partie du texte substitué, pas plus que tout espace blanc qui suit le dernier jeton du texte.

Un `#define` sans *jeton-chaîne* supprime les occurrences de l' *identificateur* dans le fichier source. L' *identificateur* reste défini et peut être testé à l’aide des `#if defined` `#ifdef` directives et.

La deuxième forme de syntaxe définit une macro de type fonction avec des paramètres. Cette forme accepte la liste facultative des paramètres qui doivent apparaître entre parenthèses. Une fois la macro définie, chaque occurrence suivante de l' *identificateur*( *identificateur*<sub>OPT</sub>,..., *identificateur*<sub>OPT</sub> ) est remplacée par une version de l’argument de *chaîne de jeton* dont les arguments réels sont remplacés par des paramètres formels.

Les noms de paramètres formels apparaissent dans *Token-String* pour marquer les emplacements où les valeurs réelles sont substituées. Chaque nom de paramètre peut apparaître plusieurs fois dans la *chaîne de jeton*, et les noms peuvent apparaître dans n’importe quel ordre. Le nombre d'arguments de l'appel doit correspondre au nombre de paramètres de la définition de macro. L'utilisation répandue des parenthèses garantit que les arguments réels complexes sont interprétés correctement.

Les paramètres formels de la liste sont séparés par des virgules. Chaque nom contenu dans la liste doit être unique et la liste doit être placée entre parenthèses. Aucun espace ne peut séparer l' *identificateur* et la parenthèse ouvrante. Utiliser la concaténation de ligne : Placez une barre oblique inverse ( `\` ) juste avant le caractère de saut de ligne, pour les directives longues sur plusieurs lignes sources. La portée d’un nom de paramètre formel s’étend jusqu’à la nouvelle ligne qui termine *Token-String*.

Lorsqu’une macro a été définie dans la deuxième forme de syntaxe, les instances textuelles suivantes suivies d’une liste d’arguments indiquent un appel de macro. Les arguments réels qui suivent une instance d' *identificateur* dans le fichier source sont mis en correspondance avec les paramètres formels correspondants dans la définition de macro. Chaque paramètre formel dans une *chaîne de jeton* qui n’est pas précédé d’un opérateur String ( `#` ), Charing ( `#@` ) ou de l’opérateur de collage de jeton ( `##` ), ou qui n’est pas suivi d’un `##` opérateur, est remplacé par l’argument réel correspondant. Toutes les macros figurant dans l'argument réel sont développées avant que la directive ne remplace le paramètre formel. (Les opérateurs sont décrits dans [opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md).)

Les exemples suivants de macros avec arguments illustrent la deuxième forme de la syntaxe **#define** :

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Les arguments avec des effets secondaires provoquent des résultats inattendus générés par les macros. Un paramètre formel donné peut apparaître plusieurs fois dans une *chaîne de jeton*. Si ce paramètre formel est remplacé par une expression à effets secondaires, l'expression, avec ses effets secondaires, peut être évaluée plusieurs fois. (Consultez les exemples sous [opérateur de collage de jeton (# #)](../preprocessor/token-pasting-operator-hash-hash.md).)

La directive `#undef` entraîne l'oubli de la définition de préprocesseur d'un identificateur. Pour plus d’informations, consultez [la Directive #undef](../preprocessor/hash-undef-directive-c-cpp.md) .

Si le nom de la macro définie se produit dans la *chaîne de jeton* (même suite à une autre expansion macro), il n’est pas développé.

Une deuxième **#define** pour une macro portant le même nom génère un avertissement à moins que la deuxième séquence de jeton soit identique à la première.

**Spécifique à Microsoft**

Microsoft C/C++ vous permet de redéfinir une macro si la nouvelle définition est syntaxiquement identique à la définition d'origine. En d'autres termes, les deux définitions peuvent avoir des noms de paramètres différents. Ce comportement diffère de la norme ANSI C, qui requiert que les deux définitions soient lexicalement identiques.

Par exemple, les deux macros suivantes sont identiques, sauf pour les noms de paramètres. ANSI C n’autorise pas ce type de redéfinition, mais Microsoft C/C++ le compile sans erreur.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

En revanche, les deux macros suivantes ne sont pas identiques et généreront un avertissement dans Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**FIN spécifique à Microsoft**

Cet exemple illustre la directive **#define** :

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

La première instruction définit l'identificateur `WIDTH` en tant que constante entière 80, puis définit `LENGTH` en tant que `WIDTH` et la constante entière 10. Chaque occurrence de `LENGTH` est remplacée par (`WIDTH + 10`). Ensuite, chaque occurrence de `WIDTH + 10` est remplacée par l'expression (`80 + 10`). Les parenthèses autour de `WIDTH + 10` sont importantes car elles contrôlent l'interprétation d'instructions telles que :

```C
var = LENGTH * 20;
```

Après l'étape de prétraitement, l'instruction devient :

```C
var = ( 80 + 10 ) * 20;
```

ce qui correspond à 1800. Sans parenthèses, le résultat est :

```C
var = 80 + 10 * 20;
```

qui prend la valeur 280.

**Spécifique à Microsoft**

La définition des macros et des constantes avec l’option de compilateur [/d](../build/reference/d-preprocessor-definitions.md) a le même effet que l’utilisation d’une **#define** directive de prétraitement au début de votre fichier. Jusqu'à 30 macros peuvent être définies avec l'option /D.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
