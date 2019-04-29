---
title: 'Erreur irrécupérable RW1025 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347205"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Erreur irrécupérable RW1025 du compilateur de ressources 

Insuffisance de mémoire de tas lointain

Recherchez les logiciels résidant en mémoire qui peut être occuper trop d’espace. Utilisez le programme CHKDSK pour connaître la quantité de mémoire vous disposez.

Si vous créez un fichier de ressources de grande taille, fractionner le script de ressources en deux fichiers. Après avoir créé les deux fichiers .res, utilisez la ligne de commande MS-DOS pour les joindre :

```
copy first.res /b + second.res /b full.res
```