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
ms.openlocfilehash: 35a80503597b7e59ec10618b9c8e18e0e69f018e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221508"
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
Classe de l’utilisateur qui dérive de `CRowsetImpl` .

*Stockage*<br/>
Classe d’enregistrement utilisateur.

*CreatorClass*<br/>
La classe qui contient les propriétés de l’ensemble de lignes ; en général, la commande.

*ArrayType*<br/>
Classe qui servira de stockage pour les données de l’ensemble de lignes. Par défaut, ce paramètre `CAtlArray` a la valeur, mais il peut s’agir de n’importe quelle classe qui prend en charge les fonctionnalités requises.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrait une chaîne d’un `DBID` et la copie dans le *BSTR* passé.|
|[SetCommandText](#setcommandtext)|Valide et stocke les `DBID` dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Méthodes substituables

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Récupère les informations de colonne pour une demande de client particulière.|
|[GetCommandFromID](#getcommandfromid)|Vérifie si l’un des paramètres ou les deux contiennent des valeurs de chaîne et, si tel est le cas, copie les valeurs de chaîne dans les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Vérifie si l’un des deux ou les deux `DBID` contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Par défaut, `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement de l’utilisateur `CRowsetImpl` . Vous pouvez utiliser une autre classe de type tableau en remplaçant l' `ArrayType` argument de modèle par `CRowsetImpl` .|
|[m_strCommandText](#strcommandtext)|Contient la commande initiale de l’ensemble de lignes.|
|[m_strIndexText](#strindextext)|Contient l’index initial de l’ensemble de lignes.|

## <a name="remarks"></a>Notes

`CRowsetImpl`fournit des substitutions sous la forme de conversions statiques. Les méthodes contrôlent la façon dont un ensemble de lignes donné validera le texte de la commande. Vous pouvez créer votre propre `CRowsetImpl` classe de style en rendant les interfaces d’implémentation multiples héritées. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute` . Selon le type d’ensemble de lignes que vous créez, les méthodes Creator s’attendent à des signatures différentes pour `Execute` . Par exemple, si vous utilisez une `CRowsetImpl` classe dérivée de pour implémenter un ensemble de lignes de schéma, la `Execute` méthode aura la signature suivante :

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Si vous créez une `CRowsetImpl` classe dérivée de pour implémenter un ensemble de lignes de commande ou de session, la `Execute` méthode aura la signature suivante :

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Pour implémenter l’une des `CRowsetImpl` méthodes dérivées de `Execute` , vous devez remplir vos mémoires tampons de données internes ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

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
dans Pointeur vers à `DBID` partir duquel extraire une chaîne.

*BSTR*<br/>
dans Une référence [CComBSTR](../../atl/reference/ccombstr-class.md) pour placer une copie de la `DBID` chaîne.

*bIndex*<br/>
[in] **`true`** Si un index `DBID` ; dans **`false`** le cas d’une table `DBID` .

### <a name="return-value"></a>Valeur de retour

HRESULT standard. Selon que le `DBID` est une table ou un index (indiqué par *bIndex*), la méthode retourne DB_E_NOINDEX ou DB_E_NOTABLE.

### <a name="remarks"></a>Notes

Cette méthode est appelée par les `CRowsetImpl` implémentations de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl :: SetCommandText

Valide et stocke les `DBID` dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Paramètres

*pTableID*<br/>
dans Pointeur vers le `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers le `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

La `SetCommentText` méthode est appelée par `CreateRowset` , une méthode modélisée de `IOpenRowsetImpl` .

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
dans Pointeur vers la `CRowsetImpl` classe dérivée de l’utilisateur.

*pcCols*<br/>
dans Pointeur (sortie) vers le nombre de colonnes retournées.

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure statique `ATLCOLUMNINFO` .

### <a name="remarks"></a>Notes

Cette méthode est une substitution avancée.

Cette méthode est appelée par plusieurs classes d’implémentation de base pour récupérer les informations de colonne pour une demande de client particulière. En général, cette méthode est appelée par `IColumnsInfoImpl` . Si vous substituez cette méthode, vous devez placer une version de la méthode dans votre `CRowsetImpl` classe dérivée de. Étant donné que la méthode peut être placée dans une classe non mise en forme, vous devez remplacer *PV* par la `CRowsetImpl` classe dérivée appropriée.

L’exemple suivant illustre `GetColumnInfo` l’utilisation de. Dans cet exemple, `CMyRowset` est une `CRowsetImpl` classe dérivée de. Pour remplacer `GetColumnInfo` toutes les instances de cette classe, placez la méthode suivante dans la `CMyRowset` définition de classe :

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
dans Pointeur vers le `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers le `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir les données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie si un ou les deux paramètres contiennent des valeurs de chaîne. Si elles contiennent des valeurs de chaîne, cette méthode copie les valeurs de chaîne dans les membres de données. En plaçant une méthode avec cette signature dans votre `CRowsetImpl` classe dérivée de, votre méthode sera appelée à la place de l’implémentation de base.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl :: ValidateCommandID

Vérifie si l’un des deux ou les deux `DBID` contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Paramètres

*pTableID*<br/>
dans Pointeur vers le `DBID` représentant l’ID de table.

*pIndexID*<br/>
dans Pointeur vers le `DBID` représentant l’ID d’index.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir ses membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie si l’un des deux ou les deux `DBID` contiennent des valeurs de chaîne et, si tel est le cas, les copie dans ses membres de données. En plaçant une méthode avec cette signature dans votre `CRowsetImpl` classe dérivée de, votre méthode sera appelée à la place de l’implémentation de base.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl :: m_rgRowData

Par défaut, `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement de l’utilisateur `CRowsetImpl` .

### <a name="syntax"></a>Syntaxe

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Notes

*ArrayType* est un paramètre de modèle de `CRowsetImpl` .

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
