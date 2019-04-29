---
title: Erreur BSCMAKE BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: d1f74a90657985a87accc13bc2b576c1d7fd5a4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279812"
---
# <a name="bscmake-error-bk1506"></a>Erreur BSCMAKE BK1506

Impossible d’ouvrir le fichier 'nom_fichier' [ : raison]

BSCMAKE ne peut pas ouvrir le fichier.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fichier est verrouillé par un autre processus. Si `reason` indique **autorisation refusée**, le navigateur peut être à l’aide du fichier. Fermez la fenêtre de navigation et recommencez la génération.

1. Un disque saturé.

1. Une erreur matérielle.

1. Le fichier de sortie spécifié a le même nom qu’un sous-répertoire existant.