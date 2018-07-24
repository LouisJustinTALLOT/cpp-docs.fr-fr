---
title: Cdberrorinfo, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a219024c56bd1b976682c7262d84ce26bce0930
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208609"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo, classe
Fournit la prise en charge pour le traitement d’erreur OLE DB à l’aide de OLE DB [IErrorRecords](https://msdn.microsoft.com/library/ms718112.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDBErrorInfo  
``` 

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h 
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetAllErrorInfo](#getallerrorinfo)|Retourne toutes les informations d’erreur contenues dans un enregistrement d’erreur.|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|Appels [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) pour retourner des informations de base sur l’erreur spécifiée.|  
|[GetCustomErrorObject](#getcustomerrorobject)|Appels [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) pour retourner un pointeur vers une interface sur un objet d’erreur personnalisé.|  
|[GetErrorInfo](#geterrorinfo)|Appels [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) pour retourner un `IErrorInfo` pointeur d’interface vers l’enregistrement spécifié.|  
|[GetErrorParameters](#geterrorparameters)|Appels [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) pour retourner les paramètres de l’erreur.|  
|[GetErrorRecords](#geterrorrecords)|Obtient les enregistrements d’erreur pour l’objet spécifié.|  
  
## <a name="remarks"></a>Notes  
 Cette interface retourne un ou plusieurs enregistrements d’erreur à l’utilisateur. Appelez [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) tout d’abord, pour obtenir le nombre d’enregistrements d’erreur. Puis à appeler une de l’accès aux fonctions, telles que [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)pour récupérer les informations d’erreur pour chaque enregistrement.  
  
## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo
Retourne tous les types d’informations d’erreur contenues dans un enregistrement d’erreur.  
  
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
 *ulRecordNum*  
 [in] Numéro de base zéro de l’enregistrement pour lequel retourner les informations d’erreur.  
  
 *lcid*  
 [in] L’ID de paramètres régionaux pour les informations d’erreur à retourner.  
  
 *pbstrDescription*  
 [out] Pointeur vers une description de l’erreur ou la valeur NULL si les paramètres régionaux ne sont pas pris en charge. Consultez la section Notes.  
  
 *pbstrSource*  
 [out] Un pointeur vers une chaîne contenant le nom du composant qui a généré l’erreur.  
  
 *pguid*  
 [out] Un pointeur vers le GUID de l’interface ayant défini l’erreur.  
  
 *pdwHelpContext*  
 [out] Pointeur vers l’ID de contexte d’aide pour l’erreur.  
  
 *pbstrHelpFile*  
 [out] Un pointeur vers une chaîne contenant le chemin d’accès au fichier d’aide qui décrit l’erreur.  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite. Consultez [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) dans le *de référence du programmeur OLE DB* pour les autres valeurs de retour.  
  
### <a name="remarks"></a>Notes  
 La valeur de sortie *pbstrDescription* est obtenu en interne en appelant `IErrorInfo::GetDescription`, qui définit la valeur null si les paramètres régionaux ne sont pas pris en charge, ou si les deux conditions suivantes sont remplies :  
  
1.  la valeur de *lcid* n’est pas aux États-Unis Anglais et  
  
2.  la valeur de *lcid* est différent de la valeur retournée par GetUserDefaultLCID. 

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo
Appels [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) pour retourner des informations de base sur l’erreur, telles que le code de retour et le numéro d’erreur spécifique au fournisseur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,   
  ERRORINFO* pErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject
Appels [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) pour retourner un pointeur vers une interface sur un objet d’erreur personnalisé.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,   
   REFIID riid,IUnknown** ppObject) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo
Appels [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) pour retourner un [IErrorInfo](https://msdn.microsoft.com/library/ms718112.aspx) pointeur d’interface vers l’enregistrement spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,   
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters
Appels [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) pour retourner les paramètres de l’erreur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,   
  DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords
Obtient les enregistrements d’erreur pour l’objet spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  


HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Interface à l’objet pour lequel obtenir les enregistrements d’erreur.  
  
 *IID*  
 [in] IID de l’interface associée à l’erreur.  
  
 *pcRecords*  
 [out] Un pointeur vers le nombre (base 1) des enregistrements d’erreur.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Utiliser la première forme de la fonction si vous souhaitez vérifier quelle interface pour obtenir les informations d’erreur à partir de. Sinon, utilisez la deuxième forme.  
  
## <a name="see-also"></a>Voir aussi  
 [DBViewer](../../visual-cpp-samples.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)