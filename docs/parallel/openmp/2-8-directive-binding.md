---
title: 2.8 Liaison de directives
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528616"
---
# <a name="28-directive-binding"></a>2.8 Liaison de directives

Liaison dynamique des directives doit respecter les règles suivantes :

- Le **pour**, **sections**, **unique**, **master**, et **barrière** directives lier à la dynamiquement englobant **parallèles**, s’il en existe, quelle que soit la valeur de n’importe quel **si** clause qui doivent être présent dans cette directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée du thread principal uniquement.

- Le **classés** directive lie à dynamiquement englobante **pour**.

- Le **atomique** directive applique un accès exclusif au niveau **atomique** directives dans tous les threads, pas seulement l’équipe actuelle.

- Le **critique** directive applique un accès exclusif au niveau **critique** directives dans tous les threads, pas seulement l’équipe actuelle.

- Une directive ne peut jamais lier dynamiquement à n’importe quelle directive en dehors de la plus proche englobante **parallèles**.