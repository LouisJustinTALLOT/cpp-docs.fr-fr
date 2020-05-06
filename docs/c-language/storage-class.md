---
title: Classe de stockage
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: aa6e977b3aa03b5f08901cfa8b0abe1b4046e72d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857006"
---
# <a name="storage-class"></a>Classe de stockage

Dans une définition de fonction, le spécificateur de classe de stockage attribue à la fonction la classe de stockage `extern` ou **static**.

## <a name="syntax"></a>Syntaxe

*définition de fonction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribute-SEQ* est spécifique à Microsoft\*/

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*Storage-Class-specifier*:/\* pour les définitions de fonction\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**externes**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**statique**

Si une définition de fonction n'inclut pas de *storage-class-specifier*, la classe de stockage a par défaut la valeur `extern`. Vous pouvez déclarer explicitement une fonction comme `extern`, mais ce n'est pas obligatoire.

Si la déclaration d'une fonction contient le *storage-class-specifier* `extern`, l'identificateur a la même liaison que toute déclaration visible de l'identificateur avec une portée de fichier. S'il n'existe aucune déclaration visible avec une portée de fichier, l'identificateur a une liaison externe. Si un identificateur a une portée de fichier et aucun *storage-class-specifier*, l'identificateur a une liaison externe. La liaison externe signifie que chaque instance de l'identificateur identifie le même objet ou la même fonction. Consultez [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations sur la liaison et la portée de fichier.

Les déclarations de fonction dans la portée du bloc avec un spécificateur de classe de stockage autre que `extern` génèrent des erreurs.

Une fonction avec la classe de stockage **static** est uniquement visible dans le fichier source dans lequel elle est définie. Toutes les autres fonctions, que la classe de stockage `extern` leur soit attribuée explicitement ou implicitement, sont visibles dans tous les fichiers source du programme. Si la classe de stockage **static** est voulue, elle doit être déclarée dans la première occurrence d'une déclaration (le cas échéant) de la fonction et dans la définition de la fonction.

**Spécifique à Microsoft**

Lorsque les extensions Microsoft sont activées, une fonction initialement déclarée sans classe de stockage (ou avec la classe de stockage `extern`) reçoit la classe de stockage **static** si la définition de fonction se trouve dans le même fichier source et que cette définition indique explicitement la classe de stockage **static**.

Lors de la compilation avec l'option de compilateur /Ze, les fonctions déclarées dans un bloc à l'aide du mot clé `extern` ont une visibilité globale. Ce n'est pas le cas lorsque la compilation est effectuée avec /Za. Cette fonctionnalité ne peut pas être considérée comme adaptée si la portabilité du code source est un élément pris en compte.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
