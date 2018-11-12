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
ms.openlocfilehash: 1fb5164b9e744175f60c920a1d92278e9d5213f2
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264656"
---
# <a name="ole-db-resource-pooling-and-services"></a>Services et regroupement des ressources OLE DB

Pour fonctionner correctement avec le regroupement OLE DB, ou avec n’importe quel service OLE DB, votre fournisseur doit prendre en charge le regroupement de tous les objets. Il s’agit d’une exigence de tout OLE DB fournisseur 1.5 ou ultérieure. Il est essentiel pour tirer parti des services. Les fournisseurs qui ne prennent pas en charge d’agrégation ne peut pas être mis en pool et des services supplémentaires sont fournies.

Pour être regroupés, fournisseurs doivent prendre en charge le modèle de thread libre. Le pool de ressources détermine le modèle de fournisseur thread conformément à la propriété DBPROP_THREADMODEL.

Si le fournisseur a un état de connexion global qui peut changer pendant que la source de données est dans un état initialisé, il doit prendre en charge la nouvelle propriété DBPROP_RESETDATASOURCE. Cette propriété est appelée avant une connexion est réutilisée et donne le fournisseur la possibilité de nettoyer l’état avant son utilisation suivante. Si le fournisseur ne peut pas nettoyer un état associé à la connexion, il peut retourner DBPROPSTATUS_NOTSETTABLE pour la propriété et la connexion n’est pas réutilisée.

Les fournisseurs qui se connectent à une base de données distante et peuvent détecter si cette connexion est peut-être perdue doivent prendre en charge la propriété DBPROP_CONNECTIONSTATUS. Cette propriété donne aux services OLE DB la possibilité de détecter les connexions mortes et assurez-vous qu’ils ne sont pas retournées au pool.

Enfin, l’inscription de transaction automatique généralement ne fonctionne pas, sauf si elle est implémentée au même niveau que le regroupement. Les fournisseurs qui prennent en charge l’inscription de transaction automatique doivent prendre en charge la désactivation de cette inscription en exposant la propriété DBPROP_INIT_OLEDBSERVICES et en désactivant l’inscription si le DBPROPVAL_OS_TXNENLISTMENT est désélectionné.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)