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

*declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaration-Specifiers* *attribute-SEQ*<sub>OPT</sub> *init-declarator-List*<sub>OPT</sub> **;**

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;de déclaration de *Storage-Class-* specifier *-Specifiers*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclaration de *type-* spécificateurs *-spécificateurs*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;de la déclaration de *qualificateur de type* &nbsp; *-spécificateurs*<sub>OPT</sub>

*attribute-SEQ* :&nbsp;&nbsp;&nbsp;&nbsp;/\* \*propres à Microsoft /<br/>
attribut d' *attribut* &nbsp;&nbsp;&nbsp;&nbsp; *-Seq*<sub>OPT</sub>

*attribut* : l’un des&nbsp;&nbsp;&nbsp;&nbsp;/\* \*propres à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall __cdecl](../cpp/thiscall.md) [__inline __vectorcall](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-List* **,** *init-declarator*

*init-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclarateur* **=** *initialiseur* /pour l’initialisation scalaire \* \*    /

*storage-class-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-modifier-SEQ* **)**  /\* \*spécifique à Microsoft /

*type-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* \*propres à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* \*propres à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* \*propres à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* \*propres à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-qualifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *déclarateur* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constante-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *Parameter-type-list* **)**  /\* déclarateur New-style \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-List*<sub>OPT</sub> **)**  /\* déclarateur de style obsolète \*/

*pointer* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>opt</sub> *pointeur* *de liste de qualificateurs de type* <strong>\*</strong>

*parameter-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* Liste de paramètres \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;la *liste des paramètres* **,...**

*parameter-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,** *paramètre-DECLARATION*

*type-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-List* *-qualifier*

*enum-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*d' **énumération** <sub>OPT</sub> **{** *Enumerator-List* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur* d' **énumération**

*enumerator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerator-List* **,** *énumérateur*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumeration-constant* **=** constant *-expression*

*enumeration-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*struct-or-union-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identificateur *struct-or-Union* *identifier*<sub>OPT</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur* *struct-or-Union*

*struct-or-union* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;struct- *declaration-list* *struct-DECLARATION*

*struct-declaration* :<br/>
&nbsp;&nbsp;&nbsp;spécificateur de &nbsp; *-qualifier-qualificateur* - *declarator* -List **;**

*specifier-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;spécificateur *de spécificateur de type* &nbsp; *-qualificateur-qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;spécificateur de *qualificateur de type* &nbsp; *-qualificateur-qualifier-List*<sub>OPT</sub>

*struct-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;struct *-déclarateur* struct- *declarator-List* **,** *struct-declarator*

*struct-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;du *déclarateur* *de spécificateur de type* &nbsp;<sub>OPT</sub> **:** *constant-expression*

*parameter-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* * /\** déclarateur nommé \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *abstract-declarator*<sub>OPT</sub> /\* \*déclarateur anonyme /

*identifier-list* : /\* Pour le déclarateur de style ancien \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur-liste* **,** *identificateur*

*abstract-declarator* : /\* Utilisé avec des déclarateurs anonymes \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-abstract-declarator*

*direct-abstract-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>OPT</sub> **[** *constant-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>OPT</sub> **(** *Parameter-type-list*<sub>OPT</sub> **)**

*initializer* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **}**  /\* pour l’initialisation d’agrégats \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **,}**

*initializer-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer-List* **,** *initializer*

*type-name* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-List* *abstract-declarator*<sub>OPT</sub>

*typedef-name* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*Extended-decl-modifier-SEQ*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*spécifique à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier-SEQ* *Extended-decl-modifier*

*Extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*spécifiques à Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)<br/>
[Grammaire de la structure de la phrase](../c-language/phrase-structure-grammar.md)<br/>
[Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)
