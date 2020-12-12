---
description: En savoir plus sur les attributs de Storage-Class étendu C
title: Attributs étendus de classe de stockage C
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 9dff43594ef97214609c6ed2195240d0e21648e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168759"
---
# <a name="c-extended-storage-class-attributes"></a>Attributs étendus de classe de stockage C

**Spécifique à Microsoft**

Des informations plus récentes à ce sujet sont disponibles dans [__declspec (Référence C++)](../cpp/declspec.md).

La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour le langage C. Les attributs de classe de stockage qui utilisent la syntaxe à attributs étendus incluent thread, naked, dllimport et dllexport.

La syntaxe à attributs étendus utilisée pour la spécification des informations de classe de stockage utilise le mot clé __declspec, qui indique qu'une instance d'un type donné doit être stockée avec un attribut de classe de stockage spécifique à Microsoft (thread, naked, dllimport ou dllexport). Parmi les exemples d'autres modificateurs de classe de stockage figurent les mots clés static et extern. Toutefois, ces mots clés font partie de la norme ANSI C et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus.

## <a name="syntax"></a>Syntaxe

*storage-class-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *Extended-decl-modifier-SEQ* **)**  / \* Spécifique à Microsoft\*/

*Extended-decl-modifier-SEQ*: &nbsp; &nbsp; &nbsp; &nbsp; / \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*Extended-decl-modifier*: &nbsp; &nbsp; &nbsp; &nbsp; / \* spécifique à Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**

Un espace blanc sépare les modificateurs de déclaration. Notez que *extended-decl-modifier-seq* peut être vide, auquel cas __declspec n'a aucun effet.

Les attributs de classe de stockage thread, naked, dllimport et dllexport sont une propriété uniquement de la déclaration des données ou de la fonction à laquelle ils sont appliqués. Ils ne redéfinissent pas les attributs de type de la fonction elle-même. L'attribut thread affecte uniquement les données. L'attribut naked affecte uniquement les fonctions. Les attributs dllimport et dllexport affectent les fonctions et les données.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
