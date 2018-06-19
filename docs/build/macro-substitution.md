---
title: Substitution de macro | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4028ee710cf38b6a4ef929de9a7e4ffad95f3e41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368068"
---
# <a name="macro-substitution"></a>Substitution macro
Lorsque *nom_macro* est appelé, chaque occurrence de *string1* dans sa définition de la chaîne est remplacée par *chaîne2*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>Notes  
 Substitution de macro respecte la casse et est littérale ; *string1* et *chaîne2* ne peut pas appeler des macros. Substitution ne modifie pas la définition d’origine. Vous pouvez substituer du texte dans n’importe quelle macro prédéfinie, sauf [ $$@ ](../build/filename-macros.md).  
  
 Aucun des espaces ou des tabulations, faites précéder le signe deux-points ; ceux-ci sont interprétés en tant que littéral. Si *chaîne2* est null, toutes les occurrences de *string1* sont supprimés de la chaîne de définition de la macro.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’une macro NMAKE](../build/using-an-nmake-macro.md)