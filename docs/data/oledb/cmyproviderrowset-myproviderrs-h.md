---
title: CCustomRowset (CustomRS.H) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 211c83ec63611c493f03e48b58619caca373ce65
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216355"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

L’Assistant génère une entrée pour l’objet d’ensemble de lignes. Dans ce cas, elle est appelée `CCustomRowset`. Le `CCustomRowset` classe hérite d’une classe de fournisseur OLE DB appelée `CRowsetImpl`, qui implémente toutes les interfaces nécessaires pour l’objet d’ensemble de lignes. Le code suivant montre la chaîne d’héritage pour `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` utilise également le `IAccessor` et `IColumnsInfo` interfaces. Il utilise ces interfaces pour les champs de sortie dans les tables. La classe fournit également une implémentation pour `IRowsetIdentity`, ce qui permet au consommateur de déterminer si deux lignes sont identiques. Le `IRowsetInfo` interface implémente les propriétés de l’objet d’ensemble de lignes. Le `IConvertType` interface permet au fournisseur résoudre les différences entre les types de données demandés par le consommateur et ceux utilisés par le fournisseur.

Le `IRowset` interface gère en fait la récupération des données. Le consommateur appelle d’abord une méthode appelée `GetNextRows` pour retourner un handle à une ligne, appelé un `HROW`. Le consommateur appelle ensuite `IRowset::GetData` avec qui `HROW` pour récupérer les données demandées.

`CRowsetImpl` prend également plusieurs paramètres de modèle. Ces paramètres permettent de déterminer comment la `CRowsetImpl` classe gère les données. Le `ArrayType` argument vous permet de déterminer le mécanisme de stockage est utilisé pour stocker les données de ligne. Le *RowClass* paramètre spécifie la classe qui contient un `HROW`.

Le *RowsetInterface* paramètre vous permet d’utiliser également le `IRowsetLocate` ou `IRowsetScroll` interface. Le `IRowsetLocate` et `IRowsetScroll` interfaces héritent toutes deux de `IRowset`. Par conséquent, les modèles du fournisseur OLE DB doivent assurer une gestion spéciale pour ces interfaces. Si vous souhaitez utiliser une de ces interfaces, vous devez utiliser ce paramètre.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
