---
title: Classe CHttpFile
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
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368390"
---
# <a name="chttpfile-class"></a>Classe CHttpFile

Fournit les fonctionnalités permettant de demander et de lire des fichiers sur un serveur HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Crée un objet `CHttpFile` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Ajoute des en-têtes à la demande envoyée à un serveur HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Termine une demande envoyée à un serveur HTTP avec la fonction membre [SendRequestEx.](#sendrequestex)|
|[CHttpFile::GetFileURL](#getfileurl)|Obtient l’URL pour le fichier spécifié.|
|[CHttpFile::GetObject](#getobject)|Obtient l’objet cible du verbe dans une demande à un serveur HTTP.|
|[CHttpFile::GetVerb](#getverb)|Obtient le verbe qui a été utilisé dans une demande à un serveur HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Retourne la réponse ou demande des en-têtes du serveur HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Récupère le code d’état associé à une `dwStatusCode` demande HTTP et le place dans le paramètre fourni.|
|[CHttpFile::SendRequest](#sendrequest)|Envoie une demande à un serveur HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Envoie une demande à un serveur HTTP en `CInternetFile`utilisant les méthodes [Write](../../mfc/reference/cinternetfile-class.md#write) ou [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de .|

## <a name="remarks"></a>Notes

Si votre session Internet lit les données d’un `CHttpFile`serveur HTTP, vous devez créer une instance de .

Pour en savoir `CHttpFile` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Appelez cette fonction de membre pour ajouter un ou plusieurs en-têtes de demande HTTP à la poignée de demande HTTP.

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
Un pointeur à une chaîne contenant l’en-tête ou les en-têtes pour ajouter à la demande. Chaque en-tête doit être terminé par une paire CR/LF.

*dwFlags*<br/>
Modifie la sémantique des nouveaux en-têtes. Il peut s'agir d'une des méthodes suivantes :

- HTTP_ADDREQ_FLAG_COALESCE fusionne les en-têtes du même nom, en utilisant le drapeau pour ajouter la première en-tête trouvée à l’en-tête suivant. Par exemple, "Accepter:\*texte/ " suivi\*par "Accepter: audio/ " aboutit\*à la\*formation de l’en-tête unique "Accepter: texte / , audio/ ". Il appartient à la demande d’appel d’assurer un schéma cohérent en ce qui concerne les données reçues par les demandes envoyées avec des en-têtes fusionnés ou séparés.

- HTTP_ADDREQ_FLAG_REPLACE effectue une suppression et ajouter pour remplacer l’en-tête actuel. Le nom d’en-tête sera utilisé pour supprimer l’en-tête actuel, et la pleine valeur sera utilisée pour ajouter le nouvel en-tête. Si la valeur de l’en-tête est vide et que l’en-tête est trouvé, il est supprimé. S’il n’est pas vide, la valeur de l’en-tête est remplacée.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW Seulement ajoute l’en-tête s’il n’existe pas déjà. Si l’on existe, une erreur est retournée.

- HTTP_ADDREQ_FLAG_ADD utilisé avec REPLACE. Ajoute l’en-tête s’il n’existe pas.

*dwHeadersLen*<br/>
La longueur, en caractères, de *pstrHeaders*. Si c’est -1L, alors *pstrHeaders* est supposé être zéro-ended et la longueur est calculée.

*Str*<br/>
Une référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’en-tête de demande ou des en-têtes à ajouter.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`AddRequestHeaders`joint des en-têtes supplémentaires en format libre à la poignée de demande HTTP. Il est destiné à être utilisé par des clients sophistiqués qui ont besoin d’un contrôle détaillé sur la demande exacte envoyée au serveur HTTP.

> [!NOTE]
> L’application peut passer plusieurs en-têtes dans *pstrHeaders* ou *str* pour un `AddRequestHeaders` appel en utilisant HTTP_ADDREQ_FLAG_ADD ou HTTP_ADDREQ_FLAG_ADD_IF_NEW. Si l’application tente de supprimer ou de remplacer un en-tête à l’aide de HTTP_ADDREQ_FLAG_REMOVE ou de HTTP_ADDREQ_FLAG_REPLACE, un seul en-tête peut être fourni en *lpszHeaders*.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile::CHttpFile

Cette fonction de membre `CHttpFile` est appelée à construire un objet.

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

*hFile (en)*<br/>
Une poignée à un fichier Internet.

*hSession*<br/>
Une poignée à une session Internet.

*pstrObject*<br/>
Un pointeur à `CHttpFile` une chaîne contenant l’objet.

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur.

*pstrVerb (pstrVerb)*<br/>
Un pointeur à une chaîne contenant la méthode à utiliser lors de l’envoi de la demande. Peut être POST, HEAD, ou GET.

*dwContexte*<br/>
L’identifiant de `CHttpFile` contexte pour l’objet. Voir **Remarques** pour plus d’informations sur ce paramètre.

*pConnection*<br/>
Un pointeur vers un objet [CHttpConnection.](../../mfc/reference/chttpconnection-class.md)

### <a name="remarks"></a>Notes

Vous ne `CHttpFile` construisez jamais un objet directement; plutôt appeler [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) à la place.

La valeur `dwContext` par défaut est envoyée `CHttpFile` par MFC à l’objet à `CHttpFile` partir de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet. Lorsque vous `CInternetSession::OpenURL` `CHttpConnection` appelez ou `CHttpFile` construisez un objet, vous pouvez remplacer la valeur par défaut pour définir l’identifiant contextuelle à une valeur de votre choix. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile::EndRequest

Appelez cette fonction de membre pour mettre fin à une demande envoyée à un serveur HTTP avec la fonction membre [SendRequestEx.](#sendrequestex)

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Drapeaux décrivant l’opération. Pour une liste des drapeaux appropriés, voir [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) dans le SDK Windows.

*lpBuffIn*<br/>
Pointeur vers un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) initialisé qui décrit le tampon d’entrée utilisé pour l’opération.

*dwContexte*<br/>
L’identifiant de `CHttpFile` contexte pour l’opération. Voir Remarques pour plus d’informations sur ce paramètre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

La valeur par défaut pour *dwContext* `CHttpFile` est envoyée par MFC à l’objet `CHttpFile` de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet. Lorsque vous appelez [CInternetSession: :OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` objet, vous pouvez remplacer la valeur par défaut pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile::GetFileURL

Appelez cette fonction de membre pour obtenir le nom du fichier HTTP comme URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant une URL faisant référence à la ressource associée à ce fichier.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre seulement après un appel `CHttpFile` réussi à [SendRequest](#sendrequest) ou sur un objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile::GetObject

Appelez cette fonction de membre pour obtenir `CHttpFile`le nom de l’objet associé à ceci .

```
CString GetObject() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom de l’objet.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre seulement après un appel `CHttpFile` réussi à [SendRequest](#sendrequest) ou sur un objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile::GetVerb

Appelez cette fonction de membre pour obtenir le `CHttpFile`verbe HTTP (ou la méthode) associé à ceci .

```
CString GetVerb() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom du verbe HTTP (ou méthode).

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre seulement après un appel `CHttpFile` réussi à [SendRequest](#sendrequest) ou sur un objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile::QueryInfo

Appelez cette fonction de membre pour retourner la réponse ou demander des en-têtes à partir d’une demande HTTP.

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
Une combinaison de l’attribut à la requête et des drapeaux suivants qui spécifient le type d’information demandée :

- HTTP_QUERY_CUSTOM Trouve le nom d’en-tête et retourne cette valeur dans *lpvBuffer* sur la sortie. HTTP_QUERY_CUSTOM lance une affirmation si l’en-tête n’est pas trouvé.

- HTTP_QUERY_FLAG_REQUEST_HEADERS Typiquement, l’application interroge les en-têtes de réponse, mais une application peut également interroger les en-têtes de demande en utilisant ce drapeau.

- HTTP_QUERY_FLAG_SYSTEMTIME Pour les en-têtes dont la valeur est une chaîne de date/temps, comme « Last-Modified-Time », ce drapeau renvoie la valeur d’en-tête comme une structure standard Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui n’exige pas que l’application analyse les données. Si vous utilisez ce drapeau, vous `SYSTEMTIME` pouvez utiliser le remplacement de la fonction.

- HTTP_QUERY_FLAG_NUMBER Pour les en-têtes dont la valeur est un nombre, comme le code d’état, ce drapeau renvoie les données comme un nombre 32 bits.

Consultez la section **Remarques** pour une liste des valeurs possibles.

*lpvBuffer*<br/>
Un pointeur vers le tampon qui reçoit l’information.

*lpdwBufferLength*<br/>
À l’entrée, cela indique une valeur contenant la longueur du tampon de données, en nombre de caractères ou d’octets. Consultez la section **Remarques** pour obtenir des informations plus détaillées sur ce paramètre.

*lpdwIndex*<br/>
Un pointeur vers un index d’en-tête à base de zéro. Sa valeur peut être NULL. Utilisez ce drapeau pour énumérer plusieurs en-têtes du même nom. Sur l’entrée, *lpdwIndex* indique l’indice de l’en-tête spécifié pour revenir. Sur la production, *lpdwIndex* indique l’indice de l’en-tête suivant. Si l’indice suivant ne peut pas être trouvé, ERROR_HTTP_HEADER_NOT_FOUND est retourné.

*Str*<br/>
Une référence à l’objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) recevant les informations retournées.

*dwIndex*<br/>
Une valeur indicative. Voir *lpdwIndex*.

*pSysTime (en)*<br/>
Un pointeur vers une structure Win32 [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre seulement après un appel `CHttpFile` réussi à [SendRequest](#sendrequest) ou sur un objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Vous pouvez récupérer les types `QueryInfo`de données suivants à partir de :

- cordes (par défaut)

- `SYSTEMTIME`(pour "Data:" "Expires:" etc., en-têtes)

- DWORD (pour STATUS_CODE, CONTENT_LENGTH, etc.)

Lorsqu’une chaîne est écrite au tampon, et `lpdwBufferLength` que la fonction du membre réussit, contient la longueur de la chaîne dans les caractères moins 1 pour le caractère NULL de fin.

Les valeurs possibles *dwInfoLevel* comprennent :

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

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode

Appelez cette fonction de membre pour obtenir le code d’état associé à une demande HTTP et placez-le dans le paramètre *dwStatusCode* fourni.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Paramètres

*dwStatusCode (en)*<br/>
Une référence à un code de statut. Les codes d’état indiquent le succès ou l’échec de l’événement demandé. Voir **Remarques** pour une sélection de descriptions de code de statut.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre seulement après un appel `CHttpFile` réussi à [SendRequest](#sendrequest) ou sur un objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Les codes d’état HTTP font partie de groupes indiquant le succès ou l’échec de la demande. Les tableaux suivants décrivent les groupes de code d’état et les codes de statut HTTP les plus courants.

|Groupe|Signification|
|-----------|-------------|
|200-299|Succès|
|300-399|Information|
|400-499|Erreur de demande|
|500-599|Erreur de serveur|

Codes de statut HTTP communs :

|Code d’état|Signification|
|-----------------|-------------|
|200|URL localisée, transmission suit|
|400|Demande inintelligible|
|404|URL demandée non trouvée|
|405|Le serveur ne prend pas en charge la méthode demandée|
|500|Erreur de serveur inconnue|
|503|Capacité du serveur atteinte|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile::SendRequest

Appelez cette fonction de membre pour envoyer une demande à un serveur HTTP.

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
Un pointeur à une chaîne contenant le nom des en-têtes à envoyer.

*dwHeadersLen*<br/>
La longueur des en-têtes identifiés par *pstrHeaders*.

*lpOptional*<br/>
Toutes les données facultatives à envoyer immédiatement après les en-têtes de la demande. Ceci est généralement utilisé pour les opérations POST et PUT. Cela peut être NULL s’il n’y a pas de données facultatives à envoyer.

*dwOptionalLen*<br/>
La longueur de *lpOptional*.

*strHeaders (en)*<br/>
Une chaîne contenant le nom des en-têtes pour la demande envoyée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::SendRequestEx

Appelez cette fonction de membre pour envoyer une demande à un serveur HTTP.

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
Drapeaux décrivant l’opération. Pour une liste de drapeaux appropriés, voir [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) dans le SDK Windows.

*dwContexte*<br/>
L’identifiant de `CHttpFile` contexte pour l’opération. Voir Remarques pour plus d’informations sur ce paramètre.

*lpBuffIn*<br/>
Pointeur vers un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) initialisé qui décrit le tampon d’entrée utilisé pour l’opération.

*lpBuffOut*<br/>
Pointeur d’un INTERNET_BUFFERS initialisé qui décrit le tampon de sortie utilisé pour l’opération.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

Cette fonction permet à votre application d’envoyer des `CInternetFile`données à l’aide des méthodes [Write](../../mfc/reference/cinternetfile-class.md#write) and [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de . Vous devez connaître la longueur des données à envoyer avant d’appeler l’un ou l’autre remplacement de cette fonction. Le premier remplacement vous permet de spécifier la longueur des données que vous souhaitez envoyer. La deuxième dérogation accepte les indications pour INTERNET_BUFFERS structures, qui peuvent être utilisées pour décrire le tampon en détail.

Une fois que le contenu est écrit au fichier, appelez [EndRequest](#endrequest) pour mettre fin à l’opération.

La valeur par défaut pour *dwContext* `CHttpFile` est envoyée par MFC à l’objet `CHttpFile` de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet. Lorsque vous appelez [CInternetSession: :OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` objet, vous pouvez remplacer la valeur par défaut pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

### <a name="example"></a>Exemple

Ce fragment de code envoie le contenu d’une chaîne à un DLL nommé MFCISAPI. DLL sur le serveur LOCALHOST. Bien que cet exemple `WriteString`n’utilise qu’un seul appel, l’utilisation de plusieurs appels pour envoyer des données dans les blocs est acceptable.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Classe CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)
