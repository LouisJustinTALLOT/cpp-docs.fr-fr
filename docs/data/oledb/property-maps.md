---
title: Mappages de propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbed70f7871cb215a944a5143793b26b4196d7bc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052748"
---
# <a name="property-maps"></a>Mappages des propriétés

En plus de la session, un ensemble de lignes et un objet de commande facultatifs, chaque fournisseur prend en charge une ou plusieurs propriétés. Ces propriétés sont définies dans les mappages de propriété contenus dans les fichiers d’en-tête créés par l’Assistant fournisseur OLE DB. Chaque fichier d’en-tête contient un mappage pour les propriétés dans le groupe de propriétés OLE DB définis pour l’ou les objets définis dans ce fichier. Le fichier d’en-tête qui contient l’objet de source de données contient également le mappage des propriétés pour le [propriétés DataSource](https://msdn.microsoft.com/library/ms724188). Session.h contient le mappage des propriétés pour le [propriétés de la Session](/previous-versions/windows/desktop/ms714221). Les objets ensemble de lignes et commande résident dans un fichier d’en-tête unique, appelé *nom_projet*RS.h. Ces propriétés sont des membres de la [propriétés de l’ensemble de lignes](/previous-versions/windows/desktop/ms711252) groupe.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)