---
title: "Spécificateurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a242c2c517f7db6f75b825bd13396637a64d138
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="specifiers"></a>Spécificateurs
Cette rubrique décrit la *decl-specifiers* composant (spécificateurs de déclaration) d’un [déclaration](declarations-and-definitions-cpp.md).  
  
 Les espaces réservés et les mots clés de langage suivants sont des spécificateurs de déclaration :  
  
 *spécificateur de classe de stockage*  
  
 *spécificateur de type*  
  
 *spécificateur de fonction*  
  
 [Friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [__declspec](../cpp/declspec.md) `(` *extended-decl-modifier-seq*`)`  
  
## <a name="remarks"></a>Remarques  
 Le *decl-specifiers* partie d’une déclaration est la plus longue séquence de *decl-specifiers* qui peuvent être prises pour signifier un nom de type, sans inclure le pointeur ou de modificateurs de référence. Le reste de la déclaration est la *déclarateur*, qui inclut le nom introduit.  
  
 Le tableau suivant répertorie quatre déclarations et puis de chaque déclaration *decl-specifers* et *déclarateur* composant séparément.  
  
|Déclaration|*decl-specifiers*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 Étant donné que `signed`, `unsigned`, `long`, et `short` impliquent tous `int`, un `typedef` nom suivant une de ces mots clés est considérée comme un membre de *declarator-list,* pas de *decl-specifiers*.  
  
> [!NOTE]
>  Comme un nom peut être redéclaré, sa traduction est soumise à la déclaration la plus récente de la portée actuelle. Une nouvelle déclaration peut affecter la façon dont les noms sont interprétés par le compilateur, notamment des noms `typedef`.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations et définitions](declarations-and-definitions-cpp.md)