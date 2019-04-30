---
title: '#define, Directive (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: 8a0cc7e7836a0c82c72055fe8d9e7497995485d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409900"
---
# <a name="define-directive-cc"></a>#define, directive (C/C++)

Le **#define** crée un *macro*, qui est l’association d’un identificateur ou un identificateur paramétré avec une chaîne de jeton. Une fois la macro définie, le compilateur peut substituer la chaîne de jeton pour chaque occurrence de l'identificateur dans le fichier source.

## <a name="syntax"></a>Syntaxe

`#define` *identifier* *token-string*<sub>opt</sub>

`#define` *identificateur* `(` *identificateur*<sub>opt</sub> `,` *...*  `,` *identificateur*<sub>opt</sub> `)` *chaîne de jeton*<sub>opt</sub>

## <a name="remarks"></a>Notes

Le **#define** directive indique au compilateur de remplacer *chaîne de jeton* pour chaque occurrence de *identificateur* dans le fichier source. Le *identificateur* est remplacé uniquement lorsqu’il forme un jeton. Autrement dit, *identificateur* n’est pas remplacé s’il apparaît dans un commentaire, dans une chaîne, ou en tant que partie d’un identificateur plus long. Pour plus d’informations, consultez [jetons](../cpp/tokens-cpp.md).

Le *chaîne de jeton* argument se compose d’une série de jetons, tels que les mots clés, des constantes ou des instructions complètes. Un ou plusieurs espaces blancs doivent séparer *chaîne de jeton* de *identificateur*. Cet espace blanc n'est pas considéré comme faisant partie du texte substitué, pas plus que tout espace blanc qui suit le dernier jeton du texte.

Un `#define` sans un *chaîne de jeton* supprime les occurrences de *identificateur* à partir du fichier source. Le *identificateur* reste défini et peut être testé à l’aide de la `#if defined` et `#ifdef` directives.

La deuxième forme de syntaxe définit une macro de type fonction avec des paramètres. Cette forme accepte la liste facultative des paramètres qui doivent apparaître entre parenthèses. Une fois la macro définie, chaque occurrence suivante de *identificateur*( *identificateur*<sub>opt</sub>,..., *identificateur* <sub>opt</sub> ) est remplacé par une version de la *chaîne de jeton* argument qui a des arguments réels sont remplacés par des paramètres formels.

Les noms de paramètres formels apparaissent dans *chaîne de jeton* pour marquer les emplacements où les valeurs réelles sont substituées. Chaque nom de paramètre peut apparaître plusieurs fois dans *chaîne de jeton*, et les noms peuvent apparaître dans n’importe quel ordre. Le nombre d'arguments de l'appel doit correspondre au nombre de paramètres de la définition de macro. L'utilisation répandue des parenthèses garantit que les arguments réels complexes sont interprétés correctement.

Les paramètres formels de la liste sont séparés par des virgules. Chaque nom contenu dans la liste doit être unique et la liste doit être placée entre parenthèses. Aucun espace ne peut séparer *identificateur* et la parenthèse ouvrante. Utilisez la concaténation de ligne : placer une barre oblique inverse (`\`) immédiatement avant le caractère de saut de ligne, pour les longues directives sur plusieurs lignes de code source. La portée d’un nom de paramètre formel s’étend vers la nouvelle ligne se termine *chaîne de jeton*.

Lorsqu’une macro a été définie dans la deuxième forme de syntaxe, les instances textuelles suivantes suivies d’une liste d’arguments indiquent un appel de macro. Les arguments réels qui suivent une instance de *identificateur* dans le fichier source sont mis en correspondance avec des paramètres formels correspondants dans la définition de macro. Chaque paramètre formel dans *chaîne de jeton* qui n’est pas précédé par un enchaînement (`#`), de charizing (`#@`), ou de collage de jeton (`##`) (opérateur), ou pas suivi par un `##` opérateur, est remplacé par l’argument réel correspondant. Toutes les macros figurant dans l'argument réel sont développées avant que la directive ne remplace le paramètre formel. (Les opérateurs sont décrits dans [opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md).)

Les exemples suivants de macros comportant des arguments illustrent la deuxième forme de la **#define** syntaxe :

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Les arguments avec des effets secondaires provoquent des résultats inattendus générés par les macros. Un paramètre formel donné peut apparaître plusieurs fois dans *chaîne de jeton*. Si ce paramètre formel est remplacé par une expression à effets secondaires, l'expression, avec ses effets secondaires, peut être évaluée plusieurs fois. (Consultez les exemples sous [opérateurs de collage de jeton (##)](../preprocessor/token-pasting-operator-hash-hash.md).)

La directive `#undef` entraîne l'oubli de la définition de préprocesseur d'un identificateur. Consultez [la Directive #undef](../preprocessor/hash-undef-directive-c-cpp.md) pour plus d’informations.

Si le nom de la macro définie apparaît dans *chaîne de jeton* (même comme résultat d’une autre expansion macro), il n’est pas développé.

Une seconde **#define** pour une macro portant le même nom génère un avertissement, sauf si la deuxième séquence de jeton est identique à la première.

**Section spécifique à Microsoft**

Microsoft C/C++ vous permet de redéfinir une macro si la nouvelle définition est syntaxiquement identique à la définition d'origine. En d'autres termes, les deux définitions peuvent avoir des noms de paramètres différents. Ce comportement diffère de C ANSI, ce qui nécessite que les deux définitions soient lexicalement identiques.

Par exemple, les deux macros suivantes sont identiques, sauf pour les noms de paramètres. C ANSI n’autorise pas de redéfinition, mais Microsoft C/C++ le compile sans erreur.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

En revanche, les deux macros suivantes ne sont pas identiques et généreront un avertissement dans Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**FIN de la section spécifique à Microsoft**

Cet exemple illustre la **#define** directive :

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

**Section spécifique à Microsoft**

Définition des macros et constantes avec le [/D](../build/reference/d-preprocessor-definitions.md) option du compilateur a le même effet que d’utiliser un **#define** directive de préprocesseur au début de votre fichier. Jusqu'à 30 macros peuvent être définies avec l'option /D.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)