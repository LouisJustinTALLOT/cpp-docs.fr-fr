---
title: Liaison d’importations | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 551028999d11379c06d3319f01e882a33ad57936
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705196"
---
# <a name="binding-imports"></a>Liaison d’importations

Le comportement de l’éditeur de liens par défaut consiste à créer une table d’adresse d’importation peut être liée pour le DLL à chargement différé. Si la DLL est liée, la fonction d’assistance tente d’utiliser les informations liées au lieu d’appeler **GetProcAddress** sur chacun des importations référencées. Si l’horodatage ou l’adresse préférée ne correspondre pas celles de la DLL chargée, la fonction d’assistance suppose que la table d’adresses importation liées est obsolète et poursuit comme si elle n’existe pas.

Si vous n’envisagez pas de lier les importations à chargement différé de DLL, en spécifiant [/retarder](../../build/reference/delay-delay-load-import-settings.md): nobind sur la ligne de commande de l’éditeur de liens empêche la table d’adresses importation liées généré et beaucoup d’espace dans le fichier image.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)