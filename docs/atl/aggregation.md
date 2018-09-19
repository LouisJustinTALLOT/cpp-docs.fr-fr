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
ms.openlocfilehash: ce2fbe4a2dd566541a637459510ec8422b318c47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070912"
---
# <a name="aggregation"></a>Agrégation

Il est parfois quand un implémenteur d’un objet souhaitez tirer parti des services offerts par un autre objet prédéfini. En outre, il aimerait que ce deuxième objet à apparaissent sous la forme d’un composant naturel de la première. COM permet d’obtenir les deux de ces objectifs via l’agrégation et relation contenant-contenu.

L’agrégation signifie que l’objet conteneur (externe) crée l’objet (interne) contenu dans le cadre du processus de création et les interfaces de l’objet interne sont exposées en externe. Un objet s’autorise à être agrégée ou non. Dans le cas, il doit respecter certaines règles pour l’agrégation pour fonctionner correctement.

Principalement, tous les `IUnknown` des appels de méthode sur l’objet de relation contenant-contenu doivent déléguer à l’objet conteneur.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Réutilisation d’objets](/windows/desktop/com/reusing-objects)

