---
description: 'En savoir plus sur : liaison d’importations'
title: Liaison d’importations
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 7d1b4374bf1d3340a918f252d80102057febe053
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182708"
---
# <a name="binding-imports"></a>Liaison d’importations

Le comportement par défaut de l’éditeur de liens consiste à créer une table d’adresses d’importation pouvant être liée pour la DLL à chargement différé. Si la DLL est liée, la fonction d’assistance tente d’utiliser les informations liées au lieu d’appeler **GetProcAddress** sur chacune des importations référencées. Si l’horodateur ou l’adresse par défaut ne correspondent pas à ceux de la DLL chargée, la fonction d’assistance suppose que la table d’adresses d’importation liée est obsolète et se poursuit comme si elle n’existait pas.

Si vous n’envisagez pas de lier les importations à chargement différé de la DLL, la spécification de [/delay](delay-delay-load-import-settings.md): nobind sur la ligne de commande de l’éditeur de liens empêchera la génération de la table des adresses d’importation liées et l’utilisation de l’espace dans le fichier image.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
