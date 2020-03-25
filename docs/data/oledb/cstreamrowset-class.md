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
ms.openlocfilehash: 300933fd6d10f5da39d9276db746ab789851a9a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211170"
---
# <a name="cstreamrowset-class"></a>CStreamRowset, classe

Utilisé dans une déclaration `CCommand` ou `CTable`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Constructeur. Instancie et initialise l’objet `CStreamRowset`.|
|[Close](#close)|Libère le pointeur d’interface [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) dans la classe.|

## <a name="remarks"></a>Notes

Utilisez `CStreamRowset` dans votre déclaration de `CCommand` ou de `CTable`, par exemple :

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

or

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` retourne un pointeur de `ISequentialStream`, qui est stocké dans `m_spStream`. Vous utilisez ensuite la méthode `Read` pour récupérer les données (chaîne Unicode) au format XML. Par exemple :

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 effectue la mise en forme XML et retourne toutes les colonnes et toutes les lignes de l’ensemble de lignes sous la forme d’une chaîne XML.

> [!NOTE]
>  Cette fonctionnalité fonctionne avec SQL Server 2000 uniquement.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset :: CStreamRowset

Instancie et initialise l’objet `CStreamRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset :: Close

Libère le pointeur d’interface [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) dans la classe.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
