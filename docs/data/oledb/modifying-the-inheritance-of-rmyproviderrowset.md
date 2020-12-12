---
description: 'En savoir plus sur : modification de l’héritage de RCustomRowset'
title: Modification de l’héritage de RCustomRowset
ms.date: 10/26/2018
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
ms.openlocfilehash: c54533122083c526ad12ac6514efa3ad9ba47cf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287006"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modification de l’héritage de RCustomRowset

Pour ajouter l' `IRowsetLocate` interface à l’exemple de fournisseur simple en lecture seule, modifiez l’héritage de `CCustomRowset` . Initialement, `CCustomRowset` hérite de `CRowsetImpl` . Vous devez le modifier pour qu’il hérite de `CRowsetBaseImpl` .

Pour ce faire, créez une nouvelle classe, `CCustomRowsetImpl` , dans le port *personnalisé* RS. h :

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

À présent, modifiez le mappage d’interface COM dans l’interface RS. h *personnalisée* comme suit :

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Ce code crée un mappage d’interface COM qui indique `CMyRowsetImpl` à d’appeler à `QueryInterface` la fois pour les `IRowset` `IRowsetLocate` interfaces et. Pour obtenir toute l’implémentation pour les autres classes d’ensemble de lignes, le mappage lie la `CMyRowsetImpl` classe à la `CRowsetBaseImpl` classe définie par les modèles OLE DB ; la carte utilise la macro COM_INTERFACE_ENTRY_CHAIN, qui indique à OLE DB modèles d’analyser la table com en `CRowsetBaseImpl` réponse à un `QueryInterface` appel.

Enfin, liez `CCustomRowset` à `CMyRowsetBaseImpl` en modifiant `CCustomRowset` pour hériter de `CMyRowsetImpl` , comme suit :

```cpp
class CCustomRowset : public CMyRowsetImpl<CCustomRowset, CCustomWindowsFile, CCustomCommand>
```

`CCustomRowset` peut désormais utiliser l' `IRowsetLocate` interface tout en tirant parti du reste de l’implémentation pour la classe rowset.

Une fois cette opération effectuée, vous pouvez [déterminer de façon dynamique les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Amélioration du fournisseur de Read-Only simple](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
