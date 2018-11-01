---
title: Création d'un fournisseur simple accessible en lecture seule
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 2ac8e45ca06a5566923141adf5a22dc6710eeeab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432602"
---
# <a name="creating-a-simple-read-only-provider"></a>Création d'un fournisseur simple accessible en lecture seule

Lorsque vous avez créé un fournisseur OLE DB à l’aide de la **Assistant Projet ATL** et **Assistant fournisseur OLE DB ATL**, vous pouvez ajouter d’autres fonctionnalités que vous souhaitez prendre en charge. Commencez la conception de votre fournisseur en examinant le type de données que vous prévoyez d’envoyer au consommateur et dans quelles conditions. Il est particulièrement important de déterminer si vous avez besoin prendre en charge les commandes, les transactions et les autres objets facultatifs. Une bonne conception en amont permet d’accélérer implémentation et au test.

L’exemple est présenté en deux parties :

- La première partie montre comment [créer un fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) qui lit une paire de chaînes.

- La seconde partie montre comment [améliorer le fournisseur simple en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md) en ajoutant le `IRowsetLocate` interface.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
