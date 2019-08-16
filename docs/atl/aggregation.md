---
title: Agrégation
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491980"
---
# <a name="aggregation"></a>Agrégation

Il arrive parfois que l’implémenteur d’un objet souhaite tirer parti des services offerts par un autre objet prédéfini. En outre, il aimerait que ce deuxième objet apparaisse comme une partie naturelle du premier. COM réalise ces deux objectifs grâce à la relation contenant-contenu et à l’agrégation.

L’agrégation signifie que l’objet conteneur (externe) crée l’objet contenu (interne) dans le cadre de son processus de création et que les interfaces de l’objet interne sont exposées par le externe. Un objet peut être agrégé ou non. Si c’est le cas, il doit suivre certaines règles pour que l’agrégation fonctionne correctement.

En premier lieu `IUnknown` , tous les appels de méthode sur l’objet contenu doivent déléguer à l’objet conteneur.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Réutilisation d’objets](/windows/win32/com/reusing-objects)
