---
title: Résumé des déclarations | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e5fe380d41b5d1e58a63b1aa0b99a239dee515
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392521"
---
# <a name="summary-of-declarations"></a>Résumé des déclarations
`declaration`:  
 *declaration-specifiers attribute-seq* <sub>opt</sub> *init-declarator-list*<sub>opt</sub>**;**  
  
 /\* *attribute-seq* est spécifique de Microsoft */  
  
 *declaration-specifiers* :  
 *storage-class-specifier declaration-specifiers*<sub>opt</sub>  
  
 *type-specifier declaration-specifiers*<sub>opt</sub>  
  
 *type-qualifier declaration-specifiers*<sub>opt</sub>  
  
 *attribute-seq* :            /\* *attribute-seq* est spécifique de Microsoft \*/  
 *attribute attribute-seq* <sub>opt</sub>  
  
 *attribute* : un des éléments suivants :      /* Spécifique de Microsoft \*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init-declarator-list* :  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator* :  
 *declarator*  
  
 *declarator*  **=**  *initializer* /* Pour l’initialisation scalaire \*/  
  
 *storage-class-specifier* :  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec (**  *extended-decl-modifier-seq*  **)** /* Spécifique de Microsoft \*/  
  
 *type-specifier* :  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` /* Spécifique de Microsoft \*/  
  
 `__int16` /* Spécifique de Microsoft \*/  
  
 `__int32` /* Spécifique de Microsoft \*/  
  
 `__int64` /* Spécifique de Microsoft \*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *type-qualifier* :  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator* :  
 *identifier*  
  
 **(**  *declarator*  **)**  
  
 *direct-declarator*  **[**  *constant-expression* <sub>opt</sub>**]**  
  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* Déclarateur de nouveau style \*/  
  
 *direct-declarator*  **(**  *identifier-list*<sub>opt</sub>**)** /* Déclarateur de style obsolète \*/  
  
 `pointer`:  
 **\*** *type-qualifier-list*<sub>opt</sub>  
  
 **\*** *type-qualifier-list*<sub>opt</sub>`pointer`  
  
 *parameter-type-list* :                           /\* La liste de paramètres \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list* :  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *type-qualifier-list* :  
 *type-qualifier*  
  
 *type-qualifier-list type-qualifier*  
  
 *enum-specifier* :  
 **enum**  *identifier*<sub>opt</sub>**{** *enumerator-list* **}**  
  
 **enum**  *identifier*  
  
 *enumerator-list* :  
 *enumerator*  
  
 *enumerator-list*  **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration-constant*  
  
 *enumeration-constant*  **=**  *constant-expression*  
  
 *enumeration-constant* :  
 *identifier*  
  
 *struct-or-union-specifier* :  
 *struct-or-union identifier*<sub>opt</sub>**{** *struct-declaration-list* **}** *struct-or-union identifier*  
  
 *struct-or-union* :  
 **struct**  
  
 **union**  
  
 *struct-declaration-list* :  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 *struct-declaration* :  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list* :  
 *type-specifier specifier-qualifier-list*<sub>opt</sub>  
  
 *type-qualifier specifier-qualifier-list*<sub>opt</sub>  
  
 *struct-declarator-list* :  
 *struct-declarator struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator* :  
 *declarator*  
  
 *type-specifier declarator*<sub>opt</sub> **:** *constant-expression*  
  
 *parameter-declaration* :  
 *declaration-specifiers declarator* /* Déclarateur nommé \*/  
  
 *declaration-specifiers abstract-declarator*<sub>opt</sub>**/\*** Déclarateur anonyme **\*/**  
  
 *identifier-list* : **/\*** Pour le déclarateur de style ancien **\* /**  
 *identifier*  
  
 *identifier-list*  **,**  *identifier*  
  
 *abstract-declarator* : **/\*** Utilisé avec des déclarateurs anonymes **\*/**  
 *pointer*  
  
 `pointer`<sub>opt</sub>*direct-abstract-declarator*  
  
 *direct-abstract-declarator* :  
 **(**  *abstract-declarator*  **)**  
  
 *direct-abstract-declarator*<sub>opt</sub>**[** *constant-expression*<sub>opt</sub>**]**  
  
 *direct-abstract-declarator*<sub>opt</sub>**(** *parameter-type-list* <sub>opt</sub>**)**  
  
 *initializer* :  
 *assignment-expression*  
  
 **{**  *initializer-list*  **}** /* Pour l’initialisation d’agrégats \*/  
  
 **{**  *initializer-list*  **, }**  
  
 *initializer-list* :  
 *initializer*  
  
 *initializer-list*  **,**  *initializer*  
  
 *type-name* :  
 *specifier-qualifier-list abstract-declarator*<sub>opt</sub>  
  
 *typedef-name* :  
 *identifier*  
  
 *extended-decl-modifier-seq* :/\*    Spécifique de Microsoft \*/  
 *extended-decl-modifier*<sub>opt</sub>  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 *extended-decl-modifier* :   /\* Spécifique de Microsoft \*/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’appel](../cpp/calling-conventions.md)   
 [Grammaire de la structure de la phrase](../c-language/phrase-structure-grammar.md)   
 [Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)