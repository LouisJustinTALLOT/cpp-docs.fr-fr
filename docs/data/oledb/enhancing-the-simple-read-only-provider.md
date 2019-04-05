---
title: Amélioration du fournisseur simple accessible en lecture seule
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: d61f24a9a9abffe836a7f11bd5d1517fddf97fe7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034074"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Amélioration du fournisseur simple accessible en lecture seule

Cette section montre comment améliorer la [fournisseur simple en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md) créé dans la section précédente. `IRowsetLocateImpl` Crée une implémentation pour le `IRowsetLocate` interface et ajoute la prise en charge des signets pour vous.

Lorsque vous avez un fournisseur opérationnel, vous souhaiterez peut-être améliorer pour rendre la mise à jour du fournisseur, gérer des transactions ou améliorer les performances de l’algorithme de l’extraction de lignes. La plupart des améliorations du fournisseur impliquent l’ajout d’une interface à un objet COM existant.

L’exemple dans les rubriques suivantes améliore le mécanisme d’extraction de lignes en ajoutant le `IRowsetLocate` à l’interface `CAgentRowset`. Les rubriques vous montrent à :

- [Rendre RCustomRowset l’héritage de](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Création d'un fournisseur simple accessible en lecture seule](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
