---
title: Erreur irrécupérable C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 876ae7a368d2d1a1ee94a04fc9ecf50d0f4b8d78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607063"
---
# <a name="fatal-error-c1060"></a>Erreur irrécupérable C1060

espace du tas insuffisant pour le compilateur

Le système d'exploitation ou la bibliothèque Runtime ne peut pas répondre à une demande de mémoire.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Pour corriger cette erreur, essayez les solutions possibles suivantes

1. Si le compilateur émet aussi les erreurs [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) et [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), utilisez le [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) option du compilateur pour réduire la limite d’allocation de mémoire. Si vous réduisez l'allocation de mémoire restante, l'espace du tas dont dispose votre application est plus important.

   Si le [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) option est déjà définie, essayez de la supprimer. Il se peut que l'espace du tas soit épuisé, car la limite d'allocation de mémoire spécifiée dans l'option est trop élevée. Le compilateur utilise une limite par défaut si vous supprimez le [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) option.

1. Si vous compilez sur une plateforme 64 bits, utilisez l'ensemble d'outils de compilateur 64 bits. Pour plus d’informations, consultez [Comment : activer un 64 bits Visual C++ ensemble d’outils sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Sur Windows 32 bits, essayez d’utiliser le [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) commutateur boot.ini.

1. Augmentez la taille du fichier d'échange Windows.

1. Fermez les autres programmes en cours d'exécution.

1. Éliminez les fichiers include superflus.

1. Éliminez les variables globales inutiles, par exemple, en allouant la mémoire de façon dynamique au lieu de déclarer un grand tableau.

1. Éliminez les déclarations non utilisées.

9. Fractionnez le fichier en cours en fichiers moins volumineux.