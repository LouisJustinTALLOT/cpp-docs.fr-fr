---
title: Création d'un fournisseur simple accessible en lecture seule
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: c7c6c5bb2691a110a6368decd875f5a5a06b11b5
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919187"
---
# <a name="creating-a-simple-read-only-provider"></a>Création d'un fournisseur simple accessible en lecture seule

::: moniker range="msvc-160"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

Lorsque vous avez créé un fournisseur OLE DB à l’aide de l’ **Assistant Projet ATL** et de l’ **Assistant Fournisseur OLE DB ATL** , vous pouvez ajouter d’autres fonctionnalités que vous souhaitez prendre en charge. Commencez la conception de votre fournisseur en examinant le type de données que vous prévoyez d’envoyer au consommateur et dans quelles conditions. Il est particulièrement important de déterminer si vous avez besoin de prendre en charge les commandes, les transactions et d’autres objets facultatifs. Une bonne conception en amont permet d’accélérer l’implémentation et les tests.

L’exemple est présenté en deux parties :

- La première partie montre comment [créer un fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) qui lit une paire de chaînes.

- La seconde partie montre comment [améliorer le fournisseur simple en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md) en ajoutant l’interface `IRowsetLocate`.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
