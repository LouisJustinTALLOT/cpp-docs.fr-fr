---
title: À l’aide d’une Macro NMAKE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf098a3723aa7b067b8192bf503975998e4e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380574"
---
# <a name="using-an-nmake-macro"></a>Utilisation d'une macro NMAKE
Pour utiliser une macro, placez son nom entre parenthèses précédées du signe dollar ($) comme suit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>Notes  
 Aucun des espaces ne sont autorisés. Les parenthèses sont facultatives si *nom_macro* est un caractère unique. La chaîne de définition remplace $(*nom_macro*) ; une macro non définie est remplacée par une chaîne null.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
 [Substitution macro](../build/macro-substitution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [NMAKE et les macros](../build/macros-and-nmake.md)