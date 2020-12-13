---
description: 'En savoir plus sur : erreur irrécupérable C1060'
title: Erreur irrécupérable C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 149fd4108aabf603e844c6906e072a9c64578d5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330717"
---
# <a name="fatal-error-c1060"></a>Erreur irrécupérable C1060

espace du tas insuffisant pour le compilateur

Le système d'exploitation ou la bibliothèque Runtime ne peut pas répondre à une demande de mémoire.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Pour corriger cette erreur, essayez les solutions possibles suivantes

1. Si le compilateur émet également des erreurs [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) et [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), utilisez l’option du compilateur [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) pour réduire la limite d’allocation de mémoire. Si vous réduisez l'allocation de mémoire restante, l'espace du tas dont dispose votre application est plus important.

   Si l’option [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) est déjà définie, essayez de la supprimer. Il se peut que l'espace du tas soit épuisé, car la limite d'allocation de mémoire spécifiée dans l'option est trop élevée. Le compilateur utilise une limite par défaut si vous supprimez l’option [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) .

1. Si vous compilez sur une plateforme 64 bits, utilisez l'ensemble d'outils de compilateur 64 bits. Pour plus d’informations, consultez [Comment : activer un ensemble d’outils Visual C++ bits 64 sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Sur Windows 32 bits, essayez d’utiliser le commutateur boot.ini [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) .

1. Augmentez la taille du fichier d'échange Windows.

1. Fermez les autres programmes en cours d'exécution.

1. Éliminez les fichiers include superflus.

1. Éliminez les variables globales inutiles, par exemple, en allouant la mémoire de façon dynamique au lieu de déclarer un grand tableau.

1. Éliminez les déclarations non utilisées.

1. Fractionnez le fichier en cours en fichiers moins volumineux.
