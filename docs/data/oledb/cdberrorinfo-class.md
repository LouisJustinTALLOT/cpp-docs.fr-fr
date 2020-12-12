---
description: 'En savoir plus sur : classe CDBErrorInfo'
title: CDBErrorInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: fe57963e5964403c6b17b6b41dc7ae5f77063f50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170852"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo, classe

Prend en charge OLE DB le traitement des erreurs à l’aide de l’interface OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Retourne toutes les informations sur les erreurs contenues dans un enregistrement d’erreur.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Appelle [IErrorRecords :: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) pour retourner des informations de base sur l’erreur spécifiée.|
|[GetCustomErrorObject](#getcustomerrorobject)|Appelle [IErrorRecords :: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) pour retourner un pointeur vers une interface sur un objet d’erreur personnalisé.|
|[GetErrorInfo](#geterrorinfo)|Appelle [IErrorRecords :: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) pour retourner un `IErrorInfo` pointeur d’interface vers l’enregistrement spécifié.|
|[GetErrorParameters](#geterrorparameters)|Appelle [IErrorRecords :: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) pour retourner les paramètres d’erreur.|
|[GetErrorRecords](#geterrorrecords)|Obtient les enregistrements d’erreur pour l’objet spécifié.|

## <a name="remarks"></a>Notes

Cette interface retourne un ou plusieurs enregistrements d’erreur à l’utilisateur. Appelez [CDBErrorInfo :: GetErrorRecords](#geterrorrecords) en premier, pour obtenir le nombre d’enregistrements d’erreur. Appelez ensuite l’une des fonctions d’accès, telles que [CDBErrorInfo :: GetAllErrorInfo](#getallerrorinfo), pour récupérer les informations d’erreur pour chaque enregistrement.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a> CDBErrorInfo :: GetAllErrorInfo

Retourne tous les types d’informations d’erreur contenus dans un enregistrement d’erreur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>Paramètres

*ulRecordNum*<br/>
dans Numéro de base zéro de l’enregistrement pour lequel retourner les informations d’erreur.

*lcid*<br/>
dans ID de paramètres régionaux pour les informations d’erreur à retourner.

*pbstrDescription*<br/>
à Pointeur vers une description textuelle de l’erreur ou NULL si les paramètres régionaux ne sont pas pris en charge. Consultez la section Notes.

*pbstrSource*<br/>
à Pointeur vers une chaîne contenant le nom du composant qui a généré l’erreur.

*pguid*<br/>
à Pointeur vers le GUID de l’interface qui a défini l’erreur.

*pdwHelpContext*<br/>
à Pointeur vers l’ID de contexte d’aide pour l’erreur.

*pbstrHelpFile*<br/>
à Pointeur vers une chaîne contenant le chemin d’accès au fichier d’aide qui décrit l’erreur.

### <a name="return-value"></a>Valeur renvoyée

S_OK, en cas de réussite. Consultez [IErrorRecords :: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* pour les autres valeurs de retour.

### <a name="remarks"></a>Notes

La valeur de sortie de *pbstrDescription* est obtenue en interne en appelant `IErrorInfo::GetDescription` , qui définit la valeur sur null si les paramètres régionaux ne sont pas pris en charge, ou si les deux conditions suivantes sont vraies :

1. la valeur du *LCID* n’est pas l’anglais des États-Unis et

1. la valeur de *LCID* n’est pas égale à la valeur retournée par GetUserDefaultLCID.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> CDBErrorInfo :: GetBasicErrorInfo

Appelle [IErrorRecords :: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) pour retourner des informations de base sur l’erreur, telles que le code de retour et le numéro d’erreur spécifique au fournisseur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IErrorRecords :: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a> CDBErrorInfo :: GetCustomErrorObject

Appelle [IErrorRecords :: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) pour retourner un pointeur vers une interface sur un objet d’erreur personnalisé.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IErrorRecords :: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a> CDBErrorInfo :: GetErrorInfo

Appelle [IErrorRecords :: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) pour retourner un pointeur d’interface [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) à l’enregistrement spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IErrorRecords :: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a> CDBErrorInfo :: GetErrorParameters

Appelle [IErrorRecords :: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) pour retourner les paramètres d’erreur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IErrorRecords :: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a> CDBErrorInfo :: GetErrorRecords

Obtient les enregistrements d’erreur pour l’objet spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Interface de l’objet pour lequel obtenir les enregistrements d’erreur.

*vaut*<br/>
dans IID de l’interface associée à l’erreur.

*pcRecords*<br/>
à Pointeur vers le nombre d’enregistrements d’erreur (base un).

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Utilisez la première forme de la fonction si vous souhaitez vérifier l’interface à partir de laquelle obtenir les informations d’erreur. Dans le cas contraire, utilisez le deuxième formulaire.

## <a name="see-also"></a>Voir aussi

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
