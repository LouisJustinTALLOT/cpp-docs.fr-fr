---
description: 'En savoir plus sur : amélioration du fournisseur de Read-Only simple'
title: Amélioration du fournisseur simple accessible en lecture seule
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: 00a0ea4fb9b759447026353ba0d78c7c856b15ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317634"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Amélioration du fournisseur simple accessible en lecture seule

Cette section montre comment améliorer le [fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) créé dans la section précédente. `IRowsetLocateImpl` crée une implémentation pour l' `IRowsetLocate` interface et ajoute la prise en charge des signets pour vous.

Si vous disposez d’un fournisseur opérationnel, vous pouvez l’améliorer pour mettre à jour le fournisseur, gérer les transactions ou améliorer les performances de l’algorithme d’extraction de lignes. La plupart des améliorations du fournisseur impliquent l’ajout d’une interface à un objet COM existant.

L’exemple des rubriques suivantes améliore le mécanisme d’extraction de lignes en ajoutant l' `IRowsetLocate` interface à `CAgentRowset` . Les rubriques vous montrent comment :

- [Faire en sorte que RCustomRowset hérite de IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Déterminez dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur de Read-Only simple](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
