---
title: IErrorRecordsImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 149508ee799ab2802dd2a106b503376851ac31cd
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573352"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl, classe
Implémente la norme OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) interface, ajout d’enregistrements à et récupérer des enregistrements d’un membre de données ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) de type **CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Une classe dérivée de `IErrorRecordsImpl`.  
  
 *RecordClass*  
 Une classe qui représente un objet d’erreur OLE DB.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetErrorDescriptionString](#geterrordescriptionstring)|Obtient la chaîne de description d’erreur à partir d’un enregistrement d’erreur.|  
|[GetErrorGUID](#geterrorguid)|Obtient le GUID de l’erreur à partir d’un enregistrement d’erreur.|  
|[GetErrorHelpContext](#geterrorhelpcontext)|Obtient l’ID de contexte d’aide à partir d’un enregistrement d’erreur.|  
|[GetErrorHelpFile](#geterrorhelpfile)|Obtient le chemin d’accès complet du fichier d’aide à partir d’un enregistrement d’erreur.|  
|[GetErrorSource](#geterrorsource)|Obtient le code source d’erreur à partir d’un enregistrement d’erreur.|  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[AddErrorRecord](#adderrorrecord)|Ajoute un enregistrement à l’objet d’erreur OLE DB.|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|Retourne des informations de base sur l’erreur, telles que le code de retour et le numéro d’erreur spécifique au fournisseur.|  
|[GetCustomErrorObject](#getcustomerrorobject)|Retourne un pointeur vers une interface sur un objet d’erreur personnalisé.|  
|[GetErrorInfo](#geterrorinfo)|Retourne un [IErrorInfo](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) pointeur d’interface sur l’enregistrement spécifié.|  
|[GetErrorParameters](#geterrorparameters)|Retourne les paramètres de l’erreur.|  
|[GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans l’objet d’enregistrement OLE DB.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_rgErrors](#rgerrors)|Tableau d’enregistrements d’erreur.|  

## <a name="geterrordescriptionstring"></a> IErrorRecordsImpl::GetErrorDescriptionString
Obtient la chaîne de description d’erreur à partir d’un enregistrement d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rCurError*  
 Un `ERRORINFO` enregistrements dans une `IErrorInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une chaîne décrivant l’erreur.  
  
## <a name="geterrorguid"></a> IErrorRecordsImpl::GetErrorGUID
Obtient le GUID de l’erreur à partir d’un enregistrement d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rCurError*  
 Un `ERRORINFO` enregistrements dans une `IErrorInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à un GUID pour l’erreur.  

## <a name="geterrorhelpcontext"></a> IErrorRecordsImpl::GetErrorHelpContext
Obtient l’ID de contexte d’aide à partir d’un enregistrement d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rCurError*  
 Un `ERRORINFO` enregistrements dans une `IErrorInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de contexte d’aide pour l’erreur.  

## <a name="geterrorhelpfile"></a> IErrorRecordsImpl::GetErrorHelpFile
Obtient le nom de chemin d’accès du fichier d’aide à partir d’un enregistrement d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rCurError*  
 Un `ERRORINFO` enregistrements dans une `IErrorInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une chaîne qui contient le nom de chemin d’accès du fichier d’aide pour l’erreur.

## <a name="geterrorsource"></a> IErrorRecordsImpl::GetErrorSource
Obtient le code source qui a provoqué l’erreur à partir d’un enregistrement d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rCurError*  
 Un `ERRORINFO` enregistrements dans une `IErrorInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une chaîne contenant le code source de l’erreur. 

## <a name="adderrorrecord"></a> IErrorRecordsImpl::AddErrorRecord
Ajoute un enregistrement à l’objet d’erreur OLE DB.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,  
   DWORD dwLookupID,  
   DISPPARAMS *pdispparams,  
   IUnknown *punkCustomError,  
   DWORD dwDynamicErrorID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::AddErrorRecord](/previous-versions/windows/desktop/ms725362\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="getbasicerrorinfo"></a> IErrorRecordsImpl::GetBasicErrorInfo
Retourne des informations de base sur l’erreur, telles que le code de retour et le numéro d’erreur spécifique au fournisseur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,  
   ERRORINFO *pErrorInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907\(v=vs.85\)) dans le *de référence du programmeur OLE DB*. 

## <a name="getcustomerrorobject"></a> IErrorRecordsImpl::GetCustomErrorObject
Retourne un pointeur vers une interface sur un objet d’erreur personnalisé.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,  
   REFIID riid,  
   IUnknown **ppObject);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="geterrorinfo"></a> IErrorRecordsImpl::GetErrorInfo
Retourne un [IErrorInfo](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) pointeur d’interface sur l’enregistrement spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,  
   LCID lcid,  
   IErrorInfo **ppErrorInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.

## <a name="geterrorparameters"></a> IErrorRecordsImpl::GetErrorParameters
Retourne les paramètres de l’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,  
   DISPPARAMS *pdispparams);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="getrecordcount"></a> IErrorRecordsImpl::GetRecordCount
Retourne le nombre d’enregistrements dans l’objet d’enregistrement OLE DB.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetRecordCount](/previous-versions/windows/desktop/ms722724\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  

## <a name="rgerrors"></a> IErrorRecordsImpl::m_rgErrors
Tableau d’enregistrements d’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CAtlArray< RecordClass > m_rgErrors;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)