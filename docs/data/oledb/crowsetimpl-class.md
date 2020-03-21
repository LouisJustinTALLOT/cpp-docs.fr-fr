---
title: CRowsetImpl, classe
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 956648babf987d156cac753f8373518a83362013
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079676"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl, classe

Fournit une implémentation de l’ensemble de lignes standard OLE DB sans nécessiter plusieurs héritages de nombreuses interfaces d’implémentation.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl :
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe de l’utilisateur qui dérive de `CRowsetImpl`.

*Stockage*<br/>
Classe d’enregistrement utilisateur.

*CreatorClass*<br/>
La classe qui contient les propriétés de l’ensemble de lignes ; en général, la commande.

*ArrayType*<br/>
Classe qui servira de stockage pour les données de l’ensemble de lignes. Par défaut, ce paramètre a la valeur `CAtlArray`, mais il peut s’agir de n’importe quelle classe qui prend en charge les fonctionnalités requises.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrait une chaîne d’un `DBID` et la copie dans le *BSTR* passé.|
|[SetCommandText](#setcommandtext)|Valide et stocke le `DBID`s dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Méthodes substituables

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Récupère les informations de colonne pour une demande de client particulière.|
|[GetCommandFromID](#getcommandfromid)|Vérifie si l’un des paramètres ou les deux contiennent des valeurs de chaîne et, si tel est le cas, copie les valeurs de chaîne dans les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Vérifie si l’un ou les deux `DBID`s contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Par défaut, une `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement de l’utilisateur pour `CRowsetImpl`. Vous pouvez utiliser une autre classe de type tableau en remplaçant l’argument de modèle `ArrayType` par `CRowsetImpl`.|
|[m_strCommandText](#strcommandtext)|Contient la commande initiale de l’ensemble de lignes.|
|[m_strIndexText](#strindextext)|Contient l’index initial de l’ensemble de lignes.|

## <a name="remarks"></a>Notes

`CRowsetImpl` fournit des remplacements sous la forme de conversions statiques. Les méthodes contrôlent la façon dont un ensemble de lignes donné validera le texte de la commande. Vous pouvez créer votre propre classe de style `CRowsetImpl`en rendant les interfaces d’implémentation multiples héritées. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute`. Selon le type d’ensemble de lignes que vous créez, les méthodes Creator s’attendent à des signatures différentes pour `Execute`. Par exemple, si vous utilisez une classe dérivée de `CRowsetImpl`pour implémenter un ensemble de lignes de schéma, la méthode `Execute` aura la signature suivante :

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Si vous créez une classe dérivée de `CRowsetImpl`pour implémenter l’ensemble de lignes d’une commande ou d’une session, la méthode `Execute` aura la signature suivante :

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Pour implémenter l’une des méthodes de `Execute` dérivées de `CRowsetImpl`, vous devez remplir vos mémoires tampons de données internes ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl :: NameFromDBID

Extrait une chaîne d’un `DBID` et la copie dans le *BSTR* passé.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Paramètres

*pDBID*<br/>
dans Pointeur vers le `DBID` à partir duquel extraire une chaîne.

*BSTR*<br/>
dans Une référence [CComBSTR](../../atl/reference/ccombstr-class.md) pour placer une copie de la chaîne de `DBID`.

*bIndex*<br/>
dans **true** si un index `DBID`; **false** si une table `DBID`.

### <a name="return-value"></a>Valeur de retour

HRESULT standard. Selon que la `DBID` est une table ou un index (indiqué par *bIndex*), la méthode retourne DB_E_NOINDEX ou DB_E_NOTABLE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par les implémentations `CRowsetImpl` de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl :: SetCommandText

Valide et stocke le `DBID`s dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Paramètres

*pTableID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

La méthode `SetCommentText` est appelée par `CreateRowset`, méthode statique de `IOpenRowsetImpl`.

Cette méthode délègue son travail en appelant [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) via un pointeur converti.

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl :: GetColumnInfo

Récupère les informations de colonne pour une demande de client particulière.

### <a name="syntax"></a>Syntaxe

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Paramètres

*va*<br/>
dans Pointeur vers la classe dérivée `CRowsetImpl` de l’utilisateur.

*pcCols*<br/>
dans Pointeur (sortie) vers le nombre de colonnes retournées.

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure `ATLCOLUMNINFO` statique.

### <a name="remarks"></a>Notes

Cette méthode est une substitution avancée.

Cette méthode est appelée par plusieurs classes d’implémentation de base pour récupérer les informations de colonne pour une demande de client particulière. En règle générale, cette méthode est appelée par `IColumnsInfoImpl`. Si vous substituez cette méthode, vous devez placer une version de la méthode dans votre classe dérivée de `CRowsetImpl`. Étant donné que la méthode peut être placée dans une classe non mise en forme, vous devez remplacer *PV* par la classe appropriée dérivée de `CRowsetImpl`.

L’exemple suivant illustre l’utilisation de `GetColumnInfo`. Dans cet exemple, `CMyRowset` est une classe dérivée de `CRowsetImpl`. Pour substituer `GetColumnInfo` pour toutes les instances de cette classe, placez la méthode suivante dans la définition de la classe `CMyRowset` :

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl :: GetCommandFromID

Vérifie si l’un des paramètres ou les deux contiennent des valeurs de chaîne et, si tel est le cas, copie les valeurs de chaîne dans les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Paramètres

*pTableID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie si un ou les deux paramètres contiennent des valeurs de chaîne. Si elles contiennent des valeurs de chaîne, cette méthode copie les valeurs de chaîne dans les membres de données. En plaçant une méthode avec cette signature dans votre classe dérivée de `CRowsetImpl`, votre méthode sera appelée à la place de l’implémentation de base.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl :: ValidateCommandID

Vérifie si l’un ou les deux `DBID`s contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Paramètres

*pTableID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers l' `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie si l’un ou les deux `DBID`s contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données. En plaçant une méthode avec cette signature dans votre classe dérivée de `CRowsetImpl`, votre méthode sera appelée à la place de l’implémentation de base.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl :: m_rgRowData

Par défaut, une `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement de l’utilisateur pour `CRowsetImpl`.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Notes

*ArrayType* est un paramètre de modèle pour `CRowsetImpl`.

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>CRowsetImpl :: m_strCommandText

Contient la commande initiale de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>CRowsetImpl :: m_strIndexText

Contient l’index initial de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```