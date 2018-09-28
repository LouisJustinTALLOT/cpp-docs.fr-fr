---
title: Attributs étendus de classe de stockage C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a55f4ac98a712d8166c3d0ca5e22e13cb8c9145
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758815"
---
# <a name="c-extended-storage-class-attributes"></a>Attributs étendus de classe de stockage C
**Section spécifique à Microsoft**  
  
Des informations plus récentes à ce sujet sont disponibles dans [__declspec (Référence C++)](../cpp/declspec.md).  
  
La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour le langage C. Les attributs de classe de stockage qui utilisent la syntaxe à attributs étendus incluent thread, naked, dllimport et dllexport.  
  
La syntaxe à attributs étendus utilisée pour la spécification des informations de classe de stockage utilise le mot clé __declspec, qui indique qu'une instance d'un type donné doit être stockée avec un attribut de classe de stockage spécifique à Microsoft (thread, naked, dllimport ou dllexport). Parmi les exemples d'autres modificateurs de classe de stockage figurent les mots clés static et extern. Toutefois, ces mots clés font partie de la norme ANSI C et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus.  
  
## <a name="syntax"></a>Syntaxe

*storage-class-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)** /\* Propre à Microsoft \*/

*extended-decl-modifier-seq* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Propre à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*extended-decl-modifier* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Propre à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

Un espace blanc sépare les modificateurs de déclaration. Notez que *extended-decl-modifier-seq* peut être vide, auquel cas __declspec n'a aucun effet.
  
Les attributs de classe de stockage thread, naked, dllimport et dllexport sont une propriété uniquement de la déclaration des données ou de la fonction à laquelle ils sont appliqués. Ils ne redéfinissent pas les attributs de type de la fonction elle-même. L'attribut thread affecte uniquement les données. L'attribut naked affecte uniquement les fonctions. Les attributs dllimport et dllexport affectent les fonctions et les données.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
[Déclarations et types](../c-language/declarations-and-types.md)