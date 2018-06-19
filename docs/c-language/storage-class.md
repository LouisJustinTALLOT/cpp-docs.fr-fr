---
title: Classe de stockage │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecd50ddf72fbafb23571e2b2709418e4eb89093e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391429"
---
# <a name="storage-class"></a>Classe de stockage
Dans une définition de fonction, le spécificateur de classe de stockage attribue à la fonction la classe de stockage `extern` ou **static**.  
  
## <a name="syntax"></a>Syntaxe  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* est spécifique de Microsoft */  
  
 *declaration-specifiers* :  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *storage-class-specifier* : /\* Pour les définitions de fonction \*/  
 **extern**  
  
 **static**  
  
 Si une définition de fonction n'inclut pas de *storage-class-specifier*, la classe de stockage a par défaut la valeur `extern`. Vous pouvez déclarer explicitement une fonction comme `extern`, mais ce n'est pas obligatoire.  
  
 Si la déclaration d'une fonction contient le *storage-class-specifier*`extern`, l'identificateur a la même liaison que toute déclaration visible de l'identificateur avec une portée de fichier. S'il n'existe aucune déclaration visible avec une portée de fichier, l'identificateur a une liaison externe. Si un identificateur a une portée de fichier et aucun *storage-class-specifier*, l'identificateur a une liaison externe. La liaison externe signifie que chaque instance de l'identificateur identifie le même objet ou la même fonction. Consultez [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations sur la liaison et la portée de fichier.  
  
 Les déclarations de fonction dans la portée du bloc avec un spécificateur de classe de stockage autre que `extern` génèrent des erreurs.  
  
 Une fonction avec la classe de stockage **static** est uniquement visible dans le fichier source dans lequel elle est définie. Toutes les autres fonctions, que la classe de stockage `extern` leur soit attribuée explicitement ou implicitement, sont visibles dans tous les fichiers source du programme. Si la classe de stockage **static** est voulue, elle doit être déclarée dans la première occurrence d'une déclaration (le cas échéant) de la fonction et dans la définition de la fonction.  
  
 **Section spécifique à Microsoft**  
  
 Lorsque les extensions Microsoft sont activées, une fonction initialement déclarée sans classe de stockage (ou avec la classe de stockage `extern`) reçoit la classe de stockage **static** si la définition de fonction se trouve dans le même fichier source et que cette définition indique explicitement la classe de stockage **static**.  
  
 Lors de la compilation avec l'option de compilateur /Ze, les fonctions déclarées dans un bloc à l'aide du mot clé `extern` ont une visibilité globale. Ce n'est pas le cas lorsque la compilation est effectuée avec /Za. Cette fonctionnalité ne peut pas être considérée comme adaptée si la portabilité du code source est un élément pris en compte.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Définitions de fonction C](../c-language/c-function-definitions.md)