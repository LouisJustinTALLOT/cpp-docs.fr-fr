---
title: Liaison d’importations
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 6ee9d9cc180e77d817b7b52baa1a6eb5209a8365
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486344"
---
# <a name="binding-imports"></a>Liaison d’importations

Le comportement de l’éditeur de liens par défaut consiste à créer une table d’adresse d’importation peut être liée pour le DLL à chargement différé. Si la DLL est liée, la fonction d’assistance tente d’utiliser les informations liées au lieu d’appeler **GetProcAddress** sur chacun des importations référencées. Si l’horodatage ou l’adresse préférée ne correspondre pas celles de la DLL chargée, la fonction d’assistance suppose que la table d’adresses importation liées est obsolète et poursuit comme si elle n’existe pas.

Si vous n’envisagez pas de lier les importations à chargement différé de DLL, en spécifiant [/retarder](../../build/reference/delay-delay-load-import-settings.md): nobind sur la ligne de commande de l’éditeur de liens empêche la table d’adresses importation liées généré et beaucoup d’espace dans le fichier image.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)