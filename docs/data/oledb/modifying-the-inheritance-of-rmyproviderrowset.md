---
title: Modification de l’héritage de RCustomRowset | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
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
ms.openlocfilehash: 13e15b470be6f6a5af4f8012e3a70896f648e665
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216511"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modification de l’héritage de RCustomRowset

Pour ajouter le `IRowsetLocate` l’interface à l’exemple de fournisseur simple en lecture seule, modifiez l’héritage de `RCustomRowset`. Initialement, `RCustomRowset` hérite `CRowsetImpl`. Vous devez modifier qu’elle hérite de `CRowsetBaseImpl`.

Pour ce faire, créez une nouvelle classe, `CCustomRowsetImpl`, dans CustomRS.h :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

À présent, modifiez le mappage d’interface COM dans *personnalisé*RS.h comme suit :

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Ce code crée un mappage d’interface COM qui indique à `CMyRowsetImpl` pour appeler `QueryInterface` à la fois pour le `IRowset` et `IRowsetLocate` interfaces. Pour obtenir l’ensemble de l’implémentation pour l’ensemble de lignes autres classes, les liens de mappage les `CMyRowsetImpl` classe revenir à la `CRowsetBaseImpl` classe définis par les modèles OLE DB ; le mappage utilise la macro COM_INTERFACE_ENTRY_CHAIN, qui indique aux modèles OLE DB d’analyser le mappage COM dans `CRowsetBaseImpl` en réponse à une `QueryInterface` appeler.

Enfin, liez `RAgentRowset` à `CMyRowsetBaseImpl` en modifiant `RAgentRowset` d’hériter de `CMyRowsetImpl`, comme suit :

```cpp
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>
```

`RAgentRowset` peuvent désormais utiliser le `IRowsetLocate` interface tout en tirant parti du reste de l’implémentation pour la classe rowset.

Dans ce cas, vous pouvez [déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
