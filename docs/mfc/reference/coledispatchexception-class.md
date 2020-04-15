---
title: COleDispatchException, classe
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375063"
---
# <a name="coledispatchexception-class"></a>COleDispatchException, classe

Gère les exceptions propres à l'interface `IDispatch` OLE, qui est une partie fondamentale d'OLE automation.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchException : public CException
```

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Aide contexte d’erreur.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Description d’erreur verbale.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Fichier d’aide `m_dwHelpContext`à utiliser avec .|
|[COleDispatchException::m_strSource](#m_strsource)|Application qui a généré l’exception.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-code d’erreur spécifique.|

## <a name="remarks"></a>Notes

Comme les autres classes `CException` d’exception `COleDispatchException` dérivées de la classe de base, peuvent être utilisés avec les macros THROW, THROW_LAST, TRY, CATCH, AND_CATCH et END_CATCH.

En général, vous devez appeler [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) pour créer et lancer un `COleDispatchException` objet.

Pour plus d’informations sur les exceptions, voir les articles [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext

Identifie un contexte d’aide dans l’aide de votre application (. HLP) fichier.

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Notes

Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est lancée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatchException::m_strDescription

Contient une description d’erreur verbale, comme "Disk full.".

```
CString m_strDescription;
```

### <a name="remarks"></a>Notes

Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est lancée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

Le cadre remplit cette chaîne avec le nom du fichier d’aide de l’application.

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatchException::m_strSource

Le cadre remplit cette chaîne avec le nom de l’application qui a généré l’exception.

```
CString m_strSource;
```

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatchException::m_wCode

Contient un code d’erreur spécifique à votre application.

```
WORD m_wCode;
```

### <a name="remarks"></a>Notes

Ce membre est défini par la fonction [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) lorsqu’une exception est lancée.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)<br/>
[Classe COleException](../../mfc/reference/coleexception-class.md)
