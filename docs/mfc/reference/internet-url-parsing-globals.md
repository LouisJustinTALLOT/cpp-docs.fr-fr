---
title: Internet URL Parsing Globals and Helpers
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356620"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet URL Parsing Globals and Helpers

Lorsqu’un client envoie une requête au serveur Internet, vous pouvez utiliser l’un des globaux d’analyse d’URL pour extraire des informations sur le client. Les fonctions d’aide fournissent d’autres fonctionnalités Internet.

## <a name="internet-url-parsing-globals"></a>Objet Globals d'analyse des URL Internet

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Parse une chaîne d’URL et renvoie le type de service et ses composants.|
|[AfxParseURLEx](#afxparseurlex)|Parse une chaîne d’URL et renvoie le type de service et ses composants, ainsi que la fourniture du nom d’utilisateur et du mot de passe.|

## <a name="other-internet-helpers"></a>Autres aides Internet

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Jette une exception liée à la connexion Internet.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Détermine le type de poignée Internet.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

Ce global est utilisé dans [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Paramètres

*pstrURL (pstrURL)*<br/>
Un pointeur à une chaîne contenant l’URL à analyser.

*dwServiceType dwServiceType*<br/>
Indique le type de service Internet. Les valeurs possibles sont les suivantes :

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer (en)*<br/>
Le premier segment de l’URL suivant le type de service.

*strObject*<br/>
Un objet auquel l’URL fait référence (peut être vide).

*nPort (en)*<br/>
Déterminé à partir des parties serveur ou objet de l’URL, si l’un ou l’autre existe.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’URL a été analysée avec succès; autrement, 0 s’il est vide ou ne contient pas un type de service Internet connu.

### <a name="remarks"></a>Notes

Il analyse une chaîne d’URL et renvoie le type de service et ses composants.

Par exemple, `AfxParseURL` analyse les URL du formulaire *service://server/dir/dir/object.ext:port* et renvoie ses composants stockés comme suit :

*strServer* "serveur"

*strObject* "/dir/dir/object/object.ext"

*nPort* #port

*dwServiceType* #service

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. H.

### <a name="requirements"></a>Spécifications

  **En-tête** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx AfxParseURLEx

Cette fonction globale est la version étendue [d’AfxParseURL](#afxparseurl) et est utilisée dans [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*pstrURL (pstrURL)*<br/>
Un pointeur à une chaîne contenant l’URL à analyser.

*dwServiceType dwServiceType*<br/>
Indique le type de service Internet. Les valeurs possibles sont les suivantes :

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer (en)*<br/>
Le premier segment de l’URL suivant le type de service.

*strObject*<br/>
Un objet auquel l’URL fait référence (peut être vide).

*nPort (en)*<br/>
Déterminé à partir des parties serveur ou objet de l’URL, si l’un ou l’autre existe.

*strUsername*<br/>
Une référence `CString` à un objet contenant le nom de l’utilisateur.

*strPassword (strPassword)*<br/>
Une référence `CString` à un objet contenant le mot de passe de l’utilisateur.

*dwFlags*<br/>
Les drapeaux qui contrôlent la façon d’analyser l’URL. Peut être une combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|ICU_DECODE|Convertir %XX séquences d’évasion en caractères.|
|ICU_NO_ENCODE|Ne convertissez pas les caractères dangereux pour échapper à la séquence.|
|ICU_NO_META|N’enlevez pas les séquences de méta (telles que « ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' et "..") de l’URL.|
|ICU_ENCODE_SPACES_ONLY|Encodez uniquement les espaces.|
|ICU_BROWSER_MODE|Ne pas encoder ou décoder les caractères après ''ou '', et ne supprimez pas l’espace blanc de fuite après ''. Si cette valeur n’est pas spécifiée, l’URL entière est codée et l’espace blanc de fuite est supprimé.|

Si vous utilisez la valeur par défaut de MFC, qui n’est pas \\un signal, la \\fonction convertit tous les personnages dangereux et les méta séquences (tels que .,., et ...) pour échapper aux séquences.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’URL a été analysée avec succès; autrement, 0 s’il est vide ou ne contient pas un type de service Internet connu.

### <a name="remarks"></a>Notes

Il analyse une chaîne d’URL et renvoie le type de service et ses composants, ainsi que la fourniture du nom et du mot de passe de l’utilisateur. Les drapeaux indiquent comment les caractères dangereux sont manipulés.

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. H.

### <a name="requirements"></a>Spécifications

  **En-tête** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGetInternetHandleType AfxGetInternetHandleType AfxGetInternetHandleType Afx

Utilisez cette fonction globale pour déterminer le type de poignée Internet.

### <a name="syntax"></a>Syntaxe

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Paramètres

*hQuery (en)*<br/>
Une poignée à une requête Internet.

### <a name="return-value"></a>Valeur de retour

N’importe lequel des types de services Internet définis par WININET. H. Consultez la section Remarques pour une liste de ces services Internet. Si la poignée est NULL ou non reconnue, la fonction renvoie AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Notes

La liste suivante comprend les `AfxGetInternetHandleType`types Internet possibles retournés par .

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
> Afin d’appeler cette fonction, votre projet doit inclure AFXINET. H.

### <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrowInternetException

Jette une exception Internet.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Paramètres

*dwContexte*<br/>
L’identifiant de contexte pour l’opération qui a causé l’erreur. La valeur par défaut de *dwContext* est spécifiée à l’origine dans [CInternetSession](cinternetsession-class.md) et est transmise à [CInternetConnection](cinternetconnection-class.md)- et [CInternetFile](cinternetfile-class.md)-classes dérivées. Pour des opérations spécifiques effectuées sur une connexion ou un fichier, vous remplacez généralement la valeur par défaut avec un *dwContext* de votre propre. Cette valeur est ensuite retournée à [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) pour identifier l’état de l’opération spécifique.

*dwError*<br/>
Erreur ayant provoqué l'exception.

### <a name="remarks"></a>Notes

Vous êtes responsable de déterminer la cause en fonction du code d’erreur du système d’exploitation.

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. H.

### <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CInternetException, classe](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
