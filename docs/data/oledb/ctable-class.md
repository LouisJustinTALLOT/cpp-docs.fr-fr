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
ms.openlocfilehash: 15081173edfae5ba0f881a6c1607a22e77a8a7c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452167"
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
[in] Un pointeur vers un tableau de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](/previous-versions/windows/desktop/ms713696) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows. La valeur par défaut NULL ne spécifie aucuns propriétés.

*ulPropSets*<br/>
[in] Le nombre de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures passées dans le *pPropSet* argument.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724) dans le *de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)