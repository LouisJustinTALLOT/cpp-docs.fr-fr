---
title: Erreur BSCMAKE BK1506 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26201a894212701cca19ab2192676b37a69e8b57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088694"
---
# <a name="bscmake-error-bk1506"></a>Erreur BSCMAKE BK1506

Impossible d’ouvrir le fichier 'nom_fichier' [ : raison]

BSCMAKE ne peut pas ouvrir le fichier.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fichier est verrouillé par un autre processus. Si `reason` indique **autorisation refusée**, le navigateur peut être à l’aide du fichier. Fermez la fenêtre de navigation et recommencez la génération.

1. Un disque saturé.

1. Une erreur matérielle.

1. Le fichier de sortie spécifié a le même nom qu’un sous-répertoire existant.