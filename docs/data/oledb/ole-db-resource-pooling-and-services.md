---
title: Services et regroupement des ressources OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210026"
---
# <a name="ole-db-resource-pooling-and-services"></a>Services et regroupement des ressources OLE DB

Pour fonctionner correctement avec le regroupement OLE DB, ou avec n’importe quel service OLE DB, votre fournisseur doit prendre en charge l’agrégation de tous les objets. Il s’agit d’une exigence d’un fournisseur OLE DB 1,5 ou version ultérieure. Il est essentiel pour tirer parti des services. Les fournisseurs qui ne prennent pas en charge l’agrégation ne peuvent pas être regroupés et aucun service supplémentaire n’est fourni.

Pour être regroupés, les fournisseurs doivent prendre en charge le modèle de thread libre. Le pool de ressources détermine le modèle de thread du fournisseur en fonction de la propriété DBPROP_THREADMODEL.

Si le fournisseur a un état de connexion global qui peut changer pendant que la source de données est dans un état initialisé, il doit prendre en charge la nouvelle propriété de DBPROP_RESETDATASOURCE. Cette propriété est appelée avant la réutilisation d’une connexion et donne au fournisseur la possibilité de nettoyer l’état avant sa prochaine utilisation. Si le fournisseur ne peut pas nettoyer un état associé à la connexion, il peut retourner DBPROPSTATUS_NOTSETTABLE pour la propriété et la connexion n’est pas réutilisée.

Les fournisseurs qui se connectent à une base de données distante et peuvent détecter si cette connexion peut être perdue doivent prendre en charge la propriété DBPROP_CONNECTIONSTATUS. Cette propriété donne au OLE DB services la possibilité de détecter les connexions inactives et de s’assurer qu’elles ne sont pas retournées au pool.

Enfin, l’inscription automatique de la transaction ne fonctionne généralement pas, sauf si elle est implémentée au même niveau que le regroupement. Les fournisseurs qui prennent en charge l’inscription de transaction automatique doivent prendre en charge la désactivation de cette inscription en exposant la propriété DBPROP_INIT_OLEDBSERVICES et en désactivant l’inscription si la DBPROPVAL_OS_TXNENLISTMENT est désélectionnée.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)
