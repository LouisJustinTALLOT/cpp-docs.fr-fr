---
title: Erreur irrécupérable C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822234"
---
# <a name="fatal-error-c1305"></a>Erreur irrécupérable C1305

la base de données de profil 'pgd_file ' du correspond à une architecture différente

Un fichier .pgd qui a été généré à partir de l’opération/LTCG : PGINSTRUMENT pour une autre plateforme a été passée au [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimisations guidées par profil](../../build/profile-guided-optimizations.md) sont disponibles pour les plateformes x86 et x64. Toutefois, un fichier .pgd généré avec une opération de/LTCG : PGINSTRUMENT pour une plateforme n’est pas valide en tant qu’entrée à un/LTCG : PGOPTIMIZE pour une autre plateforme.

Pour résoudre cette erreur, seulement passez un fichier .pgd qui est créé avec/LTCG : PGINSTRUMENT pour/LTCG : PGOPTIMIZE sur la même plateforme.