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
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372406"
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
|[CInternetException::m_dwContext](#m_dwcontext)|La valeur contextuelle associée à l’opération qui a causé l’exception.|
|[CInternetException::m_dwError](#m_dwerror)|Erreur ayant provoqué l'exception.|

## <a name="remarks"></a>Notes

La `CInternetException` classe comprend deux membres de données publiques : l’un contient le code d’erreur associé à l’exception, et l’autre détient l’identifiant contextuelle de l’application Internet associée à l’erreur.

Pour plus d’informations sur les identifiants de contexte pour les applications Internet, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException

Cette fonction de membre `CInternetException` est appelée lorsqu’un objet est créé.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Paramètres

*dwError*<br/>
Erreur ayant provoqué l'exception.

### <a name="remarks"></a>Notes

Pour lancer un CInternetException, appelez la fonction mondiale MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext

La valeur contextuelle associée à l’opération Internet connexe.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Notes

L’identifiant de contexte est à l’origine spécifié dans [CInternetSession](../../mfc/reference/cinternetsession-class.md) et transmis par MFC à [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- et [CInternetFile](../../mfc/reference/cinternetfile-class.md)-classes dérivées. Vous pouvez remplacer cette valeur par défaut et attribuer à n’importe quel paramètre *dwContext* une valeur de votre choix. *dwContext* est associé à n’importe quelle opération de l’objet donné. *dwContext* identifie les informations sur l’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError

Erreur ayant provoqué l'exception.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Notes

Cette valeur d’erreur peut être un code d’erreur système, trouvé dans WINERROR. H, ou une valeur d’erreur de WININET. H.

Pour une liste des codes d’erreur Win32, voir [codes d’erreur](/windows/win32/Debug/system-error-codes). Pour une liste de messages d’erreur spécifiques à Internet, voir . Les deux sujets sont dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)
