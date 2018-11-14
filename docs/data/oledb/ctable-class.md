---
title: CTable, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 7605d78a140a0f5353a16b9e22d5d618d29ff327
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556679"
---
# <a name="ctable-class"></a>CTable, classe

Fournit un moyen d’accéder directement à un rowset simple (sans paramètres).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur.

*TRowset*<br/>
Une classe rowset.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Ouvrir](#open)|La table s’ouvre.|

## <a name="remarks"></a>Notes

Consultez [CCommand](../../data/oledb/ccommand-class.md) pour plus d’informations sur la façon d’exécuter une commande pour accéder à un ensemble de lignes.

## <a name="open"></a> CTable::Open

La table s’ouvre.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
[in] La session pour laquelle la table est ouvert.

*wszTableName*<br/>
[in] Le nom de la table à ouvrir, transmis sous forme de chaîne Unicode.

*szTableName*<br/>
[in] Le nom de la table à ouvrir, transmis sous forme de chaîne ANSI.

*dbid*<br/>
[in] Le `DBID` de la table à ouvrir.

*pPropSet*<br/>
[in] Un pointeur vers un tableau de [DBPROPSET](https://docs.microsoft.com/previous-versions/windows/desktop/ms714367(v=vs.85)) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](https://docs.microsoft.com/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows. La valeur par défaut NULL ne spécifie aucuns propriétés.

*ulPropSets*<br/>
[in] Le nombre de [DBPROPSET](https://docs.microsoft.com/previous-versions/windows/desktop/ms714367(v=vs.85)) structures passées dans le *pPropSet* argument.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IOpenRowset::OpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716724(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)