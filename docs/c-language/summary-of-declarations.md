---
title: Résumé des déclarations
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170434"
---
# <a name="summary-of-declarations"></a>Résumé des déclarations

*déclaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *attribute-SEQ*<sub>OPT</sub> *init-declarator-List*<sub>OPT</sub> **;**

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*attribute-SEQ* &nbsp; &nbsp; &nbsp; &nbsp; / :\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*attribute* *attribute-seq*<sub>opt</sub>

*attribut* : l’un&nbsp; &nbsp; &nbsp; &nbsp; / des\* éléments spécifiques à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-List*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*\* *initializer* initialiseur / de déclarateur pour l’initialisation scalaire**=**    \*/

*storage-class-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**annuler**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**statique**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**externes**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *Extended-decl-modifier-SEQ* **)**  / \* spécifique à Microsoft\*/

*type-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nullité**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Résumé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**tiers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8** / __int8\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16** / __int16\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32** / __int32\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64** / __int64\* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dissocié**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Cliquer**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**abonné**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**non signé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-Union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*qualificateur de type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*déclarateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *déclarateur* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constante-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator* **(** *Parameter-type-list* **)**  / \* New-style declarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator* **(** *identifier-List*<sub>OPT</sub> **)**  / \* -déclarateur de style obsolète\*/

*pointeur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List-*<sub>opt</sub> *pointeur* opt

*Parameter-type-list*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; :&nbsp; &nbsp; &nbsp; &nbsp; liste de paramètres&nbsp; &nbsp; / \*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de paramètres*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de paramètres* **,...**

*liste de paramètres*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Déclaration de paramètre*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,** *paramètre-DECLARATION*

*type-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*qualificateur de type*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*enum-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identificateur d' **énumération** *identifier*<sub>OPT</sub> **{** *Enumerator-List* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur* d' **énumération**

*énumérateur-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumérateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerator-List* **,** *énumérateur*

*énumérateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumération-constante*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*énumération-* **=** constante constante *-expression*

*énumération-constante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

*spécificateur struct-or-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur struct-or-Union* *identifier*<sub>OPT</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-ou-union* *identificateur*

*struct-or-union* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**modélis**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UE**

*struct-declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*struct-DECLARATION*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;struct *-déclarateur* struct *-declarator-List* **,** *struct-declarator*

*déclarateur de struct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>OPT</sub> **:** *constant-expression*

*parameter-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *déclarateur*  / \* nommé declarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *abstract-* declarator<sub>OPT</sub>  / \* du déclarateur anonyme\*/

*identifier-List*:/\* pour le déclarateur de style ancien\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur-liste* **,** *identificateur*

*abstract-declarator*:/\* utilisé avec les déclarateurs anonymes\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dirigé*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-abstract-declarator*

*direct-abstract-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *abstract-declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>OPT</sub> **[** *constante-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>OPT</sub> **(** *Parameter-type-list*<sub>OPT</sub> **)**

*initialiseur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignation-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *initializer-List* **}**  / \* pour l’initialisation d’agrégats\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *initializer-List* **,}**

*initialiseur-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer-List* **,** *initialiseur*

*nom de type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*nom de typedef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

*Extended-decl-modifier-SEQ*:&nbsp; &nbsp; &nbsp; &nbsp; / \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*Extended-decl-modifier*:&nbsp; &nbsp; &nbsp; &nbsp; / \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nue**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)<br/>
[Grammaire de la structure des expressions](../c-language/phrase-structure-grammar.md)<br/>
[Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)
