---
title: Spécificateurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d437b70148fdaba4c8eb4d7aa855e7d75f6f2487
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953745"
---
# <a name="specifiers"></a>Spécificateurs
Cette rubrique décrit la *decl-specifiers* composant (spécificateurs de déclaration) d’un [déclaration](declarations-and-definitions-cpp.md).  
  
 Les espaces réservés et les mots clés de langage suivants sont des spécificateurs de déclaration :  
  
 *spécificateur de classe de stockage*  
  
 *spécificateur de type*  
  
 *spécificateur de fonction*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [(typedef)] ( [typedef](http://msdn.microsod) `(` *extended-decl-modifier-seq* `)`  
  
## <a name="remarks"></a>Notes  
 Le *decl-specifiers* partie d’une déclaration est la plus longue séquence de *decl-specifiers* pouvant être prise pour indiquer un nom de type, sans inclure le pointeur ou modificateurs de référence. Le reste de la déclaration est la *déclarateur*, qui inclut le nom introduit.  
  
 Le tableau suivant présente les quatre déclarations et la liste de chaque déclaration *decl-specifers* et *déclarateur* composant séparément.  
  
|Déclaration|*decl-specifiers*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|**char**|`*lpszAppName`|  
|`typedef char * LPSTR;`|**char**|`*LPSTR`|  
|`const int func1();`|**int const**|`func1`|  
|`volatile void *pvvObj;`|**void volatile**|`*pvvObj`|  
  
 Étant donné que **signé**, **non signé**, **long**, et **court** impliquent tous **int**, un  **typedef** nom suivant une de ces mots clés est prise pour être membre du *declarator-list,* pas de *decl-specifiers*.  
  
> [!NOTE]
>  Comme un nom peut être redéclaré, sa traduction est soumise à la déclaration la plus récente de la portée actuelle. Une nouvelle déclaration peut affecter la façon dont les noms sont interprétés par le compilateur, notamment des noms `typedef`.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations et définitions](declarations-and-definitions-cpp.md)