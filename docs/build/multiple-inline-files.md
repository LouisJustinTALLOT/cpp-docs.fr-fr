---
title: Fichiers Inline multiples | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9be15f029c0aaab3ca4bc47fb183e1499c2e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368211"
---
# <a name="multiple-inline-files"></a>Fichiers inline multiples
Une commande peut créer plusieurs fichiers inline.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Notes  
 Pour chaque fichier, spécifiez une ou plusieurs lignes de texte inline suivies par une ligne de fin contenant le délimiteur. Commencer le texte du deuxième fichier sur la ligne suivante pour le premier fichier de délimitation.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)