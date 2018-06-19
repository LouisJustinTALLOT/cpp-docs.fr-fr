---
title: -SECTION (EDITBIN) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e29e258b4fb661cfa06e057704bba983ad924f34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378351"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)
```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## <a name="remarks"></a>Notes  
 Cette option modifie les attributs d’une section, en substituant les attributs qui ont été définies lorsque le fichier de l’objet de la section a été compilé ou lié.  
  
 Après le signe deux-points ( **:** ), spécifiez la *nom* de la section. Pour modifier le nom de section, procédez comme *nom* par un signe égal (=) et un *newname* pour la section.  
  
 Pour définir ou modifier la section `attributes`, spécifiez une virgule (**,**) suivi d’un ou plusieurs caractères des attributs. Pour exclure un attribut, faites précéder son caractère avec un point d’exclamation ( !). Les caractères suivants spécifient les attributs de la mémoire :  
  
|Attribut|Paramètre|  
|---------------|-------------|  
|c|code|  
|d|pouvant être éliminée|  
|e|executable|  
|g|données initialisées|  
|k|mise en cache mémoire virtuelle|  
|m|lien Supprimer|  
|o|informations sur les liens|  
|p|mémoire virtuelle paginée|  
|r|read|  
|s|partagés|  
|u|données non initialisées|  
|s|écriture|  
  
 Contrôle *alignement*, spécifiez le caractère **A** suivie par l’un des caractères suivants pour définir la taille de l’alignement en octets, comme suit :  
  
|Caractère|Taille d’alignement en octets|  
|---------------|-----------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|s|64|  
|x|Aucun alignement|  
  
 Spécifiez le `attributes` et *alignement* caractères sous forme de chaîne sans espace blanc. Les caractères ne respectent pas la casse.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)