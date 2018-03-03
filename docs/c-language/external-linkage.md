---
title: Liaison externe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aef61c580306cc40ef1a89c6a389c7fbaf64a5f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="external-linkage"></a>Liaison externe
Si la première déclaration au niveau de la portée du fichier d'un identificateur n'utilise pas le spécificateur de classe de stockage **static**, l'objet a une liaison externe.  
  
 Si la déclaration d'un identificateur pour une fonction ne comporte aucun *storage-class-specifier*, sa liaison est déterminée exactement comme s'il était déclaré avec le *storage-class-specifier* `extern`. Si la déclaration d'un identificateur pour un objet a une portée de fichier et aucun *storage-class-specifier*, sa liaison est externe.  
  
 Le nom d'un identificateur avec liaison externe désigne la même fonction ou le même objet de données que toute autre déclaration du même nom avec liaison externe. Les deux déclarations peuvent se trouver dans la même unité de traduction ou dans des unités différentes. Si l'objet ou la fonction a également une durée de vie globale, il ou elle est partagé(e) par le programme entier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)