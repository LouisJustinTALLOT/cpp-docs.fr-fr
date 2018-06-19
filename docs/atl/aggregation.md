---
title: Agrégation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353961"
---
# <a name="aggregation"></a>Agrégation
Il existe des cas de circonstances implémentation d’un objet pour tirer parti des services offerts par un autre objet prégénéré. En outre, il souhaite que cet objet s’affichent en tant que dans le cadre de la première. COM réalise cet objectif grâce à la relation contenant-contenu et d’agrégation.  
  
 L’agrégation signifie que l’objet de conteneur (externe) crée l’objet de contenu (interne) dans le cadre du processus de création et les interfaces de l’objet interne sont exposées en externe. Un objet permet de lui-même doit être agrégée ou non. S’il s’agit, il doit suivre certaines règles pour l’agrégation pour fonctionner correctement.  
  
 Principalement, tous les **IUnknown** des appels de méthode sur l’objet de relation contenant-contenu doivent déléguer à l’objet conteneur.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [Réutilisation d’objets](http://msdn.microsoft.com/library/windows/desktop/ms678443)

