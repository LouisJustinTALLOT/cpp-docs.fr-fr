---
title: CDBErrorInfo::GetAllErrorInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 590215ddc5c62e5c717aebe196bc33ce7d514e7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091905"
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
Retourne tous les types d’informations sur les erreurs contenues dans un enregistrement d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```
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
  
 `lcid`  
 [in] L’ID de paramètres régionaux pour les informations d’erreur à retourner.  
  
 `pbstrDescription`  
 [out] Pointeur vers une description de l’erreur ou la valeur NULL si les paramètres régionaux ne sont pas pris en charge. Consultez la section Notes.  
  
 `pbstrSource`  
 [out] Un pointeur vers une chaîne contenant le nom du composant qui a généré l’erreur.  
  
 `pguid`  
 [out] Pointeur vers le GUID de l’interface ayant défini l’erreur.  
  
 *pdwHelpContext*  
 [out] Pointeur vers l’ID de contexte d’aide pour l’erreur.  
  
 *pbstrHelpFile*  
 [out] Un pointeur vers une chaîne contenant le chemin d’accès au fichier d’aide qui décrit l’erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si l'opération a réussi. Consultez [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) dans les *de référence du programmeur OLE DB* pour d’autres valeurs de retournés.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="remarks"></a>Notes  
 La valeur de sortie `pbstrDescription` est obtenu en interne en appelant IErrorInfo::GetDescription, qui définit la valeur null si les paramètres régionaux ne sont pas pris en charge, ou si les deux conditions suivantes sont remplies :  
  
1.  la valeur de `lcid` n’est pas des États-Unis Anglais et  
  
2.  la valeur de `lcid` est différent de la valeur retournée par GetUserDefaultLCID.  
  
## <a name="see-also"></a>Voir aussi  
 [CDBErrorInfo, classe](../../data/oledb/cdberrorinfo-class.md)