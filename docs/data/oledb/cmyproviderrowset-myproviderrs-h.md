---
description: 'En savoir plus sur : CCustomRowset (Customers. H)'
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 87025be2a34f8c850bde2be53ab01519968654d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170462"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

L’Assistant génère une entrée pour l’objet rowset. Dans ce cas, il est appelé `CCustomRowset` . La `CCustomRowset` classe hérite d’une classe de fournisseur OLE DB appelée `CRowsetImpl` , qui implémente toutes les interfaces nécessaires pour l’objet rowset. Le code suivant illustre la chaîne d’héritage pour `CRowsetImpl` :

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` utilise également les `IAccessor` `IColumnsInfo` interfaces et. Elle utilise ces interfaces pour les champs de sortie dans les tables. La classe fournit également une implémentation pour `IRowsetIdentity` , qui permet au consommateur de déterminer si deux lignes sont identiques. L' `IRowsetInfo` interface implémente les propriétés de l’objet rowset. L' `IConvertType` interface permet au fournisseur de résoudre les différences entre les types de données demandés par le consommateur et ceux utilisés par le fournisseur.

L' `IRowset` interface gère en fait la récupération des données. Le consommateur appelle d’abord une méthode appelée `GetNextRows` pour retourner un handle vers une ligne, appelée `HROW` . Le consommateur appelle ensuite `IRowset::GetData` `HROW` pour récupérer les données demandées.

`CRowsetImpl` prend également plusieurs paramètres de modèle. Ces paramètres vous permettent de déterminer la façon dont la `CRowsetImpl` classe gère les données. L' `ArrayType` argument vous permet de déterminer le mécanisme de stockage utilisé pour stocker les données de ligne. Le paramètre *RowClass* spécifie la classe qui contient un `HROW` .

Le paramètre *RowsetInterface* vous permet également d’utiliser l' `IRowsetLocate` `IRowsetScroll` interface ou. Les `IRowsetLocate` `IRowsetScroll` interfaces et héritent toutes deux de `IRowset` . Par conséquent, les modèles du fournisseur OLE DB doivent fournir une gestion spéciale pour ces interfaces. Si vous souhaitez utiliser l’une de ces interfaces, vous devez utiliser ce paramètre.

## <a name="see-also"></a>Voir aussi

[Fichiers de Wizard-Generated du fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
