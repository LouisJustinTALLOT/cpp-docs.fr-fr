---
title: CMyProviderRowset (MyProviderRS.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 936c8fe849e2eb92b8eb46170fc3e67842ad6beb
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338848"
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
L’Assistant génère une entrée pour l’objet d’ensemble de lignes. Il s'appelle ici `CMyProviderRowset`. Le `CMyProviderRowset` classe hérite d’une classe de fournisseur OLE DB appelée `CRowsetImpl`, qui implémente toutes les interfaces nécessaires pour l’objet d’ensemble de lignes. Le code suivant montre la chaîne d’héritage pour `CRowsetImpl`:  
  
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
 [Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)