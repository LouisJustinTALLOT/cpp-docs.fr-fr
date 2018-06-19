---
title: Liaison externe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43301686d5bdb964cf08e8123ff4c55475228567
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383200"
---
# <a name="external-linkage"></a>Liaison externe
Si la première déclaration au niveau de la portée du fichier d'un identificateur n'utilise pas le spécificateur de classe de stockage **static**, l'objet a une liaison externe.  
  
 Si la déclaration d'un identificateur pour une fonction ne comporte aucun *storage-class-specifier*, sa liaison est déterminée exactement comme s'il était déclaré avec le *storage-class-specifier* `extern`. Si la déclaration d'un identificateur pour un objet a une portée de fichier et aucun *storage-class-specifier*, sa liaison est externe.  
  
 Le nom d'un identificateur avec liaison externe désigne la même fonction ou le même objet de données que toute autre déclaration du même nom avec liaison externe. Les deux déclarations peuvent se trouver dans la même unité de traduction ou dans des unités différentes. Si l'objet ou la fonction a également une durée de vie globale, il ou elle est partagé(e) par le programme entier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)