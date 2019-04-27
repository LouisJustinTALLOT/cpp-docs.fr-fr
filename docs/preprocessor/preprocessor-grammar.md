---
title: Syntaxe du préprocesseur
ms.date: 09/04/2018
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: 6177cf5fddba549e410842ef3f270edcc13d4782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179878"
---
# <a name="preprocessor-grammar"></a>Syntaxe du préprocesseur

*ligne de contrôle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identifier* *token-string*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identifier</em>**(** *identifier*<sub>opt</sub> **,** ... **,** *identifier*<sub>opt</sub> **)** *token-string*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *path-spec* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *path-spec* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *digit-sequence*  **"** *filename* **"**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *token-string*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *token-string*

*constant-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**defined(** *identifier* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**defined** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;toute autre expression constante

*conditionnel* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if-part* *elif-parts*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*If-partie* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if-line* *text*

*If-line* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *constant-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identifier*

*elif-parts* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-line* *text*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-line* *text*

*elif-ligne* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *constant-expression*

*partie « else »* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*else-line* *text*

*ligne Else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*ligne endif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*séquence de chiffres* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*chiffre* : un des<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*chaîne de jeton* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chaîne de jetons

*jeton* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*opérateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nom de fichier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Nom de fichier de système d’exploitation conforme

*spécification de chemin d’accès* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chemin d’accès de fichier conforme

*texte* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;N’importe quelle séquence de texte

> [!NOTE]
> Les éléments non terminaux suivants sont développées dans le [Conventions lexicales](../cpp/lexical-conventions.md) section de la *référence du langage C++*: *constante*, *expression constante* , *identificateur*, *mot clé*, *opérateur*, et */ / / délimiteur*.

## <a name="see-also"></a>Voir aussi

[Résumé de la grammaire (C/C++)](../preprocessor/grammar-summary-c-cpp.md)