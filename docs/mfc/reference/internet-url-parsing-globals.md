---
title: Analyse des URL Internet globales et des assistances
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: c7ce6eeee6deb4537d09e102b925a742ada04650
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837162"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Analyse des URL Internet globales et des assistances

Lorsqu’un client envoie une requête au serveur Internet, vous pouvez utiliser l’une des variables globales d’analyse d’URL pour extraire des informations sur le client. Les fonctions d’assistance fournissent d’autres fonctionnalités Internet.

## <a name="internet-url-parsing-globals"></a>Objet Globals d'analyse des URL Internet

|Nom|Description|
|-|-|
|[AfxParseURL](#afxparseurl)|Analyse une chaîne d’URL et retourne le type de service et ses composants.|
|[AfxParseURLEx](#afxparseurlex)|Analyse une chaîne d’URL et retourne le type de service et ses composants, ainsi que la fourniture du nom d’utilisateur et du mot de passe.|

## <a name="other-internet-helpers"></a>Autres assistances Internet

|Nom|Description|
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Lève une exception liée à la connexion Internet.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Détermine le type d’un handle Internet.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a> AfxParseURL

Ce global est utilisé dans [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Paramètres

*pstrURL*<br/>
Pointeur vers une chaîne contenant l’URL à analyser.

*dwServiceType*<br/>
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

*strServer*<br/>
Premier segment de l’URL qui suit le type de service.

*strObject*<br/>
Objet auquel l’URL fait référence (peut être vide).

*nPort*<br/>
Déterminé à partir des parties serveur ou objet de l’URL, s’il en existe une.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’URL a été analysée avec succès ; Sinon, 0 s’il est vide ou ne contient pas de type de service Internet connu.

### <a name="remarks"></a>Notes

Il analyse une chaîne d’URL et retourne le type de service et ses composants.

Par exemple, `AfxParseURL` analyse les URL de la forme *service://Server/dir/DIR/Object.ext :port* et retourne ses composants stockés comme suit :

*strServer* = = "serveur"

*strObject* = = "/dir/DIR/Object/Object.ext"

*NPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. Manutention.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXINET. h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a> AfxParseURLEx

Cette fonction globale est la version étendue de [AfxParseURL](#afxparseurl) et est utilisée dans [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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

*pstrURL*<br/>
Pointeur vers une chaîne contenant l’URL à analyser.

*dwServiceType*<br/>
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

*strServer*<br/>
Premier segment de l’URL qui suit le type de service.

*strObject*<br/>
Objet auquel l’URL fait référence (peut être vide).

*nPort*<br/>
Déterminé à partir des parties serveur ou objet de l’URL, s’il en existe une.

*strUsername*<br/>
Référence à un `CString` objet contenant le nom de l’utilisateur.

*strPassword*<br/>
Référence à un `CString` objet contenant le mot de passe de l’utilisateur.

*dwFlags*<br/>
Indicateurs qui contrôlent la façon dont l’URL doit être analysée. Peut être une combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|ICU_DECODE|Convertit% XX séquences d’échappement en caractères.|
|ICU_NO_ENCODE|Ne convertissez pas les caractères non sécurisés en séquence d’échappement.|
|ICU_NO_META|Ne supprimez pas les séquences de métadonnées (par exemple, « \. » et "\..") à partir de l’URL.|
|ICU_ENCODE_SPACES_ONLY|Encoder les espaces uniquement.|
|ICU_BROWSER_MODE|Ne pas encoder ou décoder les caractères après « # » ou « » et ne pas supprimer les espaces blancs de fin après « ». Si cette valeur n’est pas spécifiée, l’URL entière est encodée et l’espace blanc de fin est supprimé.|

Si vous utilisez la valeur par défaut MFC, qui n’est pas un indicateur, la fonction convertit tous les caractères et séquences de métadonnées non sécurisés (tels que \\ ., \... et \\ ...) en séquences d’échappement.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’URL a été analysée avec succès ; Sinon, 0 s’il est vide ou ne contient pas de type de service Internet connu.

### <a name="remarks"></a>Notes

Il analyse une chaîne d’URL et retourne le type de service et ses composants, ainsi que le nom et le mot de passe de l’utilisateur. Les indicateurs indiquent la manière dont les caractères non sécurisés sont gérés.

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. Manutention.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXINET. h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a> AfxGetInternetHandleType

Utilisez cette fonction globale pour déterminer le type d’un descripteur Internet.

### <a name="syntax"></a>Syntaxe

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Paramètres

*hQuery*<br/>
Handle d’une requête Internet.

### <a name="return-value"></a>Valeur renvoyée

N’importe quel type de service Internet défini par WININET. Manutention. Consultez la section Notes pour obtenir la liste de ces services Internet. Si le handle est NULL ou n’est pas reconnu, la fonction retourne AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Notes

La liste suivante répertorie les types Internet possibles retournés par `AfxGetInternetHandleType` .

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
> Pour appeler cette fonction, votre projet doit inclure AFXINET. Manutention.

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXINET. h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a> AfxThrowInternetException

Lève une exception Internet.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Paramètres

*dwContext*<br/>
Identificateur de contexte de l’opération à l’origine de l’erreur. La valeur par défaut de *dwContext* est spécifiée à l’origine dans [CInternetSession](cinternetsession-class.md) et est passée aux classes dérivées de [CInternetConnection,](cinternetconnection-class.md)et [CInternetFile](cinternetfile-class.md). Pour les opérations spécifiques effectuées sur une connexion ou un fichier, vous remplacez généralement la valeur par défaut par un *dwContext* . Cette valeur est ensuite retournée à [CInternetSession :: OnStatusCallback](cinternetsession-class.md#onstatuscallback) pour identifier l’état de l’opération spécifique.

*dwError*<br/>
Erreur ayant provoqué l'exception.

### <a name="remarks"></a>Notes

Vous êtes responsable de la détermination de la cause en fonction du code d’erreur du système d’exploitation.

> [!NOTE]
> Pour appeler cette fonction, votre projet doit inclure AFXINET. Manutention.

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXINET. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CInternetException, classe](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
