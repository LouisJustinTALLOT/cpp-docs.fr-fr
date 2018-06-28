---
title: Classe de COleDispatchException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65e7c613f5c4a4273208e30cd0fc6284ef4e420c
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037868"
---
# <a name="coledispatchexception-class"></a>Classe de COleDispatchException
Gère les exceptions propres à l'interface `IDispatch` OLE, qui est une partie fondamentale d'OLE automation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Contexte d’aide pour l’erreur.|  
|[COleDispatchException::m_strDescription](#m_strdescription)|Description d’erreur.|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Aide du fichier à utiliser avec `m_dwHelpContext`.|  
|[COleDispatchException::m_strSource](#m_strsource)|Application qui a généré l’exception.|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-code d’erreur spécifique.|  
  
## <a name="remarks"></a>Notes  
 Comme les autres classes d’exceptions dérivées de la `CException` classe de base, `COleDispatchException` peut être utilisé avec les macros THROW THROW_LAST, TRY, CATCH, AND_CATCH et END_CATCH.  
  
 En règle générale, vous devez appeler [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) pour créer et lever une `COleDispatchException` objet.  
  
 Pour plus d’informations sur les exceptions, consultez les articles [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions : Exceptions OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext  
 Identifie un contexte d’aide dans l’aide de votre application (. Fichier de (HLP).  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>Notes  
 Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est levée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription  
 Contient une description d’erreur, tels que « Disque plein ».  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>Notes  
 Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est levée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile  
 L’infrastructure complète de cette chaîne avec le nom du fichier d’aide de l’application.  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>  COleDispatchException::m_strSource  
 L’infrastructure complète de cette chaîne avec le nom de l’application qui a généré l’exception.  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_wcode"></a>  COleDispatchException::m_wCode  
 Contient un code d’erreur spécifique à votre application.  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>Notes  
 Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CALCDRIV](../../visual-cpp-samples.md)   
 [CException (classe)](../../mfc/reference/cexception-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException, classe](../../mfc/reference/coleexception-class.md)
