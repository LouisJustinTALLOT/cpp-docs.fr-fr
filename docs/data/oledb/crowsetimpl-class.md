---
title: CRowsetImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1583a5cb6ff67943bde8af530593dff94986d551
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340473"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl, classe
Fournit une implémentation d’ensemble de lignes OLE DB standard sans nécessiter l’héritage multiple de nombreuses interfaces d’implémentation.  
  
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
 *T*  
 Classe de l’utilisateur qui dérive de `CRowsetImpl`.  
  
 *Stockage*  
 La classe d’enregistrement utilisateur.  
  
 *CreatorClass*  
 La classe qui contient les propriétés de l’ensemble de lignes ; en général, la commande.  
  
 *ArrayType*  
 La classe qui agira en tant que stockage pour les données de l’ensemble de lignes. Ce paramètre par défaut est `CAtlArray`, mais il peut être toute classe qui prend en charge la fonctionnalité requise.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[NameFromDBID](#namefromdbid)|Extrait une chaîne à partir d’un `DBID` et le copie dans le *bstr* passé dans.|  
|[SetCommandText](#setcommandtext)|Valide et stocke le `DBID`s dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Méthodes substituables  
  
|||  
|-|-|  
|[GetColumnInfo](#getcolumninfo)|Récupère les informations de colonne pour une demande client particulier.|  
|[GetCommandFromID](#getcommandfromid)|Vérifie si un ou les deux paramètres contiennent des valeurs de chaîne et le cas échéant, copie les valeurs de chaîne pour les membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID](#validatecommandid)|Vérifie pour voir si un ou les deux `DBID`s contiennent des valeurs de chaîne et si tel est le cas, les copie dans ses données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_rgRowData](#rgrowdata)|Par défaut, un `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement utilisateur `CRowsetImpl`. Une autre classe de type de tableau peut être utilisée en modifiant le `ArrayType` argument template `CRowsetImpl`.|  
|[m_strCommandText](#strcommandtext)|Contient la commande initiale de l’ensemble de lignes.|  
|[m_strIndexText](#strindextext)|Contient l’index initial de l’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 `CRowsetImpl` Fournit des remplacements dans le formulaire d’effectue un upcast statique. Les méthodes de contrôlent la façon dans lequel un ensemble de lignes donné validera le texte de la commande. Vous pouvez créer vos propres `CRowsetImpl`-classe de style en effectuant vos interfaces de l’implémentation héritée de plusieurs. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute`. Selon le type d’ensemble de lignes que vous créez, les méthodes de créateur seront attend à recevoir des signatures différentes pour `Execute`. Par exemple, si vous utilisez un `CRowsetImpl`-dérivée de classe pour implémenter un ensemble de lignes de schéma, le `Execute` méthode possède la signature suivante :  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Si vous créez un `CRowsetImpl`-dérivée de classe pour implémenter une commande ou l’ensemble de lignes de la session, le `Execute` méthode possède la signature suivante :  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 Pour mettre en œuvre toutes les `CRowsetImpl`-dérivée `Execute` méthodes, vous devez remplir vos tampons de données interne ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID
Extrait une chaîne à partir d’un `DBID` et le copie dans le *bstr* passé dans.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pDBID*  
 [in] Un pointeur vers le `DBID` à partir duquel extraire une chaîne.  
  
 *BSTR*  
 [in] Un [CComBSTR](../../atl/reference/ccombstr-class.md) référence pour placer une copie de la `DBID` chaîne.  
  
 *bIndex*  
 [in] **true** si un index `DBID`; **false** si une table `DBID`.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard. Selon que le `DBID` est une table ou un index (indiqué par *bIndex*), la méthode retourne soit DB_E_NOINDEX ou DB_E_NOTABLE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par le `CRowsetImpl` implémentations de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md). 
  
## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText
Valide et stocke le `DBID`s dans les deux chaînes ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pTableID*  
 [in] Un pointeur vers le `DBID` représentant l’ID de table.  
  
 *pIndexID*  
 [in] Un pointeur vers le `DBID` représentant l’ID d’index.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Le `SetCommentText` méthode est appelée par `CreateRowset`, statique transformer en modèle de méthode de `IOpenRowsetImpl`.  
  
 Cette méthode délègue son travail en appelant [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) via un pointeur converti en supertype. 

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo
Récupère les informations de colonne pour une demande client particulier.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *PV*  
 [in] Un pointeur vers l’utilisateur `CRowsetImpl` classe dérivée.  
  
 *pcCols*  
 [in] Un pointeur (sortie) au nombre de colonnes retournées.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un statique `ATLCOLUMNINFO` structure.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est un remplacement avancé.  
  
 Cette méthode est appelée par plusieurs classes d’implémentation de base pour récupérer des informations de colonne pour une demande client particulier. En règle générale, cette méthode appelée `IColumnsInfoImpl`. Si vous substituez cette méthode, vous devez placer une version de la méthode dans votre `CRowsetImpl`-classe dérivée. Étant donné que la méthode peut être placée dans une classe non transformer en modèle, vous devez modifier *pv* appropriés `CRowsetImpl`-classe dérivée.  
  
 L’exemple suivant montre `GetColumnInfo` utilisation. Dans cet exemple, `CMyRowset` est un `CRowsetImpl`-classe dérivée. Pour substituer le `GetColumnInfo` pour toutes les instances de cette classe, placez la méthode suivante dans le `CMyRowset` définition de classe :  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID
Vérifie si un ou les deux paramètres contiennent des valeurs de chaîne et le cas échéant, copie les valeurs de chaîne pour les membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pTableID*  
 [in] Un pointeur vers le `DBID` représentant l’ID de Table.  
  
 *pIndexID*  
 [in] Un pointeur vers le `DBID` représentant l’ID d’Index.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir les membres de données [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie si un ou les deux paramètres contiennent des valeurs de chaîne. S’ils contiennent des valeurs de chaîne, cette méthode copie les valeurs de chaîne pour les membres de données. En plaçant une méthode avec cette signature dans votre `CRowsetImpl`-classe dérivée, votre méthode est appelée au lieu de l’implémentation de base. 

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID
Vérifie pour voir si un ou les deux `DBID`s contiennent des valeurs de chaîne et si tel est le cas, les copie dans ses données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pTableID*  
 [in] Un pointeur vers le `DBID` représentant l’ID de table.  
  
 *pIndexID*  
 [in] Un pointeur vers le `DBID` représentant l’ID d’index.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée via un upcast statique par `CRowsetImpl` pour remplir ses données membres [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) et [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Par défaut, cette méthode vérifie pour voir si un ou les deux `DBID`s contiennent des valeurs de chaîne et si tel est le cas, les copie dans ses données membres. En plaçant une méthode avec cette signature dans votre `CRowsetImpl`-classe dérivée, votre méthode est appelée au lieu de l’implémentation de base.  

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData
Par défaut, un `CAtlArray` qui templatizes sur l’argument de modèle d’enregistrement utilisateur `CRowsetImpl`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;  
```  
  
### <a name="remarks"></a>Notes  
 *ArrayType* est un paramètre de modèle à `CRowsetImpl`.  

## <a name="strcommandtext"></a> CRowsetImpl::m_strCommandText
Contient la commande initiale de l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;  
```  

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText
Contient l’index initial de l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;  
``` 