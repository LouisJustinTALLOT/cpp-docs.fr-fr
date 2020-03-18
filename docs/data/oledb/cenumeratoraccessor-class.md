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
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
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
ms.openlocfilehash: d85f630a01ab7e2a07035a8a304a56be91eca8a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442003"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor, classe

Utilisé par [CEnumerator](../../data/oledb/cenumerator-class.md) pour accéder aux données de l’ensemble de lignes de l’énumérateur.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_bIsParent](#bisparent)|Variable qui indique si l’énumérateur est un énumérateur parent, si la ligne est un énumérateur.|
|[m_nType](#ntype)|Variable qui indique si la ligne décrit une source de données ou un énumérateur.|
|[m_szDescription](#szdescription)|Description de la source de données ou de l’énumérateur.|
|[m_szName](#szname)|Nom de la source de données ou de l’énumérateur.|
|[m_szParseName](#szparsename)|Chaîne à passer à [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) pour obtenir un moniker de la source de données ou de l’énumérateur.|

## <a name="remarks"></a>Notes

Cet ensemble de lignes se compose des sources de données et des énumérateurs visibles à partir de l’énumérateur actuel.

## <a name="bisparent"></a>CEnumeratorAccessor :: m_bIsParent

Variable qui indique si l’énumérateur est un énumérateur parent, si la ligne est un énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

## <a name="ntype"></a>CEnumeratorAccessor :: m_nType

Variable qui indique si la ligne décrit une source de données ou un énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

## <a name="szdescription"></a>CEnumeratorAccessor :: m_szDescription

Description de la source de données ou de l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

## <a name="szname"></a>CEnumeratorAccessor :: m_szName

Nom de la source de données ou de l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

## <a name="szparsename"></a>CEnumeratorAccessor :: m_szParseName

Chaîne à passer à [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) pour obtenir un moniker de la source de données ou de l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) dans le *Guide de référence du programmeur de OLE DB* .

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)