---
title: Où définir des macros
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: 5a5e853627f5d337e3f0587cb41fdc77e7eeb4f5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417916"
---
# <a name="where-to-define-macros"></a>Où définir des macros

Définir des macros dans une ligne de commande, fichier de commandes, makefile ou le fichier Tools.ini.

Dans un makefile ou le fichier Tools.ini, chaque définition de macro doit figurer sur une ligne distincte et ne peut pas commencer par un espace ou une tabulation. Espaces ou des tabulations autour du signe égal sont ignorées. Tous les [chaîne de caractères](../build/defining-an-nmake-macro.md) sont littéraux, y compris les entourant de guillemets doubles et des espaces incorporés.

Dans une ligne de commande ou un fichier de commandes, les espaces et les tabulations délimitent les arguments et ne peuvent pas entourer le signe égal. Si `string` a incorporé des espaces ou des tabulations, mettez la chaîne elle-même ou la totalité de la macro entre guillemets doubles (« »).

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)
