---
title: Macros nulles et non définies
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: cf2dce2132cc1e7065cb0b93f1debd403f7a8342
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417227"
---
# <a name="null-and-undefined-macros"></a>Macros nulles et non définies

L’expansion des macros nulles et non définies pour les chaînes null, mais une macro définie comme une chaîne null est considérée comme défini dans les expressions de prétraitement. Pour définir une macro comme une chaîne null, spécifiez aucun caractère à l’exception des espaces ou des tabulations après le signe égal (=) dans une ligne de commande ou d’un fichier de commandes et placez la chaîne null ou guillemets doubles ( » «). Pour supprimer la définition d’une macro, utilisez **! UNDEF.** Pour plus d’informations, consultez [Directives de prétraitement Makefile](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)
