---
title: Classes de base de données ATL (modèles OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5147610e580d3a67400893d41af8ad9728cc72a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071217"
---
# <a name="atl-database-classes-ole-db-templates"></a>Classes de bases de données ATL (modèles OLE DB)

Microsoft fournit plusieurs implémentations d’OLE DB, un ensemble d’interfaces COM qui assurent un accès uniforme aux données de diverses sources d’informations et de formats.  OLE DB est officiellement déconseillé ; Cette documentation est pour les développeurs chargés de la maintenant code hérité. Nouvelles applications doivent utiliser ODBC pour se connecter aux sources de données SQL.

Les modèles OLE DB sont des modèles C++ dans ATL qui facilitent la technologie de base de données OLE DB à utiliser en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées.

Cette bibliothèque de modèles contient deux parties :

- [Modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) permettent d’implémenter une application de client (consommateur) OLE DB.

- [Modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) permettent d’implémenter une application de serveur (fournisseur) OLE DB.

En outre, le [attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md) offrent un moyen pratique pour créer des consommateurs OLE DB. Les attributs OLE DB injectent du code basé sur les modèles du consommateur OLE DB pour créer des consommateurs OLE DB de travail.

Notez que la bibliothèque MFC contient une classe, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), qui affiche les enregistrements de base de données dans les contrôles. La vue est une vue de formulaire directement connectée à un `CRowset` de l’objet et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue.

Pour plus d’informations, consultez [programmation OLE DB](../data/oledb/ole-db-programming.md) et [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643).

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Création d’un fournisseur OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Référence des modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Référence des modèles du fournisseur OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Exemples de modèles OLE DB](https://github.com/Microsoft/VCSamples)