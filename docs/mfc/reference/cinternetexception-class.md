---
title: CInternetException, classe
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505908"
---
# <a name="cinternetexception-class"></a>CInternetException, classe

Représente une condition d'exception liée à une opération Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Construit un objet `CInternetException`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Valeur de contexte associée à l’opération qui a provoqué l’exception.|
|[CInternetException::m_dwError](#m_dwerror)|Erreur qui a provoqué l’exception.|

## <a name="remarks"></a>Notes

La `CInternetException` classe inclut deux membres de données publics: l’un contient le code d’erreur associé à l’exception, tandis que l’autre contient l’identificateur de contexte de l’application Internet associée à l’erreur.

Pour plus d’informations sur les identificateurs de contexte pour les applications Internet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Configuration requise

**En-tête:** AFXINET. h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Cette fonction membre est appelée lorsqu’un `CInternetException` objet est créé.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Paramètres

*dwError*<br/>
Erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

Pour lever un CInternetException, appelez la fonction globale MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

Valeur de contexte associée à l’opération Internet associée.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Notes

L’identificateur de contexte est spécifié à l’origine dans [CInternetSession](../../mfc/reference/cinternetsession-class.md) et passé par MFC aux classes dérivées de [CInternetConnection,](../../mfc/reference/cinternetconnection-class.md)et [CInternetFile](../../mfc/reference/cinternetfile-class.md). Vous pouvez remplacer cette valeur par défaut et affecter à n’importe quel paramètre *dwContext* la valeur de votre choix. *dwContext* est associé à toute opération de l’objet donné. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

Erreur qui a provoqué l’exception.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Notes

Cette valeur d’erreur est peut-être un code d’erreur système, trouvé dans WINERROR. H, ou une valeur d’erreur de WININET. Manutention.

Pour obtenir la liste des codes d’erreur Win32, consultez [codes d’erreur](/windows/win32/Debug/system-error-codes). Pour obtenir la liste des messages d’erreur spécifiques à Internet, consultez. Les deux rubriques se trouvent dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException, classe](../../mfc/reference/cexception-class.md)
