---
title: Directives de préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: ac765d33aec4795e94866c097d6c453dbd0e4a08
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845326"
---
# <a name="preprocessor-directives"></a>Directives de préprocesseur

Les directives de préprocesseur, telles que `#define` et `#ifdef` , sont généralement utilisées pour rendre les programmes sources faciles à modifier et à compiler dans différents environnements d’exécution. Les directives dans le fichier source indiquent au préprocesseur d’effectuer des actions spécifiques. Par exemple, le préprocesseur peut remplacer des jetons dans le texte, insérer le contenu d'autres fichiers dans le fichier source ou supprimer la compilation d'une partie du fichier en supprimant des sections de texte. Les lignes de préprocesseur sont reconnues et exécutées avant l'expansion macro. Par conséquent, si une macro se développe en un nom qui ressemble à une commande de préprocesseur, elle n’est pas reconnue par le préprocesseur.

Les instructions de préprocesseur utilisent le même jeu de caractères que les instructions de fichier source, sauf que les séquences d’échappement ne sont pas prises en charge. Le jeu de caractères utilisé dans les instructions de préprocesseur est identique au jeu de caractères d'exécution. Le préprocesseur reconnaît aussi les valeurs de caractères négatives.

Le préprocesseur reconnaît les directives suivantes :

:::row:::
   :::column span="":::
      [`#define`](../preprocessor/hash-define-directive-c-cpp.md)\
      [`#elif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#else`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#endif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#error`](../preprocessor/hash-error-directive-c-cpp.md)\
      [`#if`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#ifdef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)\
      [`#ifndef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#import`](../preprocessor/hash-import-directive-cpp.md)\
      [`#include`](../preprocessor/hash-include-directive-c-cpp.md)\
      [`#line`](../preprocessor/hash-line-directive-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#pragma`](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
      [`#undef`](../preprocessor/hash-undef-directive-c-cpp.md)\
      [`#using`](../preprocessor/hash-using-directive-cpp.md)
   :::column-end:::
:::row-end:::

Le signe dièse ( `#` ) doit être le premier caractère qui n’est pas un espace blanc sur la ligne contenant la directive. Les caractères d’espace blanc peuvent apparaître entre le signe dièse et la première lettre de la directive. Certaines directives incluent des arguments ou des valeurs. Tout texte qui suit une directive (sauf un argument ou une valeur qui fait partie de la directive) doit être précédé du délimiteur de commentaire sur une seule ligne ( `//` ) ou placé dans les délimiteurs de commentaires ( `/* */` ). Les lignes contenant des directives de préprocesseur peuvent être poursuivies en faisant immédiatement précéder le marqueur de fin de ligne d’une barre oblique inverse ( `\` ).

Les directives de préprocesseur peuvent apparaître n’importe où dans un fichier source, mais elles s’appliquent uniquement au reste du fichier source, une fois qu’elles ont été affichées.

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)\
[Macros prédéfinies](../preprocessor/predefined-macros.md)\
[Référence du préprocesseur c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
