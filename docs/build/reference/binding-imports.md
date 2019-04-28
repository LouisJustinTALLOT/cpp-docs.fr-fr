---
title: Liaison d’importations
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 4058d738b87b69a73e8f18d977be8435a7d96a14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272921"
---
# <a name="binding-imports"></a>Liaison d’importations

Le comportement de l’éditeur de liens par défaut consiste à créer une table d’adresse d’importation peut être liée pour le DLL à chargement différé. Si la DLL est liée, la fonction d’assistance tente d’utiliser les informations liées au lieu d’appeler **GetProcAddress** sur chacun des importations référencées. Si l’horodatage ou l’adresse préférée ne correspondre pas celles de la DLL chargée, la fonction d’assistance suppose que la table d’adresses importation liées est obsolète et poursuit comme si elle n’existe pas.

Si vous n’envisagez pas de lier les importations à chargement différé de DLL, en spécifiant [/retarder](delay-delay-load-import-settings.md): nobind sur la ligne de commande de l’éditeur de liens empêche la table d’adresses importation liées généré et beaucoup d’espace dans le fichier image.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](linker-support-for-delay-loaded-dlls.md)
