---
title: Entrée et sortie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62319d040275d96314ee824f9fea020a4004974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389389"
---
# <a name="input-and-output"></a>Entrées et sorties

Les fonctions d’E/S, lisent et écrivent des données de et vers des fichiers et appareils. Les opérations d’E/S sur les fichiers ont lieu en mode texte ou binaire. La bibliothèque Runtime Microsoft propose trois types de fonctions d’E/S :

- Les fonctions [d’E/S de flux](../c-runtime-library/stream-i-o.md) traitent les données en tant que flux de caractères individuels.

- Les fonctions [d’E/S de bas niveau](../c-runtime-library/low-level-i-o.md) appellent le système d’exploitation directement pour l’opération du niveau inférieur à celui fourni par les E/S de flux.

- Les fonctions [d’E/S de console et de port](../c-runtime-library/console-and-port-i-o.md) lisent ou écrivent directement dans une console (clavier et écran) ou un port d’E/S (par exemple un port d’imprimante).

   > [!NOTE]
   > Étant donné que les fonctions de flux de données sont mises en mémoire tampon et que les fonctions de bas niveau ne le sont pas, ces deux types de fonctions sont généralement incompatibles. Pour traiter un fichier particulier, utilisez exclusivement des fonctions de flux ou de bas niveau.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
