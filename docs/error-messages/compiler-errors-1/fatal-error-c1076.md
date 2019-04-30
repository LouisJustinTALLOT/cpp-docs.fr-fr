---
title: Erreur irrécupérable C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406949"
---
# <a name="fatal-error-c1076"></a>Erreur irrécupérable C1076

> limite du compilateur : la limite du tas interne a été atteinte ; utilisez /Zm pour spécifier une limite plus élevée

Cette erreur peut être provoquée par un trop grand nombre de symboles, ou d'instanciations de modèles. À partir de Visual Studio 2015, ce message peut-être provenir de dû au fait trop de processus de génération parallèle de la sollicitation de la mémoire virtuelle Windows. Dans ce cas, nous recommandons d’utiliser le **/Zm** option doit être ignorée, sauf si vous utilisez un `#pragma hdrstop` directive.

Pour corriger cette erreur :

1. Si votre en-tête précompilé utilise un `#pragma hdrstop` directive, utilisez le [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) option pour définir la limite de mémoire du compilateur sur la valeur spécifiée dans le [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) message d’erreur. Pour plus d’informations qui inclut la définition de cette valeur dans Visual Studio, consultez la section Notes dans [/Zm (spécifier précompilé en-tête limite d’Allocation mémoire)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Envisagez de réduire le nombre de traitements parallèles spécifié à l’aide de la **/maxcpucount** option à MSBUILD. EXE conjointement avec le **/MP** option à CL. EXE. Pour plus d’informations, consultez [problèmes d’en-tête précompilé (PCH) et des recommandations](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Si vous utilisez des compilateurs hébergés 32 bits sur un système d'exploitation 64 bits, utilisez les compilateurs hébergés 64 bits à la place. Pour plus d'informations, voir [Procédure : Activer un 64 bits Visual C++ ensemble d’outils sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Éliminez les fichiers include superflus.

1. Éliminez les variables globales non nécessaires, par exemple en allouant la mémoire de façon dynamique au lieu de déclarer un grand tableau.

1. Éliminez les déclarations non utilisées.

Si l’erreur C1076 apparaît immédiatement après le démarrage de la build, la valeur spécifiée pour **/Zm** est probablement trop élevée pour votre programme. Réduire le **/Zm** valeur.