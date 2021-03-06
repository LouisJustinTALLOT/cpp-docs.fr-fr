---
description: 'En savoir plus sur : CTable, classe'
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
ms.openlocfilehash: 62808080a68bbd5de00b39c43661e06617ba53f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317725"
---
# <a name="ctable-class"></a>CTable, classe

Fournit un moyen d’accéder directement à un ensemble de lignes simple (un sans paramètre).

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
Classe d’ensemble de lignes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Ouvrir](#open)|Ouvre la table.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur l’exécution d’une commande pour accéder à un ensemble de lignes, consultez la page [CCommand](../../data/oledb/ccommand-class.md) .

## <a name="ctableopen"></a><a name="open"></a> CTable :: Open

Ouvre la table.

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
dans Session pour laquelle la table est ouverte.

*wszTableName*<br/>
dans Nom de la table à ouvrir, passé comme chaîne Unicode.

*szTableName*<br/>
dans Nom de la table à ouvrir, passé comme chaîne ANSI.

*dbid*<br/>
dans `DBID` De la table à ouvrir.

*pPropSet*<br/>
dans Pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Consultez [jeux de propriétés et groupes de propriétés](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows. La valeur par défaut NULL ne spécifie aucune propriété.

*ulPropSets*<br/>
dans Nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passées dans l’argument *pPropSet* .

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IOpenRowset :: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
