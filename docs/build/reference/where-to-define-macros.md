---
description: 'En savoir plus sur : où définir des macros'
title: Où définir des macros
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: b5fc7d6e1fd8247816993929791bf734596d00e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259199"
---
# <a name="where-to-define-macros"></a>Où définir des macros

Définissez les macros dans une ligne de commande, un fichier de commandes, un Makefile ou le fichier Tools.ini.

Dans un fichier Make ou Tools.ini, chaque définition de macro doit apparaître sur une ligne distincte et ne peut pas commencer par un espace ou une tabulation. Les espaces ou les tabulations autour du signe égal sont ignorés. Tous les [caractères de chaîne](defining-an-nmake-macro.md) sont des littéraux, y compris les guillemets et les espaces incorporés.

Dans une ligne de commande ou un fichier de commandes, les espaces et les tabulations délimitent les arguments et ne peuvent pas entourer le signe égal. Si `string` contient des espaces ou des tabulations, mettez la chaîne elle-même ou la totalité de la macro entre guillemets doubles ("").

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)
