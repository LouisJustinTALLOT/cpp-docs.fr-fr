---
title: Définitions de fonction C
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 61662caf28fad2f961a580cf280799711a6909bb
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147683"
---
# <a name="c-function-definitions"></a>Définitions de fonction C

Une définition de fonction spécifie le nom de la fonction, les types et le nombre de paramètres qu’elle s’attend à recevoir et son type de retour. Une définition de fonction comprend également un corps de fonction avec les déclarations de ses variables locales, ainsi que les instructions qui déterminent ce que fait la fonction.

## <a name="syntax"></a>Syntaxe

*translation-unit* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration* : /\* Autorisé uniquement dans la portée (fichier) externe \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* est spécifique à Microsoft \*/

Les paramètres de prototype sont les suivants :

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator* : /\*Déclarateur de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)** /\* Déclarateur de nouveau style \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)** /\* Déclarateur de style obsolète \*/

La liste des paramètres dans une définition utilise la syntaxe suivante :

*parameter-type-list* : /\* La liste de paramètrest \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

La liste des paramètres dans une définition de fonction de style ancien utilise la syntaxe suivante :

*identifier-list* : /\* Utilisé dans les définitions et les déclarations de fonction de style obsolète \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier-list* **,**  *identifier*

La syntaxe du corps de la fonction est la suivante :

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

Les seuls spécificateurs de classe de stockage pouvant modifier une déclaration de fonction sont **extern** et **static**. Le spécificateur **extern** signifie que la fonction peut être référencée à partir d'autres fichiers ; autrement dit, son nom est exporté vers l'éditeur de liens. Le spécificateur **static** signifie que la fonction ne peut pas être référencée à partir d'autres fichiers ; autrement dit, le nom n'est pas exporté par l'éditeur de liens. Si aucune classe de stockage n'apparaît dans une définition de fonction, **extern** est la valeur par défaut. Dans tous les cas, la fonction est toujours visible du point de définition jusqu'à la fin du fichier.

Les éléments *declaration-specifiers* facultatifs et l’élément *declarator* obligatoire spécifient ensemble le type de retour et le nom de la fonction. L’élément *declarator* est une combinaison de l'identificateur qui nomme la fonction et des parenthèses qui suivent le nom de la fonction. L’élément non terminal *attribute-seq* facultatif est une fonctionnalité spécifique à Microsoft définie dans [Attributs de fonction](../c-language/function-attributes.md).

L'élément *direct-declarator* (dans la syntaxe *declarator*) spécifie le nom de la fonction définie et les identificateurs de ses paramètres. Si l'élément *direct-declarator* inclut *parameter-type-list*, la liste spécifie les types de tous les paramètres. Ce déclarateur sert également de prototype de fonction pour les appels ultérieurs à la fonction.

Un élément  *declaration*dans *declaration-list* dans les définitions de fonction ne peut pas contenir de *storage-class-specifier* autre que **register**. L’élément *type-specifier* de la syntaxe *declaration-specifiers* peut être omis uniquement si la classe de stockage **register** est spécifiée pour une valeur de type **int**.

L'élément *compound-statement* est le corps de la fonction contenant des déclarations de variables locales, des références à des éléments déclarés extérieurement et des instructions.

Les sections [Attributs de fonction](../c-language/function-attributes.md), [Classe de stockage](../c-language/storage-class.md), [Type de retour](../c-language/return-type.md), [Paramètres](../c-language/parameters.md) et [Corps de la fonction](../c-language/function-body.md) décrivent les composants de la définition de fonction en détail.

## <a name="see-also"></a>Voir aussi

[Fonctions](../c-language/functions-c.md)
