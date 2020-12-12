---
description: En savoir plus sur les mappages de propriétés
title: Mappages des propriétés
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 30b277451d871de45902661f7b7e56cbc7409c97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316906"
---
# <a name="property-maps"></a>Mappages des propriétés

Avec la session, l’ensemble de lignes et l’objet de commande facultatif, chaque fournisseur prend en charge une ou plusieurs propriétés. Ces propriétés sont définies dans les mappages de propriétés stockés dans les fichiers d’en-tête créés par l' **assistant OLE DB fournisseur**. Chaque fichier d’en-tête contient un mappage pour les propriétés du groupe de propriétés OLE DB défini pour l’objet ou les objets définis dans ce fichier. Le fichier d’en-tête qui contient l’objet source de données contient également le mappage des propriétés pour les [propriétés DataSource](/previous-versions/windows/desktop/ms724188(v=vs.85)). `Session.h` contient le mappage des propriétés pour les [Propriétés de session](/previous-versions/windows/desktop/ms714221(v=vs.85)). Les objets rowset et Command se trouvent dans un seul fichier d’en-tête, appelé *ProjectName* RS. h. Ces propriétés sont des membres du groupe de [Propriétés rowset](/previous-versions/windows/desktop/ms711252(v=vs.85)) .

## <a name="see-also"></a>Voir aussi

[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
