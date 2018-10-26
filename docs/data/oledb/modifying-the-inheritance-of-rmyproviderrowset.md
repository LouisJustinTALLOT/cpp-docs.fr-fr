---
title: Modification de l’héritage de RCustomRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1a9b6e238d3824451ab0f820917c34c97826ffab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060388"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modification de l’héritage de RCustomRowset

Pour ajouter le `IRowsetLocate` l’interface à l’exemple de fournisseur simple en lecture seule, modifiez l’héritage de `RCustomRowset`. Initialement, `RCustomRowset` hérite `CRowsetImpl`. Vous devez modifier qu’elle hérite de `CRowsetBaseImpl`.

Pour ce faire, créez une nouvelle classe, `CCustomRowsetImpl`, dans CustomRS.h :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CCustomRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

À présent, modifiez le mappage d’interface COM dans CustomRS.h comme suit :

```cpp
BEGIN_COM_MAP(CCustomRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Cette opération crée un mappage d’interface COM qui indique à `CCustomRowsetImpl` pour appeler `QueryInterface` à la fois pour le `IRowset` et `IRowsetLocate` interfaces. Pour obtenir l’ensemble de l’implémentation pour l’ensemble de lignes autres classes, les liens de mappage les `CCustomRowsetImpl` classe revenir à la `CRowsetBaseImpl` classe définis par les modèles OLE DB ; le mappage utilise la macro COM_INTERFACE_ENTRY_CHAIN, qui indique aux modèles OLE DB d’analyser le mappage COM dans `CRowsetBaseImpl` en réponse à une `QueryInterface` appeler.

Enfin, liez `RAgentRowset` à `CCustomRowsetBaseImpl` en modifiant `RAgentRowset` d’hériter de `CCustomRowsetImpl`, comme suit :

```cpp
class RAgentRowset : public CCustomRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>
```

`RAgentRowset` peuvent désormais utiliser le `IRowsetLocate` interface tout en tirant parti du reste de l’implémentation pour la classe rowset.

Dans ce cas, vous pouvez [déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md)