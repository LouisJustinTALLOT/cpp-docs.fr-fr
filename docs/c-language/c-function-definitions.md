---
description: En savoir plus sur les définitions de fonction C
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
ms.openlocfilehash: 9e664224608a741897bf8ae6208a0d9011cdb3c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296925"
---
# <a name="c-function-definitions"></a>Définitions de fonction C

Une définition de fonction spécifie le nom de la fonction, les types et le nombre de paramètres qu’elle s’attend à recevoir et son type de retour. Une définition de fonction comprend également un corps de fonction avec les déclarations de ses variables locales, ainsi que les instructions qui déterminent ce que fait la fonction.

## <a name="syntax"></a>Syntaxe

*translation-unit* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*External-DECLARATION* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*External-DECLARATION*:/ \* autorisé uniquement au niveau de l’étendue externe (fichier) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*définition de fonction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*

*définition de fonction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribute-SEQ* est spécifique à Microsoft\*/

Les paramètres de prototype sont les suivants :

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*déclarateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator*:/ \* un déclarateur de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator***(***Parameter-type-list***)**  / \* New-style declarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator***(***identifier-List*<sub>OPT</sub> **)**  / \* -déclarateur de style obsolète    \*/

La liste des paramètres dans une définition utilise la syntaxe suivante :

*Parameter-type-list*:/ \* la liste de paramètres \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de paramètres* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liste de paramètres* **,...**

*liste de paramètres*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Déclaration de paramètre*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *paramètre-DECLARATION*

*parameter-declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

La liste des paramètres dans une définition de fonction de style ancien utilise la syntaxe suivante :

*identifier-List*:/ \* utilisé dans les définitions et les déclarations de fonction obsolètes \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur-liste* **,**  *identificateur*

La syntaxe du corps de la fonction est la suivante :

*Compound-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>OPT</sub> *Statement-List*<sub>OPT</sub> **}**

Les seuls spécificateurs de classe de stockage pouvant modifier une déclaration de fonction sont **`extern`** et **`static`** . Le **`extern`** spécificateur signifie que la fonction peut être référencée à partir d’autres fichiers ; autrement dit, le nom de la fonction est exporté vers l’éditeur de liens. Le **`static`** spécificateur signifie que la fonction ne peut pas être référencée à partir d’autres fichiers ; autrement dit, le nom n’est pas exporté par l’éditeur de liens. Si aucune classe de stockage n’apparaît dans une définition de fonction, **`extern`** est utilisé par défaut. Dans tous les cas, la fonction est toujours visible du point de définition jusqu'à la fin du fichier.

Les éléments *declaration-specifiers* facultatifs et l’élément *declarator* obligatoire spécifient ensemble le type de retour et le nom de la fonction. L’élément *declarator* est une combinaison de l'identificateur qui nomme la fonction et des parenthèses qui suivent le nom de la fonction. L’élément non terminal *attribute-seq* facultatif est une fonctionnalité spécifique à Microsoft définie dans [Attributs de fonction](../c-language/function-attributes.md).

L'élément *direct-declarator* (dans la syntaxe *declarator*) spécifie le nom de la fonction définie et les identificateurs de ses paramètres. Si l'élément *direct-declarator* inclut *parameter-type-list*, la liste spécifie les types de tous les paramètres. Ce déclarateur sert également de prototype de fonction pour les appels ultérieurs à la fonction.

Une *déclaration* dans la *déclaration-List* dans les définitions de fonction ne peut pas contenir de *Storage-Class-specifier* autre que **`register`** . Le *spécificateur de type* dans la syntaxe *DECLARATION-Specifiers* peut être omis uniquement si la **`register`** classe de stockage est spécifiée pour une valeur de **`int`** type.

L'élément *compound-statement* est le corps de la fonction contenant des déclarations de variables locales, des références à des éléments déclarés extérieurement et des instructions.

Les sections [Attributs de fonction](../c-language/function-attributes.md), [Classe de stockage](../c-language/storage-class.md), [Type de retour](../c-language/return-type.md), [Paramètres](../c-language/parameters.md) et [Corps de la fonction](../c-language/function-body.md) décrivent les composants de la définition de fonction en détail.

## <a name="see-also"></a>Voir aussi

[Fonctions](../c-language/functions-c.md)
