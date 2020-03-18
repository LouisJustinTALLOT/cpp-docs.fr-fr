---
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
ms.openlocfilehash: 2c84ff359bdbb39f281928fa0135edd40b1f7d20
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446082"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

L’Assistant génère une entrée pour l’objet rowset. Dans ce cas, il s’agit de `CCustomRowset`. La classe `CCustomRowset` hérite d’une classe de fournisseur OLE DB nommée `CRowsetImpl`, qui implémente toutes les interfaces nécessaires pour l’objet rowset. Le code suivant montre la chaîne d’héritage pour `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` utilise également les interfaces `IAccessor` et `IColumnsInfo`. Elle utilise ces interfaces pour les champs de sortie dans les tables. La classe fournit également une implémentation pour `IRowsetIdentity`, qui permet au consommateur de déterminer si deux lignes sont identiques. L’interface `IRowsetInfo` implémente les propriétés de l’objet rowset. L’interface `IConvertType` permet au fournisseur de résoudre les différences entre les types de données demandés par le consommateur et ceux utilisés par le fournisseur.

L’interface `IRowset` gère en fait la récupération des données. Le consommateur appelle d’abord une méthode appelée `GetNextRows` pour retourner un handle vers une ligne, appelée `HROW`. Le consommateur appelle ensuite `IRowset::GetData` avec cette `HROW` pour récupérer les données demandées.

`CRowsetImpl` prend également plusieurs paramètres de modèle. Ces paramètres vous permettent de déterminer comment la classe `CRowsetImpl` gère les données. L’argument `ArrayType` vous permet de déterminer le mécanisme de stockage utilisé pour stocker les données de ligne. Le paramètre *RowClass* spécifie la classe qui contient un `HROW`.

Le paramètre *RowsetInterface* vous permet également d’utiliser l’interface `IRowsetLocate` ou `IRowsetScroll`. Les interfaces `IRowsetLocate` et `IRowsetScroll` héritent toutes deux de `IRowset`. Par conséquent, les modèles du fournisseur OLE DB doivent fournir une gestion spéciale pour ces interfaces. Si vous souhaitez utiliser l’une de ces interfaces, vous devez utiliser ce paramètre.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
