---
title: Prise en charge de la virgule flottante pour le code plus ancien (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509641"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Prise en charge de la virgule flottante pour le code plus ancien (Visual C++)

Les registres MMX et pile à virgule flottante (MM0-MM7/ST0-ST7) sont conservés entre les commutateurs de contexte.  Il n’existe aucune convention d’appel explicite pour ces registres.  L’utilisation de ces registres est strictement interdite dans le code en mode noyau.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)