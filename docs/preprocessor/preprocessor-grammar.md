---
title: Grammaire de préprocesseur | Microsoft Docs
ms.custom: ''
ms.date: 09/04/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56df4d0bfdaf87ace87a9f9dcbde85166929e642
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766114"
---
# <a name="preprocessor-grammar"></a>Syntaxe du préprocesseur

*ligne de contrôle*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identificateur* *chaîne de jeton*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identificateur</em>**(** *identificateur*<sub>opt</sub> **,** ... **,** *identificateur*<sub>opt</sub> **)** *chaîne de jeton*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **»** *path-spec* **»**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *spécification de chemin d’accès* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *séquence de chiffres***»** *filename* **»**<sub>opt  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *chaîne de jeton*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *chaîne de jeton*

*constant-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**défini (** *identificateur* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**défini** *identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;toute autre expression constante

*conditionnel* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*If-partie* *elif-parts*<sub>opt</sub> *partie « else »*<sub>opt</sub> *endif en ligne*

*If-partie* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*If ligne* *texte*

*If-line* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *expression constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identificateur*

*elif-parts* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-ligne* *texte*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-ligne* *texte*

*elif-ligne* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *expression constante*

*partie « else »* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ligne Else* *texte*

*ligne Else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*ligne endif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*séquence de chiffres* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*chiffre*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*séquence de chiffres* *chiffre*

*chiffre* : un des<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*chaîne de jeton* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chaîne de jetons

*jeton* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Mot clé*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Opérateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*/ / / délimiteur*

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