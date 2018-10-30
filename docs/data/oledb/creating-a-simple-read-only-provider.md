---
title: Création d’un fournisseur Simple en lecture seule | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8fd4e5eb25ab1e8e6b20b576a0688da7b5aa2ef
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216394"
---
# <a name="creating-a-simple-read-only-provider"></a>Création d'un fournisseur simple accessible en lecture seule

Lorsque vous avez créé un fournisseur OLE DB à l’aide de la **Assistant Projet ATL** et **Assistant fournisseur OLE DB ATL**, vous pouvez ajouter d’autres fonctionnalités que vous souhaitez prendre en charge. Commencez la conception de votre fournisseur en examinant le type de données que vous prévoyez d’envoyer au consommateur et dans quelles conditions. Il est particulièrement important de déterminer si vous avez besoin prendre en charge les commandes, les transactions et les autres objets facultatifs. Une bonne conception en amont permet d’accélérer implémentation et au test.

L’exemple est présenté en deux parties :

- La première partie montre comment [créer un fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) qui lit une paire de chaînes.

- La seconde partie montre comment [améliorer le fournisseur simple en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md) en ajoutant le `IRowsetLocate` interface.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
