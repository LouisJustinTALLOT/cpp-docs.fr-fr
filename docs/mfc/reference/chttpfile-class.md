---
title: Classe de CHttpFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d920ca54c9e97273e4bda563921a144339eafd0f
ms.sourcegitcommit: 05075fce8a0ed7fddb99f50f3931db966a91450d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271345"
---
# <a name="chttpfile-class"></a>Classe de CHttpFile
Fournit les fonctionnalités permettant de demander et de lire des fichiers sur un serveur HTTP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CHttpFile::CHttpFile](#chttpfile)|Crée un objet `CHttpFile`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Ajoute des en-têtes à la demande envoyée à un serveur HTTP.|  
|[CHttpFile::EndRequest](#endrequest)|Met fin à une demande envoyée à un serveur HTTP avec le [SendRequestEx](#sendrequestex) fonction membre.|  
|[CHttpFile::GetFileURL](#getfileurl)|Obtient l’URL pour le fichier spécifié.|  
|[CHttpFile::GetObject](#getobject)|Obtient l’objet cible du verbe dans une demande à un serveur HTTP.|  
|[CHttpFile::GetVerb](#getverb)|Obtient le verbe qui a été utilisé dans une demande à un serveur HTTP.|  
|[CHttpFile::QueryInfo](#queryinfo)|Retourne les en-têtes de réponse ou demande à partir du serveur HTTP.|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Récupère le code d’état associé à une requête HTTP et le place dans le `dwStatusCode` paramètre.|  
|[CHttpFile::SendRequest](#sendrequest)|Envoie une demande à un serveur HTTP.|  
|[CHttpFile::SendRequestEx](#sendrequestex)|Envoie une demande à un serveur HTTP à l’aide du [écrire](../../mfc/reference/cinternetfile-class.md#write) ou [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) méthodes de `CInternetFile`.|  
  
## <a name="remarks"></a>Notes  
 Si votre session Internet lit des données à partir d’un serveur HTTP, vous devez créer une instance de `CHttpFile`.  
  
 Pour en savoir plus sur la façon `CHttpFile` fonctionne avec les autres classes MFC Internet, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxinet.h  
  
##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders  
 Appelez cette fonction membre pour ajouter un ou plusieurs en-têtes HTTP pour la requête HTTP gérer.  
  
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
 `pstrHeaders`  
 Un pointeur vers une chaîne contenant l’en-tête ou les en-têtes à ajouter à la demande. Chaque en-tête doit se terminer par une paire retour chariot/saut de ligne.  
  
 `dwFlags`  
 Modifie la sémantique des en-têtes de nouveau. Il peut s'agir d'une des valeurs suivantes :  
  
- `HTTP_ADDREQ_FLAG_COALESCE` Fusionne les en-têtes du même nom, à l’aide de l’indicateur pour ajouter le premier en-tête trouvé pour l’en-tête suivant. Par exemple, « accepter : texte /\*» suivie » accepter : audio /\*» entraîne la formation de l’en-tête unique « accepter : texte /\*, audio /\*». C’est à l’application appelante pour garantir un schéma cohérent en ce qui concerne les données reçues par les demandes envoyées avec en-têtes fusionnés ou distincts.  
  
- `HTTP_ADDREQ_FLAG_REPLACE` Effectue une suppression et ajoutez pour remplacer l’en-tête actuel. Le nom d’en-tête permet de supprimer l’en-tête actuel, et la valeur complète sera utilisée pour ajouter le nouvel en-tête. Si la valeur d’en-tête est vide et l’en-tête est trouvé, il est supprimé. Si la valeur n’est pas vide, la valeur d’en-tête est remplacée.  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW` Ajoute uniquement l’en-tête s’il n’existe pas. S’il en existe, une erreur est retournée.  
  
- `HTTP_ADDREQ_FLAG_ADD` Utilisé avec remplacement. Ajoute l’en-tête s’il n’existe.  
  
 `dwHeadersLen`  
 La longueur, en caractères, de `pstrHeaders`. S’il s’agit-1 L, puis `pstrHeaders` est censé se terminant par zéro et la longueur est calculée.  
  
 `str`  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant l’en-tête de demande ou les en-têtes à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelé pour déterminer la cause de l’erreur.  
  
### <a name="remarks"></a>Notes  
 `AddRequestHeaders` Ajoute des en-têtes supplémentaires, au format libre pour le handle de requête HTTP. Elle est destinée aux clients sophistiquées qui ont besoin de contrôler la demande exacte envoyée au serveur HTTP.  
  
> [!NOTE]
>  L’application peut passer plusieurs en-têtes dans `pstrHeaders` ou `str` pour un `AddRequestHeaders` appeler à l’aide de `HTTP_ADDREQ_FLAG_ADD` ou `HTTP_ADDREQ_FLAG_ADD_IF_NEW`. Si l’application essaie de supprimer ou remplacer un en-tête à l’aide de **HTTP_ADDREQ_FLAG_REMOVE** ou `HTTP_ADDREQ_FLAG_REPLACE`, un seul en-tête peut être fourni dans `lpszHeaders`.  
  
##  <a name="chttpfile"></a>  CHttpFile::CHttpFile  
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
 `hFile`  
 Handle vers un fichier d’Internet.  
  
 `hSession`  
 Un handle à une session Internet.  
  
 *pstrObject*  
 Un pointeur vers une chaîne contenant le `CHttpFile` objet.  
  
 `pstrServer`  
 Un pointeur vers une chaîne contenant le nom du serveur.  
  
 `pstrVerb`  
 Un pointeur vers une chaîne qui contient la méthode à utiliser lors de l’envoi de la demande. Peut être **POST**, **HEAD**, ou `GET`.  
  
 dwContext  
 L’identificateur de contexte pour le `CHttpFile` objet. Consultez **remarques** pour plus d’informations sur ce paramètre.  
  
 `pConnection`  
 Un pointeur vers un [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Impossible de créer un `CHttpFile` l’objet directement ; appelez plutôt [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) à la place.  
  
 La valeur par défaut `dwContext` est envoyé par MFC pour le `CHttpFile` à partir de l’objet le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le `CHttpFile` objet. Lorsque vous appelez `CInternetSession::OpenURL` ou `CHttpConnection` pour construire un `CHttpFile` de l’objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
##  <a name="endrequest"></a>  CHttpFile::EndRequest  
 Appelez cette fonction membre pour mettre fin à une demande envoyée à un serveur HTTP avec le [SendRequestEx](#sendrequestex) fonction membre.  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Indicateurs décrivant l’opération. Pour obtenir la liste des indicateurs appropriés, consultez [HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) dans le Kit de développement logiciel Windows.  
  
 `lpBuffIn`  
 Pointeur vers un initialisé [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) qui décrit le tampon d’entrée utilisé pour l’opération.  
  
 `dwContext`  
 L’identificateur de contexte pour le `CHttpFile` opération. Pour plus d’informations sur ce paramètre, consultez la section Notes.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 La valeur par défaut `dwContext` est envoyé par MFC pour le `CHttpFile` à partir de l’objet le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le `CHttpFile` objet. Lorsque vous appelez [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` de l’objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
##  <a name="getfileurl"></a>  CHttpFile::GetFileURL  
 Appelez cette fonction membre pour obtenir le nom du fichier en tant qu’URL HTTP.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui contient une URL faisant référence à la ressource associée à ce fichier.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre uniquement après un appel réussi à [envoi demande](#sendrequest) ou sur un `CHttpFile` objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getobject"></a>  CHttpFile::GetObject  
 Appelez cette fonction membre pour obtenir le nom de l’objet associé à cet `CHttpFile`.  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant le nom de l’objet.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre uniquement après un appel réussi à [envoi demande](#sendrequest) ou sur un `CHttpFile` objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getverb"></a>  CHttpFile::GetVerb  
 Appelez cette fonction membre pour obtenir le verbe HTTP (ou méthode) associé à ce `CHttpFile`.  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant le nom du verbe HTTP (ou de méthode).  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre uniquement après un appel réussi à [envoi demande](#sendrequest) ou sur un `CHttpFile` objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="queryinfo"></a>  CHttpFile::QueryInfo  
 Appelez cette fonction membre pour retourner une réponse ou en-têtes de demande à partir d’une requête HTTP.  
  
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
 `dwInfoLevel`  
 Une combinaison de l’attribut à la requête et les indicateurs suivants qui spécifient le type d’information demandé :  
  
- **HTTP_QUERY_CUSTOM** recherche le nom de l’en-tête et retourne cette valeur dans `lpvBuffer` en sortie. **HTTP_QUERY_CUSTOM** lève une assertion si l’en-tête n’est trouvé.  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS** en général, les en-têtes de réponse des requêtes de l’application, mais une application peut également interroger les en-têtes de demande à l’aide de cet indicateur.  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME** pour ces en-têtes dont la valeur est une chaîne de date/heure, tels que « Last-Modified-Time, » cet indicateur retourne la valeur d’en-tête en tant que Win32 standard [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui ne requiert pas la application pour analyser les données. Si vous utilisez cet indicateur, il pouvez que vous souhaitez utiliser le `SYSTEMTIME` la substitution de la fonction.  
  
- **HTTP_QUERY_FLAG_NUMBER** pour ces en-têtes dont la valeur est un nombre, tels que le code d’état, cet indicateur retourne les données sous la forme d’un nombre 32 bits.  
  
 Consultez le **notes** section pour obtenir la liste des valeurs possibles.  
  
 `lpvBuffer`  
 Pointeur vers la mémoire tampon qui reçoit les informations.  
  
 `lpdwBufferLength`  
 À l’entrée, ce paramètre pointe vers une valeur qui contient la longueur de la mémoire tampon de données, en nombre de caractères ou d’octets. Consultez le **notes** section pour plus d’informations sur ce paramètre.  
  
 `lpdwIndex`  
 Pointeur vers un index de base zéro d’en-tête. Peut être **NULL**. Utilisez cet indicateur pour énumérer plusieurs en-têtes avec le même nom. En entrée, `lpdwIndex` indique l’index de l’en-tête spécifié à retourner. En sortie, `lpdwIndex` indique l’index de l’en-tête suivant. Si l’index suivant est introuvable, **ERROR_HTTP_HEADER_NOT_FOUND** est retourné.  
  
 `str`  
 Une référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui reçoit les informations renvoyées.  
  
 `dwIndex`  
 Valeur d’index. Consultez `lpdwIndex`.  
  
 *pSysTime*  
 Un pointeur vers un Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelé pour déterminer la cause de l’erreur.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre uniquement après un appel réussi à [envoi demande](#sendrequest) ou sur un `CHttpFile` objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Vous pouvez récupérer les types suivants de données à partir de `QueryInfo`:  
  
-   chaînes (par défaut)  
  
- `SYSTEMTIME` (pour « données : « « Expires : » en-têtes, etc.,)  
  
- `DWORD` (pour **STATUS_CODE**, **CONTENT_LENGTH**, etc..)  
  
 Lorsqu’une chaîne est écrite dans la mémoire tampon et la fonction membre réussit, `lpdwBufferLength` contient la longueur de la chaîne de caractères moins 1 de la fin de **NULL** caractère.  
  
 Les possibles `dwInfoLevel` valeurs incluent :  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode  
 Appelez cette fonction membre pour obtenir le code d’état associé à une requête HTTP et le placer dans le `dwStatusCode` paramètre.  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStatusCode`  
 Une référence à un code d’état. Codes d’état indiquent la réussite ou l’échec de l’événement demandé. Consultez **remarques** pour une sélection de descriptions de code d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelé pour déterminer la cause de l’erreur.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre uniquement après un appel réussi à [envoi demande](#sendrequest) ou sur un `CHttpFile` objet créé avec succès par [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Codes d’état HTTP sont répartis en groupes indiquant la réussite ou l’échec de la demande. Les tableaux suivants décrivent les groupes de codes d’état et les codes d’état HTTP courants.  
  
|Regrouper|Signification|  
|-----------|-------------|  
|200-299|Opération réussie|  
|300-399|Information|  
|400-499|Erreur de requête|  
|500-599|Erreur de serveur|  
  
 Codes d’état HTTP courants :  
  
|Code d’état|Signification|  
|-----------------|-------------|  
|200|L’URL est localisée, la transmission suit.|  
|400|Demande inintelligible|  
|404|Demande d’URL introuvable|  
|405|Serveur ne prend pas en charge la méthode demandée|  
|500|Erreur de serveur inconnue|  
|503|Atteint la capacité du serveur|  
  
##  <a name="sendrequest"></a>  CHttpFile::SendRequest  
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
 `pstrHeaders`  
 Un pointeur vers une chaîne contenant le nom des en-têtes à envoyer.  
  
 `dwHeadersLen`  
 La longueur des en-têtes identifié par `pstrHeaders`.  
  
 `lpOptional`  
 Les données facultatives pour envoyer immédiatement après les en-têtes de demande. Ce paramètre est généralement utilisé pour **POST** et **PUT** operations. Cela peut être **NULL** si aucune donnée facultatif à envoyer.  
  
 *dwOptionalLen*  
 Longueur de `lpOptional`.  
  
 `strHeaders`  
 Chaîne contenant le nom des en-têtes pour la requête envoyée.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.  
  
##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx  
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
 *dwTotalLen*  
 Nombre d’octets à envoyer dans la demande.  
  
 `dwFlags`  
 Indicateurs décrivant l’opération. Pour obtenir la liste des indicateurs appropriés, consultez [HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) dans le Kit de développement logiciel Windows.  
  
 `dwContext`  
 L’identificateur de contexte pour le `CHttpFile` opération. Pour plus d’informations sur ce paramètre, consultez la section Notes.  
  
 `lpBuffIn`  
 Pointeur vers un initialisé [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) qui décrit le tampon d’entrée utilisé pour l’opération.  
  
 *lpBuffOut*  
 Pointeur vers un initialisé **INTERNET_BUFFERS** qui décrit la mémoire tampon de sortie utilisé pour l’opération.  
  
### <a name="return-value"></a>Valeur de retour  
 Non nul en cas de réussite. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet à votre application envoyer des données à l’aide de la [écrire](../../mfc/reference/cinternetfile-class.md#write) et [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) méthodes de `CInternetFile`. Vous devez connaître la longueur des données à envoyer avant d’appeler une substitution de cette fonction. La première substitution permet de vous permet de spécifier la longueur des données que vous souhaitez envoyer. La deuxième substitution accepte des pointeurs vers **INTERNET_BUFFERS** structures, ce qui peuvent être utilisés pour décrire la mémoire tampon dans les moindres détails.  
  
 Une fois que le contenu est écrit dans le fichier, appelez [EndRequest](#endrequest) de terminer l’opération.  
  
 La valeur par défaut `dwContext` est envoyé par MFC pour le `CHttpFile` à partir de l’objet le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le `CHttpFile` objet. Lorsque vous appelez [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) ou [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) pour construire un `CHttpFile` de l’objet, vous pouvez remplacer la valeur par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
### <a name="example"></a>Exemple  
 Ce fragment de code envoie le contenu d’une chaîne à une DLL nommée MFCISAPI. DLL sur le serveur hôte local. Tandis que cet exemple utilise un seul appel à `WriteString`, à l’aide de plusieurs appels à envoyer des données dans les blocs est acceptable.  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CInternetFile (classe)](../../mfc/reference/cinternetfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CInternetFile (classe)](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile (classe)](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)
