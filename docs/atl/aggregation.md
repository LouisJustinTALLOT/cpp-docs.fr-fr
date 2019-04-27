---
title: Agrégation
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 2eec7a801f9fe16bc48fc888d10ce413ec7e79db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223504"
---
# <a name="aggregation"></a>Agrégation

Il est parfois quand un implémenteur d’un objet souhaitez tirer parti des services offerts par un autre objet prédéfini. En outre, il aimerait que ce deuxième objet à apparaissent sous la forme d’un composant naturel de la première. COM permet d’obtenir les deux de ces objectifs via l’agrégation et relation contenant-contenu.

L’agrégation signifie que l’objet conteneur (externe) crée l’objet (interne) contenu dans le cadre du processus de création et les interfaces de l’objet interne sont exposées en externe. Un objet s’autorise à être agrégée ou non. Dans le cas, il doit respecter certaines règles pour l’agrégation pour fonctionner correctement.

Principalement, tous les `IUnknown` des appels de méthode sur l’objet de relation contenant-contenu doivent déléguer à l’objet conteneur.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Réutilisation d’objets](/windows/desktop/com/reusing-objects)
