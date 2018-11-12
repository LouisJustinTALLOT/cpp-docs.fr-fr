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
ms.openlocfilehash: e89293d7b7803cf661bce7a91ea6df72b9a06122
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531571"
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
|[CInternetException::m_dwContext](#m_dwcontext)|La valeur de contexte associée à l’opération qui a provoqué l’exception.|
|[CInternetException::m_dwError](#m_dwerror)|L’erreur qui a provoqué l’exception.|

## <a name="remarks"></a>Notes

Le `CInternetException` classe inclut deux données membres publiques : un conserve le code d’erreur associé à l’exception, et l’autre contient l’identificateur de contexte de l’application Internet associée à l’erreur.

Pour plus d’informations sur les identificateurs de contexte pour les applications Internet, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxinet.h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Cette fonction membre est appelée quand un `CInternetException` objet est créé.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Paramètres

*dwError*<br/>
L’erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

Pour lever une CInternetException, appelez la fonction globale MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

La valeur de contexte associée à l’opération Internet connexe.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Notes

L’identificateur de contexte est spécifiée à l’origine dans [CInternetSession](../../mfc/reference/cinternetsession-class.md) et passées par MFC pour [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- et [CInternetFile](../../mfc/reference/cinternetfile-class.md)-classes dérivées. Vous pouvez remplacer cette valeur par défaut et affecter l’un *dwContext* paramètre une valeur de votre choix. *dwContext* est associé à une opération de l’objet donné. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

L’erreur qui a provoqué l’exception.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Notes

Cette valeur d’erreur peut être un système de code d’erreur, trouvé dans WINERROR. H, ou une valeur d’erreur de WININET. H.

Pour obtenir la liste des codes d’erreur Win32, consultez [Codes d’erreur](/windows/desktop/Debug/system-error-codes). Pour obtenir la liste des messages d’erreur spécifiques à Internet, consultez. Les deux rubriques sont dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException, classe](../../mfc/reference/cexception-class.md)
