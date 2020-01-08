---
title: Résumé de la grammaire du préprocesseur (C++C/)
description: Définit et décrit la syntaxe de laC++ grammaire du préprocesseur Microsoft C/Compiler (MSVC).
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 99e7e8218a80e28d67767392cadfb5c4918a3bfe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302183"
---
# <a name="preprocessor-grammar-summary-cc"></a>Résumé de la grammaire du préprocesseur (C++C/)

Cet article décrit la grammaire formelle du C et C++ du préprocesseur. Il couvre la syntaxe des directives et des opérateurs de prétraitement. Pour plus d’informations, consultez directives de [préprocesseur](../preprocessor/preprocessor.md) et de [pragma et le mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="definitions"></a>Définitions du résumé de la grammaire

Les terminaux sont des points de terminaison dans une définition de syntaxe. Aucune autre résolution n'est possible. Les terminaux incluent l'ensemble des mots réservés et des identificateurs définis par l'utilisateur.

Les éléments non terminaux sont des espaces réservés dans la syntaxe. La plupart de ces éléments sont définis ailleurs dans ce résumé de syntaxe. Les définitions peuvent être récursives. Les non terminaux suivants sont définis dans la section [conventions lexicales](../cpp/lexical-conventions.md) de la  *C++ référence du langage*:

*constante*, *expression constante*, *identificateur*, *mot clé*, *opérateur*, signe de *ponctuation*

Un composant facultatif est indiqué par l'élément <sub>opt</sub> indicé. Par exemple, la syntaxe suivante indique une expression facultative entre accolades :

**{** *expression*<sub>OPT</sub> **}**

## <a name="conventions"></a>Conventions de document

Les conventions utilisent différents attributs de police pour différents composants de la syntaxe. Les symboles et les polices sont comme suit :

| Attribute | Description |
|---------------|-----------------|
| *nonterminal* | Le type italique indique des symboles non terminaux. |
| **#include** | Les symboles terminaux en gras sont des mots réservés littéraux et des symboles littéraux qui doivent être écrits comme indiqué. Les caractères situés dans ce contexte respectent toujours la casse. |
| <sub>opt</sub> | Les symboles non terminaux suivis d’<sub>opt</sub> sont toujours facultatifs.|
| police par défaut | Les caractères du jeu décrit ou répertorié dans cette police peuvent être utilisés comme symboles terminaux dans les instructions C. |

Un signe deux-points ( **:** ) qui suit un symbole non terminal introduit sa définition. D'autres définitions apparaissent sur des lignes distinctes.

Dans les blocs de syntaxe de code, ces symboles dans la police par défaut ont une signification particulière :

| Symbole | Description |
|---|---|
| \[ ] | Les crochets entourent un élément facultatif. |
| {\|} | Les accolades entourent les autres éléments, séparés par des barres verticales. |
| ... | Indique que le modèle d’élément précédent peut être répété. |

Dans les blocs de syntaxe de code, les virgules (`,`), les points (`.`), les points-virgules (`;`), les signes deux-points (`:`), les parenthèses (`( )`), les guillemets doubles (`"`) et les guillemets simples (`'`) sont des littéraux.

## <a name="grammar"></a>Grammaire du préprocesseur

*ligne de contrôle*: \
&nbsp;&nbsp;&nbsp;&nbsp; *identificateur* #define *chaîne de jeton*<sub></sub> d’identificateur\
&nbsp;&nbsp;&nbsp;&nbsp; *identificateur* **de #define (** *identificateur*<sub>OPT</sub> **,** ... **,** *identificateur*<sub>OPT</sub> **)** \ *de la chaîne de jeton*<sub></sub>
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **«** _path-spec_ **»** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _path-spec_ **>\**
&nbsp;&nbsp;&nbsp;&nbsp; **#line\** *de séquence numérique* **«** _nom de fichier_ **»** <sub></sub>
&nbsp;&nbsp; **&nbsp;&nbsp;** *identificateur* #undef
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *String Token*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*constante-expression*: \
&nbsp;&nbsp;&nbsp;&nbsp;**définie (** *identificateur* **)** \
&nbsp;&nbsp;&nbsp;&nbsp; *identificateur* défini\
&nbsp;&nbsp;&nbsp;&nbsp;toute autre expression constante

*Conditional*: \
&nbsp;&nbsp;&nbsp;&nbsp;*If-part* *Elif-parts*<sub>OPT</sub> - *part*<sub>OPT</sub>

*If-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*le* *texte* de la ligne

*If-Line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *constante-expression*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *identificateur* #ifdef
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifier*

*Elif-parties*: \
&nbsp;&nbsp;&nbsp;&nbsp;*texte* *de ligne Elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-line* *text*

*Elif-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constante-expression*

*else-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-line* *text*

*else-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*chiffre-séquence*: \
&nbsp;&nbsp;&nbsp;&nbsp;*digit*\
&nbsp;&nbsp;&nbsp; *&nbsp;chiffre* *de séquence numérique*

*digit*: un des éléments suivants : \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*jeton-chaîne*: \
&nbsp;&nbsp;&nbsp;&nbsp;chaîne de jetons

*jeton*: \
&nbsp;&nbsp;&nbsp;*mot clé* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp;*constante*\
&nbsp;&nbsp;&nbsp;*opérateur* de &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nom de fichier*: \
&nbsp;&nbsp;&nbsp;&nbsp;nom de fichier du système d’exploitation légal

*path-spec*: \
&nbsp;&nbsp;&nbsp;&nbsp;Chemin d’accès de fichier conforme

*texte*: \
&nbsp;&nbsp;&nbsp;&nbsp;toute séquence de texte

> [!NOTE]
> Les non terminaux suivants sont développés dans la section [conventions lexicales](../cpp/lexical-conventions.md) de la  *C++ référence du langage*: *constante*, *expression constante*, *identificateur*, *mot clé*, *opérateur*et signe de *ponctuation*.


## <a name="see-also"></a>Voir aussi

[Référence duC++ préprocesseur C/](../preprocessor/c-cpp-preprocessor-reference.md)
