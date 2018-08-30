---
title: Agrégation | Microsoft Docs
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
ms.openlocfilehash: 83d19e53b50791255b87cfa73a51761e2cdf5e1f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196143"
---
# <a name="aggregation"></a>Agrégation
Il est parfois quand un implémenteur d’un objet souhaitez tirer parti des services offerts par un autre objet prédéfini. En outre, il aimerait que ce deuxième objet à apparaissent sous la forme d’un composant naturel de la première. COM permet d’obtenir les deux de ces objectifs via l’agrégation et relation contenant-contenu.  
  
 L’agrégation signifie que l’objet conteneur (externe) crée l’objet (interne) contenu dans le cadre du processus de création et les interfaces de l’objet interne sont exposées en externe. Un objet s’autorise à être agrégée ou non. Dans le cas, il doit respecter certaines règles pour l’agrégation pour fonctionner correctement.  
  
 Principalement, tous les `IUnknown` des appels de méthode sur l’objet de relation contenant-contenu doivent déléguer à l’objet conteneur.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [Réutilisation d’objets](/windows/desktop/com/reusing-objects)

