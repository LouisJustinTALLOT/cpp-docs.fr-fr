---
description: 'En savoir plus sur : classe de stockage'
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
ms.openlocfilehash: 87f53c38b2f71acc15499a496e98b1f9c7173210
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296730"
---
# <a name="storage-class"></a>Classe de stockage

Le spécificateur de classe de stockage dans une définition de fonction donne à la fonction ou à la **`extern`** **`static`** classe de stockage.

## <a name="syntax"></a>Syntaxe

*définition de fonction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribute-SEQ* est spécifique à Microsoft\*/

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*Storage-Class-specifier*:/ \* pour les définitions de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`extern`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`static`**

Si une définition de fonction n’inclut pas de *Storage-Class-specifier*, la classe de stockage prend par défaut la valeur **`extern`** . Vous pouvez déclarer explicitement une fonction comme **`extern`** , mais ce n’est pas obligatoire.

Si la déclaration d’une fonction contient le *Storage-Class-specifier* **`extern`** , l’identificateur a la même liaison que toute déclaration visible de l’identificateur avec la portée de fichier. S'il n'existe aucune déclaration visible avec une portée de fichier, l'identificateur a une liaison externe. Si un identificateur a une portée de fichier et aucun *storage-class-specifier*, l'identificateur a une liaison externe. La liaison externe signifie que chaque instance de l'identificateur identifie le même objet ou la même fonction. Consultez [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations sur la liaison et la portée de fichier.

Les déclarations de fonction de portée de bloc avec un spécificateur de classe de stockage autre que **`extern`** génèrent des erreurs.

Une fonction avec **`static`** la classe de stockage est visible uniquement dans le fichier source dans lequel elle est définie. Toutes les autres fonctions, qu’elles reçoivent une **`extern`** classe de stockage explicite ou implicite, sont visibles dans tous les fichiers sources du programme. Si **`static`** la classe de stockage est souhaitée, elle doit être déclarée sur la première occurrence d’une déclaration (le cas échéant) de la fonction et sur la définition de la fonction.

**Spécifique à Microsoft**

Lorsque les extensions Microsoft sont activées, une fonction initialement déclarée sans classe de stockage (ou avec la **`extern`** classe de stockage) reçoit **`static`** la classe de stockage si la définition de la fonction se trouve dans le même fichier source et si la définition spécifie explicitement la **`static`** classe de stockage.

Lors de la compilation avec l’option de compilateur/ze, les fonctions déclarées dans un bloc à l’aide du **`extern`** mot clé ont une visibilité globale. Ce n'est pas le cas lorsque la compilation est effectuée avec /Za. Cette fonctionnalité ne peut pas être considérée comme adaptée si la portabilité du code source est un élément pris en compte.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
