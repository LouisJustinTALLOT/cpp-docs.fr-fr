---
description: 'En savoir plus sur : fichiers sources et programmes sources'
title: Fichiers sources et programmes sources
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: 9fd389f74efac11288b805d95dc2d95d4ec6d2bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296899"
---
# <a name="source-files-and-source-programs"></a>Fichiers sources et programmes sources

Un programme source peut être divisé en un ou plusieurs « fichiers sources », ou « unités de traduction ». L'entrée fournie au compilateur est appelée « unité de traduction ».

## <a name="syntax"></a>Syntaxe

*translation-unit* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*External-DECLARATION* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*définition de fonction*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclaré*

L'article [Vue d'ensemble des déclarations](../c-language/overview-of-declarations.md) fournit la syntaxe de l'élément non terminal `declaration` et la *référence du préprocesseur* explique comment [l'unité de traduction](../preprocessor/phases-of-translation.md) est traitée.

> [!NOTE]
> Reportez-vous à l'introduction [Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md) pour obtenir une explication des conventions syntaxiques ANSI.

Les composants d'une unité de traduction sont des déclarations externes qui incluent des définitions de fonctions et des déclarations d'identificateurs. Ces déclarations et définitions peuvent être dans des fichiers sources, des fichiers d'en-tête, des bibliothèques et d'autres fichiers dont le programme a besoin. Vous devez compiler chaque unité de traduction et lier les fichiers objets obtenus pour construire un programme.

Un « programme source » C est une collection de directives, de pragmas, de déclarations, de définitions, de blocs d'instructions et de fonctions. Pour être des composants valides d'un programme Microsoft C, tous les composants doivent avoir la syntaxe décrite dans cet ouvrage, bien qu'ils puissent apparaître dans n'importe quel ordre dans le programme (dans le cadre des règles détaillées dans cet ouvrage). Quoi qu'il en soit, l'emplacement de ces composants dans un programme affecte la manière dont les variables et les fonctions peuvent être utilisées dans un programme. (Consultez [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md) pour plus d'informations.)

Les fichiers sources n'ont pas besoin de contenir d'instructions exécutables. Par exemple, il peut vous paraître utile de placer les définitions des variables dans un fichier source, puis de déclarer les références à ces variables dans d'autres fichiers sources qui les utilisent. Cette technique simplifie la recherche et la mise à jour des définitions, le cas échéant. Pour la même raison, les constantes et les macros sont souvent organisées dans des fichiers distincts, appelés « fichiers Include » ou « fichiers d'en-tête », qui peuvent être référencés dans les fichiers sources selon les besoins. Consultez la *référence du préprocesseur* pour plus d'informations sur les [macros](../preprocessor/macros-c-cpp.md) et les [fichiers Include](../preprocessor/hash-include-directive-c-cpp.md).

## <a name="see-also"></a>Voir aussi

[Structure du programme](../c-language/program-structure.md)
