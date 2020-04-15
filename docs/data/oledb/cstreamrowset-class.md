---
title: CStreamRowset, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366271"
---
# <a name="cstreamrowset-class"></a>CStreamRowset, classe

Utilisé dans `CCommand` `CTable` une ou une déclaration.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Paramètres

*TAccessor (en anglais)*<br/>
Un cours d’accesseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CStreamRowset (en anglais)](#cstreamrowset)|Constructeur. Instantanéise et initialise `CStreamRowset` l’objet.|
|[Fermer](#close)|Sortie du pointeur [d’interface ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) dans la classe.|

## <a name="remarks"></a>Notes

Utiliser `CStreamRowset` dans `CCommand` `CTable` votre déclaration ou, par exemple :

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

or

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`retourne `ISequentialStream` un pointeur, `m_spStream`qui est stocké dans . Vous utilisez `Read` ensuite la méthode pour récupérer les données (chaîne Unicode) en format XML. Par exemple :

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 effectue le formatage XML, et retournera toutes les colonnes et toutes les lignes de l’achaset comme une seule chaîne XML.

> [!NOTE]
> Cette fonctionnalité fonctionne uniquement avec SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset::CStreamRowset

Instantanéise et initialise `CStreamRowset` l’objet.

### <a name="syntax"></a>Syntaxe

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset::Fermer

Sortie du pointeur [d’interface ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) dans la classe.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB Consumer Templates Référence](../../data/oledb/ole-db-consumer-templates-reference.md)
