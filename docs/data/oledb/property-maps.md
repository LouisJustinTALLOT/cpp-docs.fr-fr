---
title: Mappages des propriétés
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 0e1e9999c63bfa525988b67d020031fd76514b67
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415888"
---
# <a name="property-maps"></a>Mappages des propriétés

Avec la session, un ensemble de lignes et un objet de commande facultatifs, chaque fournisseur prend en charge une ou plusieurs propriétés. Ces propriétés sont définies dans les mappages de propriété stockés dans les fichiers d’en-tête créés par le **Assistant fournisseur OLE DB**. Chaque fichier d’en-tête contient un mappage pour les propriétés dans le groupe de propriétés OLE DB définis pour l’ou les objets définis dans ce fichier. Le fichier d’en-tête qui contient l’objet de source de données contient également le mappage des propriétés pour le [propriétés DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` contient le mappage des propriétés pour le [propriétés de la Session](/previous-versions/windows/desktop/ms714221(v=vs.85)). Les objets de l’ensemble de lignes et de commande sont dans un fichier d’en-tête unique, appelé *nom_projet*RS.h. Ces propriétés sont des membres de la [propriétés de l’ensemble de lignes](/previous-versions/windows/desktop/ms711252(v=vs.85)) groupe.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
