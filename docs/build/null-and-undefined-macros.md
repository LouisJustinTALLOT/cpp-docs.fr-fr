---
title: Macros nulles et non définies | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494a084ee5ba1da29c132aa632b647b37f305855
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368468"
---
# <a name="null-and-undefined-macros"></a>Macros nulles et non définies
L’expansion des macros nulles et non définies pour les chaînes null, mais une macro définie comme une chaîne null est considérée comme défini dans les expressions de prétraitement. Pour définir une macro comme une chaîne null, spécifiez aucun caractère à l’exception des espaces ou des tabulations après le signe égal (=) dans une ligne de commande ou un fichier de commandes et placez la chaîne null ou la définition des guillemets doubles ( » «). Pour supprimer la définition d’une macro, utilisez **! UNDEF.** Pour plus d’informations, consultez [Directives de prétraitement Makefile](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)