---
title: Grammaire du préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222263"
---
# <a name="preprocessor-grammar"></a>Grammaire du préprocesseur

*ligne de contrôle*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identificateur* *jeton-chaîne* <sub>OPT</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identificateur* **(** &#x2800;identificateur&#x200B;<sub>OPT</sub> **,** ... **,** *identificateur* &#x200B; <sub></sub>opt&#x2800; **)** *jeton-chaîne*<sub>OPT</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _chemin d’accès-spécification_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** _chemin d’accès-spécification_ **\<** **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *chiffre-séquence* **"** _nom du fichier_ **"** &#x200B; <sub>OPT</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *jeton-chaîne*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*constante-expression*: \
&nbsp;&nbsp;&nbsp;&nbsp;**defined (** &#x2800;*identificateur*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**défini** *identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp;toute autre expression constante

*Conditional*: \
&nbsp;&nbsp;&nbsp;&nbsp;*If-part* *Elif-parties* <sub>OPT</sub> *autre partie* <sub>OPT</sub> *endif-ligne*

*If-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*If-Line* *texte*

*If-Line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *constant-expression*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifier*

*Elif-parties*: \
&nbsp;&nbsp;&nbsp;&nbsp;*ligne Elif* *texte*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-line* *text*

*Elif-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constant-expression*

*else-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-line* *text*

*else-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-ligne*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*chiffre-séquence*: \
&nbsp;&nbsp;&nbsp;&nbsp;*caractères*\
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*digit*: un des éléments suivants: \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*jeton-chaîne*: \
&nbsp;&nbsp;&nbsp;&nbsp;Chaîne de jetons

*jeton*: \
&nbsp;&nbsp;&nbsp;&nbsp;*mot*\
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp;*suivantes*\
&nbsp;&nbsp;&nbsp;&nbsp;*and*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*nom de fichier*: \
&nbsp;&nbsp;&nbsp;&nbsp;Nom de fichier du système d’exploitation légal

*path-spec*: \
&nbsp;&nbsp;&nbsp;&nbsp;Chemin d’accès de fichier conforme

*texte*: \
&nbsp;&nbsp;&nbsp;&nbsp;Toute séquence de texte

> [!NOTE]
> Les non terminaux suivants sont développés dans la section [conventions lexicales](../cpp/lexical-conventions.md) de la  *C++ référence du langage*: *constante*, *expression constante*, *identificateur*, *mot clé*, *opérateur*etsigne de ponctuation.

## <a name="see-also"></a>Voir aussi

[Résumé de la grammaire (C++C/)](../preprocessor/grammar-summary-c-cpp.md)
