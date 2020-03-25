---
title: Erreur irrécupérable C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204176"
---
# <a name="fatal-error-c1076"></a>Erreur irrécupérable C1076

> limite du compilateur : la limite du tas interne a été atteinte ; utilisez /Zm pour spécifier une limite plus élevée

Cette erreur peut être provoquée par un trop grand nombre de symboles, ou d'instanciations de modèles. À compter de Visual Studio 2015, ce message peut résulter d’une sollicitation de la mémoire virtuelle Windows due à un trop grand nombre de processus de génération parallèle. Dans ce cas, la recommandation d’utiliser l’option **/ZM** doit être ignorée, sauf si vous utilisez une directive `#pragma hdrstop`.

Pour corriger cette erreur :

1. Si votre en-tête précompilé utilise une directive `#pragma hdrstop`, utilisez l’option [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) pour définir la limite de mémoire du compilateur à la valeur spécifiée dans le message d’erreur [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) . Pour plus d’informations sur la définition de cette valeur dans Visual Studio, consultez la section Notes dans [/ZM (spécifier la limite d’allocation de mémoire d’en-tête précompilé)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Envisagez de réduire le nombre de processus parallèles spécifiés à l’aide de l’option **/maxcpucount** pour MSBuild. EXE conjointement avec l’option **/MP** à cl. Exécutable. Pour plus d’informations, consultez [problèmes et recommandations concernant les en-têtes précompilés (PCH)](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Si vous utilisez des compilateurs hébergés 32 bits sur un système d'exploitation 64 bits, utilisez les compilateurs hébergés 64 bits à la place. Pour plus d’informations, consultez [Comment : activer un ensemble d’outils visuels C++ 64 bits sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Éliminez les fichiers include superflus.

1. Éliminez les variables globales non nécessaires, par exemple en allouant la mémoire de façon dynamique au lieu de déclarer un grand tableau.

1. Éliminez les déclarations non utilisées.

Si C1076 se produit immédiatement après le démarrage de la génération, la valeur spécifiée pour **/ZM** est probablement trop élevée pour votre programme. Réduisez la valeur **/ZM** .
