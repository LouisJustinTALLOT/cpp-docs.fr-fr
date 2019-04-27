---
title: CEnumeratorAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: e609b346bb4a0c2469c24e20540c646fa869ae26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230730"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor, classe

Utilisé par [CEnumerator](../../data/oledb/cenumerator-class.md) accéder aux données à partir de l’ensemble de lignes d’énumérateur.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_bIsParent](#bisparent)|Une variable qui indique si l’énumérateur est un énumérateur parent, si la ligne est un énumérateur.|
|[m_nType](#ntype)|Une variable qui indique si la ligne décrit une source de données ou d’un énumérateur.|
|[m_szDescription](#szdescription)|Description de la source de données ou de l’énumérateur.|
|[m_szName](#szname)|Le nom de la source de données ou de l’énumérateur.|
|[m_szParseName](#szparsename)|Chaîne à passer au [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) pour obtenir un moniker de la source de données ou d’un énumérateur.|

## <a name="remarks"></a>Notes

Cet ensemble de lignes se compose des sources de données et des énumérateurs visibles à partir de l’énumérateur en cours.

## <a name="bisparent"></a> CEnumeratorAccessor::m_bIsParent

Une variable qui indique si l’énumérateur est un énumérateur parent, si la ligne est un énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Notes

Consultez [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

## <a name="ntype"></a> CEnumeratorAccessor::m_nType

Une variable qui indique si la ligne décrit une source de données ou d’un énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Notes

Consultez [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

## <a name="szdescription"></a> CEnumeratorAccessor::m_szDescription

Description de la source de données ou de l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Notes

Consultez [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

## <a name="szname"></a> CEnumeratorAccessor::m_szName

Le nom de la source de données ou de l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Notes

Consultez [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

## <a name="szparsename"></a> CEnumeratorAccessor::m_szParseName

Chaîne à passer au [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) pour obtenir un moniker de la source de données ou d’un énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Notes

Consultez [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *de référence du programmeur OLE DB* pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)