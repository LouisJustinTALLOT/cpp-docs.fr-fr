---
description: 'En savoir plus sur : CHttpFile, classe'
title: CHttpFile, classe
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: 95beff477e19ef15235ceb7235aa0240ec07ff65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209969"
---
# <a name="chttpfile-class"></a>CHttpFile, classe

Fournit les fonctionnalités permettant de demander et de lire des fichiers sur un serveur HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CHttpFile :: CHttpFile](#chttpfile)|Crée un objet `CHttpFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHttpFile :: AddRequestHeaders](#addrequestheaders)|Ajoute des en-têtes à la demande envoyée à un serveur HTTP.|
|[CHttpFile :: EndRequest](#endrequest)|Met fin à une demande envoyée à un serveur HTTP avec la fonction membre [SendRequestEx](#sendrequestex) .|
|[CHttpFile :: GetFileURL](#getfileurl)|Obtient l’URL du fichier spécifié.|
|[CHttpFile :: GetObject](#getobject)|Obtient l’objet cible du verbe dans une demande adressée à un serveur HTTP.|
|[CHttpFile :: GetVerb](#getverb)|Obtient le verbe utilisé dans une demande à un serveur HTTP.|
|[CHttpFile :: QueryInfo](#queryinfo)|Retourne les en-têtes de réponse ou de demande à partir du serveur HTTP.|
|[CHttpFile :: QueryInfoStatusCode](#queryinfostatuscode)|Récupère le code d’état associé à une requête HTTP et le place dans le `dwStatusCode` paramètre fourni.|
|[CHttpFile :: SendRequest](#sendrequest)|Envoie une requête à un serveur HTTP.|
|[CHttpFile :: SendRequestEx](#sendrequestex)|Envoie une requête à un serveur HTTP à l’aide des méthodes [Write](../../mfc/reference/cinternetfile-class.md#write) ou [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de `CInternetFile` .|

## <a name="remarks"></a>Notes

Si votre session Internet lit les données à partir d’un serveur HTTP, vous devez créer une instance de `CHttpFile` .

Pour en savoir plus sur le `CHttpFile` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a> CHttpFile :: AddRequestHeaders

Appelez cette fonction membre pour ajouter un ou plusieurs en-têtes de requête HTTP au descripteur de requête HTTP.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>Paramètres

*pstrHeaders*<br/>
Pointeur vers une chaîne contenant l’en-tête ou les en-têtes à ajouter à la demande. Chaque en-tête doit se terminer par une paire CR/LF.

*dwFlags*<br/>
Modifie la sémantique des nouveaux en-têtes. Il peut s'agir d'une des méthodes suivantes :

- HTTP_ADDREQ_FLAG_COALESCE fusionne les en-têtes du même nom, à l’aide de l’indicateur pour ajouter le premier en-tête trouvé à l’en-tête suivant. Par exemple, « Accept : Text/ \* » suivi de « Accept : audio/ \* » produit la formation de l’en-tête unique « Accept : Text/ \* , audio/ \* ». Il revient à l’application appelante de garantir un schéma cohésif en ce qui concerne les données reçues par les demandes envoyées avec des en-têtes fusionnés ou distincts.

- HTTP_ADDREQ_FLAG_REPLACE effectue une suppression et un ajout pour remplacer l’en-tête actuel. Le nom d’en-tête sera utilisé pour supprimer l’en-tête actuel, et la valeur complète sera utilisée pour ajouter le nouvel en-tête. Si la valeur d’en-tête est vide et que l’en-tête est trouvé, elle est supprimée. S’il n’est pas vide, la valeur d’en-tête est remplacée.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW ajoute l’en-tête uniquement s’il n’existe pas déjà. S’il en existe une, une erreur est retournée.

- HTTP_ADDREQ_FLAG_ADD utilisé avec Replace. Ajoute l’en-tête s’il n’existe pas.

*dwHeadersLen*<br/>
Longueur, en caractères, de *pstrHeaders*. S’il s’agit de-1L, *pstrHeaders* est supposé être terminé par zéro et la longueur est calculée.

*str*<br/>
Référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’en-tête ou les en-têtes de demande à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`AddRequestHeaders` Ajoute des en-têtes de format libre supplémentaires au handle de requête HTTP. Elle est destinée à être utilisée par des clients sophistiqués qui ont besoin d’un contrôle détaillé sur la demande exacte envoyée au serveur HTTP.

> [!NOTE]
> L’application peut passer plusieurs en-têtes dans *pstrHeaders* ou *Str* pour un `AddRequestHeaders` appel à l’aide de HTTP_ADDREQ_FLAG_ADD ou HTTP_ADDREQ_FLAG_ADD_IF_NEW. Si l’application tente de supprimer ou de remplacer un en-tête à l’aide de HTTP_ADDREQ_FLAG_REMOVE ou HTTP_ADDREQ_FLAG_REPLACE, un seul en-tête peut être fourni dans *lpszHeaders*.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a> CHttpFile :: CHttpFile

Cette fonction membre est appelée pour construire un `CHttpFile` objet.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>Paramètres

*hFile*<br/>
Handle d’un fichier Internet.

*hSession*<br/>
Handle d’une session Internet.

*pstrObject*<br/>
Pointeur vers une chaîne contenant l' `CHttpFile` objet.

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur.

*pstrVerb*<br/>
Pointeur vers une chaîne contenant la méthode à utiliser lors de l’envoi de la demande. Peut être de la publication, du début ou de l’extraction.

*dwContext*<br/>
Identificateur de contexte de l' `CHttpFile` objet. Pour plus d’informations sur ce paramètre, consultez la **section Notes** .

*pConnection*<br/>
Pointeur vers un objet [CHttpConnection](../../mfc/reference/chttpconnection-class.md) .

### <a name="remarks"></a>Notes

Vous ne construisez jamais `CHttpFile` directement un objet, plutôt que d’appeler [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection :: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) à la place.

La valeur par défaut de `dwContext` est envoyée par MFC à l' `CHttpFile` objet à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l' `CHttpFile` objet. Quand vous appelez `CInternetSession::OpenURL` ou `CHttpConnection` pour construire un `CHttpFile` objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="chttpfileendrequest"></a><a name="endrequest"></a> CHttpFile :: EndRequest

Appelez cette fonction membre pour terminer une demande envoyée à un serveur HTTP avec la fonction membre [SendRequestEx](#sendrequestex) .

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Indicateurs décrivant l’opération. Pour obtenir la liste des indicateurs appropriés, consultez [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) dans le SDK Windows.

*lpBuffIn*<br/>
Pointeur vers un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) initialisé qui décrit la mémoire tampon d’entrée utilisée pour l’opération.

*dwContext*<br/>
Identificateur de contexte de l' `CHttpFile` opération. Pour plus d’informations sur ce paramètre, consultez la section Notes.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* est envoyée par MFC à l' `CHttpFile` objet à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l' `CHttpFile` objet. Quand vous appelez [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet First Steps : wininet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a> CHttpFile :: GetFileURL

Appelez cette fonction membre pour obtenir le nom du fichier HTTP sous la forme d’une URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant une URL faisant référence à la ressource associée à ce fichier.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement après un appel réussi à [SendRequest](#sendrequest) ou sur un `CHttpFile` objet créé correctement par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetobject"></a><a name="getobject"></a> CHttpFile :: GetObject

Appelez cette fonction membre pour récupérer le nom de l’objet associé à ce `CHttpFile` .

```
CString GetObject() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom de l’objet.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement après un appel réussi à [SendRequest](#sendrequest) ou sur un `CHttpFile` objet créé correctement par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetverb"></a><a name="getverb"></a> CHttpFile :: GetVerb

Appelez cette fonction membre pour recevoir le verbe HTTP (ou la méthode) associée à ce `CHttpFile` .

```
CString GetVerb() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom du verbe http (ou de la méthode).

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement après un appel réussi à [SendRequest](#sendrequest) ou sur un `CHttpFile` objet créé correctement par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a> CHttpFile :: QueryInfo

Appelez cette fonction membre pour retourner des en-têtes de réponse ou de demande à partir d’une requête HTTP.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>Paramètres

*dwInfoLevel*<br/>
Combinaison de l’attribut à interroger et des indicateurs suivants qui spécifient le type d’informations demandé :

- HTTP_QUERY_CUSTOM recherche le nom de l’en-tête et retourne cette valeur dans *lpvBuffer* à la sortie. HTTP_QUERY_CUSTOM lève une assertion si l’en-tête est introuvable.

- HTTP_QUERY_FLAG_REQUEST_HEADERS généralement, l’application interroge les en-têtes de réponse, mais une application peut également interroger des en-têtes de demande à l’aide de cet indicateur.

- HTTP_QUERY_FLAG_SYSTEMTIME pour les en-têtes dont la valeur est une chaîne de date/heure, telle que « Last-modified-Time », cet indicateur retourne la valeur d’en-tête en tant que structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) Win32 standard qui ne nécessite pas que l’application analyse les données. Si vous utilisez cet indicateur, vous souhaiterez peut-être utiliser la `SYSTEMTIME` substitution de la fonction.

- HTTP_QUERY_FLAG_NUMBER pour les en-têtes dont la valeur est un nombre, tel que le code d’État, cet indicateur retourne les données sous la forme d’un nombre de 32 bits.

Consultez la section **Notes** pour obtenir la liste des valeurs possibles.

*lpvBuffer*<br/>
Pointeur vers la mémoire tampon qui reçoit les informations.

*lpdwBufferLength*<br/>
À l’entrée, cette valeur pointe vers une valeur contenant la longueur de la mémoire tampon de données, en nombre de caractères ou en octets. Pour plus d’informations sur ce paramètre, consultez la section **Notes** .

*lpdwIndex*<br/>
Pointeur vers un index d’en-tête de base zéro. Sa valeur peut être NULL. Utilisez cet indicateur pour énumérer plusieurs en-têtes portant le même nom. En entrée, *lpdwIndex* indique l’index de l’en-tête spécifié à retourner. Lors de la sortie, *lpdwIndex* indique l’index de l’en-tête suivant. Si l’index suivant est introuvable, ERROR_HTTP_HEADER_NOT_FOUND est retourné.

*str*<br/>
Référence à l’objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit les informations retournées.

*dwIndex*<br/>
Valeur d’index. Consultez *lpdwIndex*.

*pSysTime*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) Win32.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement après un appel réussi à [SendRequest](#sendrequest) ou sur un `CHttpFile` objet créé correctement par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Vous pouvez récupérer les types de données suivants à partir de `QueryInfo` :

- chaînes (par défaut)

- `SYSTEMTIME` (pour « données : « » expire :», etc., en-têtes)

- DWORD (pour STATUS_CODE, CONTENT_LENGTH, etc.)

Lorsqu’une chaîne est écrite dans la mémoire tampon et que la fonction membre est réussie, `lpdwBufferLength` contient la longueur de la chaîne en caractères moins 1 pour le caractère null de fin.

Les valeurs possibles de *dwInfoLevel* sont les suivantes :

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a> CHttpFile :: QueryInfoStatusCode

Appelez cette fonction membre pour obtenir le code d’état associé à une requête HTTP et placez-la dans le paramètre *dwStatusCode* fourni.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Paramètres

*dwStatusCode*<br/>
Référence à un code d’État. Les codes d’État indiquent la réussite ou l’échec de l’événement demandé. Consultez la **section Notes** pour une sélection des descriptions de code d’État.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement après un appel réussi à [SendRequest](#sendrequest) ou sur un `CHttpFile` objet créé correctement par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Les codes d’état HTTP appartiennent à des groupes indiquant la réussite ou l’échec de la demande. Les tableaux suivants décrivent les groupes de codes d’État et les codes d’état HTTP les plus courants.

|Groupe|Signification|
|-----------|-------------|
|200-299|Succès|
|300-399|Information|
|400-499|Erreur de requête|
|500-599|Erreur de serveur|

Codes d’état HTTP courants :

|Code d’état|Signification|
|-----------------|-------------|
|200|URL située, transmission suit|
|400|Requête inintelligible|
|404|URL demandée introuvable|
|405|Le serveur ne prend pas en charge la méthode demandée|
|500|Erreur de serveur inconnue|
|503|Capacité du serveur atteinte|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a> CHttpFile :: SendRequest

Appelez cette fonction membre pour envoyer une demande à un serveur HTTP.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>Paramètres

*pstrHeaders*<br/>
Pointeur vers une chaîne contenant le nom des en-têtes à envoyer.

*dwHeadersLen*<br/>
Longueur des en-têtes identifiés par *pstrHeaders*.

*lpOptional*<br/>
Toutes les données facultatives à envoyer immédiatement après les en-têtes de demande. Cela est généralement utilisé pour les opérations de publication et de placement. Il peut s’agir de la valeur NULL s’il n’y a pas de données facultatives à envoyer.

*dwOptionalLen*<br/>
Longueur de *lpOptional*.

*strHeaders*<br/>
Chaîne contenant le nom des en-têtes de la demande envoyée.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a> CHttpFile :: SendRequestEx

Appelez cette fonction membre pour envoyer une demande à un serveur HTTP.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*dwTotalLen*<br/>
Nombre d’octets à envoyer dans la demande.

*dwFlags*<br/>
Indicateurs décrivant l’opération. Pour obtenir la liste des indicateurs appropriés, consultez [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) dans le SDK Windows.

*dwContext*<br/>
Identificateur de contexte de l' `CHttpFile` opération. Pour plus d’informations sur ce paramètre, consultez la section Notes.

*lpBuffIn*<br/>
Pointeur vers un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) initialisé qui décrit la mémoire tampon d’entrée utilisée pour l’opération.

*lpBuffOut*<br/>
Pointeur vers un INTERNET_BUFFERS initialisé qui décrit la mémoire tampon de sortie utilisée pour l’opération.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

Cette fonction permet à votre application d’envoyer des données à l’aide des méthodes [Write](../../mfc/reference/cinternetfile-class.md#write) et [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de `CInternetFile` . Vous devez connaître la longueur des données à envoyer avant d’appeler la substitution de cette fonction. Le premier remplacement vous permet de spécifier la longueur des données que vous souhaitez envoyer. Le deuxième remplacement accepte les pointeurs vers des structures de INTERNET_BUFFERS, qui peuvent être utilisées pour décrire la mémoire tampon de manière très détaillée.

Une fois que le contenu est écrit dans le fichier, appelez [EndRequest](#endrequest) pour terminer l’opération.

La valeur par défaut pour *dwContext* est envoyée par MFC à l' `CHttpFile` objet à partir de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l' `CHttpFile` objet. Quand vous appelez [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

### <a name="example"></a>Exemple

Ce fragment de code envoie le contenu d’une chaîne à une DLL nommée MFCISAPI.DLL sur le serveur LOCALHOST. Bien que cet exemple utilise un seul appel à `WriteString` , l’utilisation de plusieurs appels pour envoyer des données par blocs est acceptable.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)
