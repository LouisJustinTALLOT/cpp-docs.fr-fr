---
description: 'En savoir plus sur : classe CInternetSession'
title: CInternetSession (classe)
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: 54ea5369bc0df2821cd9ac527a4ed91cfdc2c19f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339655"
---
# <a name="cinternetsession-class"></a>CInternetSession (classe)

Crée et initialise une ou plusieurs sessions Internet simultanées et, si nécessaire, décrit votre connexion à un serveur proxy.

## <a name="syntax"></a>Syntaxe

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession :: CInternetSession](#cinternetsession)|Construit un objet `CInternetSession`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetSession :: Close](#close)|Ferme la connexion Internet lorsque la session Internet est terminée.|
|[CInternetSession :: EnableStatusCallback](#enablestatuscallback)|Établit une routine de rappel d’État.|
|[CInternetSession :: GetContext](#getcontext)|Ferme la connexion Internet lorsque la session Internet est terminée.|
|[CInternetSession :: GetCookie](#getcookie)|Retourne les cookies pour l’URL spécifiée et toutes ses URL parentes.|
|[CInternetSession :: GetCookieLength](#getcookielength)|Récupère la variable qui spécifie la longueur du cookie stocké dans la mémoire tampon.|
|[CInternetSession :: GetFtpConnection](#getftpconnection)|Ouvre une session FTP avec un serveur. Ouvre une session sur l’utilisateur.|
|[CInternetSession :: GetGopherConnection](#getgopherconnection)|Ouvre un serveur Gopher pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession :: GetHttpConnection](#gethttpconnection)|Ouvre un serveur HTTP pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession :: OnStatusCallback](#onstatuscallback)|Met à jour l’état d’une opération lorsque le rappel d’État est activé.|
|[CInternetSession :: OpenURL](#openurl)|Analyse et ouvre une URL.|
|[CInternetSession :: SetCookie](#setcookie)|Définit un cookie pour l’URL spécifiée.|
|[CInternetSession :: SetOption](#setoption)|Définit les options de la session Internet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession :: Operator HINTERNET](#operator_hinternet)|Handle de la session Internet en cours.|

## <a name="remarks"></a>Notes

Si votre connexion Internet doit être maintenue pendant la durée d’une application, vous pouvez créer un `CInternetSession` membre de la classe [CWinApp](../../mfc/reference/cwinapp-class.md).

Une fois que vous avez établi une session Internet, vous pouvez appeler [OpenURL](#openurl). `CInternetSession` Ensuite, analyse l’URL pour vous en appelant la fonction globale [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Quel que soit son type de protocole, `CInternetSession` interprète l’URL et la gère pour vous. Il peut gérer les demandes de fichiers locaux identifiés avec la ressource URL « file:// ». `OpenURL` retourne un pointeur vers un objet [CStdioFile](../../mfc/reference/cstdiofile-class.md) si le nom que vous lui transmettez est un fichier local.

Si vous ouvrez une URL sur un serveur Internet à l’aide de `OpenURL` , vous pouvez lire les informations du site. Si vous souhaitez effectuer des actions spécifiques au service (par exemple, HTTP, FTP ou Gopher) sur des fichiers situés sur un serveur, vous devez établir la connexion appropriée avec ce serveur. Pour ouvrir un type particulier de connexion directement à un service particulier, utilisez l’une des fonctions membres suivantes :

- [GetGopherConnection](#getgopherconnection) pour ouvrir une connexion à un service Gopher.

- [GetHttpConnection](#gethttpconnection) pour ouvrir une connexion à un service http.

- [GetFtpConnection](#getftpconnection) pour ouvrir une connexion à un service FTP.

[SetOption](#setoption) vous permet de définir les options de requête de votre session, telles que les valeurs de délai d’attente, le nombre de nouvelles tentatives, etc.

`CInternetSession` les fonctions membres [setcookie](#setcookie), [getCookie](#getcookie)et [GetCookieLength](#getcookielength) permettent de gérer une base de données de cookies Win32, à travers laquelle des serveurs et des scripts maintiennent des informations d’État sur la station de travail cliente.

Pour plus d’informations sur les tâches de programmation Internet de base, consultez l’article [première étape d’Internet : wininet](../../mfc/wininet-basics.md). Pour obtenir des informations générales sur l’utilisation des classes MFC WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` lèvera un [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) pour les types de service non pris en charge. Seuls les types de services suivants sont actuellement pris en charge : FTP, HTTP, Gopher et file.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a> CInternetSession :: CInternetSession

Cette fonction membre est appelée lorsqu’un `CInternetSession` objet est créé.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*pstrAgent*<br/>
Pointeur vers une chaîne qui identifie le nom de l’application ou de l’entité appelant les fonctions Internet (par exemple, « Microsoft Internet Browser »). Si *pstrAgent* a la valeur null (valeur par défaut), le Framework appelle la fonction globale [AfxGetAppName](application-information-and-management.md#afxgetappname), qui retourne une chaîne terminée par le caractère null qui contient le nom d’une application. Certains protocoles utilisent cette chaîne pour identifier votre application sur le serveur.

*dwContext*<br/>
Identificateur de contexte de l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession :: OnStatusCallback](#onstatuscallback). La valeur par défaut est 1 ; Toutefois, vous pouvez assigner explicitement un ID de contexte spécifique pour l’opération. L’objet et tout travail qu’il contient sont associés à cet ID de contexte.

*dwAccessType*<br/>
Type d’accès requis. Les éléments suivants sont des valeurs valides, dont l’un peut être fourni :

- INTERNET_OPEN_TYPE_PRECONFIG Connectez-vous à l’aide de paramètres préconfigurés dans le registre. Ce type d’accès est défini par défaut. Pour vous connecter par le biais d’un proxy TIS, définissez *dwAccessType* sur cette valeur ; vous définissez ensuite le registre de manière appropriée.

- INTERNET_OPEN_TYPE_DIRECT se connecter directement à Internet.

- INTERNET_OPEN_TYPE_PROXY se connecter via un proxy CERN.

Pour plus d’informations sur la connexion avec différents types de proxys, consultez [étapes dans une application cliente FTP classique](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Nom du proxy CERN préféré si *dwAccessType* est défini en tant que INTERNET_OPEN_TYPE_PROXY. La valeur par défaut est NULL.

*pstrProxyBypass*<br/>
Pointeur vers une chaîne contenant une liste facultative d’adresses de serveur. Ces adresses peuvent être ignorées lors de l’utilisation de l’accès proxy. Si une valeur NULL est fournie, la liste de contournement est lue à partir du Registre. Ce paramètre est significatif uniquement si *dwAccessType* est défini sur INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Indique diverses options de mise en cache. La valeur par défaut est 0. Les valeurs possibles sont :

- INTERNET_FLAG_DONT_CACHE ne mettez pas en cache les données, que ce soit localement ou sur un serveur de passerelle.

- Les opérations de téléchargement INTERNET_FLAG_OFFLINE sont satisfaites uniquement via le cache persistant. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être associé à l’opérateur **or au niveau du** bit ( **&#124;**).

### <a name="remarks"></a>Notes

`CInternetSession` est la première fonction Internet appelée par une application. Il initialise les structures de données internes et prépare les appels futurs à partir de l’application.

Si aucune connexion Internet ne peut être ouverte, `CInternetSession` lève une [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a> CInternetSession :: Close

Appelez cette fonction membre lorsque votre application a terminé d’utiliser l' `CInternetSession` objet.

```cpp
virtual void Close();
```

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a> CInternetSession :: EnableStatusCallback

Appelez cette fonction membre pour activer le rappel d’État.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie si le rappel est activé ou désactivé. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

Lorsque vous gérez le rappel d’État, vous pouvez fournir l’état de la progression de l’opération (par exemple, la résolution du nom, la connexion au serveur, etc.) dans la barre d’état de l’application. L’affichage de l’état de l’opération est particulièrement souhaitable au cours d’une opération à long terme.

Comme les rappels se produisent pendant le traitement de la requête, l’application doit passer le moins de temps possible dans le rappel pour empêcher la dégradation du débit des données sur le réseau. Par exemple, le fait de placer une boîte de dialogue dans un rappel peut être une opération de longue durée que le serveur met fin à la demande.

Le rappel d’État ne peut pas être supprimé tant que des rappels sont en attente.

Pour gérer les opérations de façon asynchrone, vous devez créer votre propre thread ou utiliser les fonctions WinInet sans MFC.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a> CInternetSession :: GetContext

Appelez cette fonction membre pour obtenir la valeur de contexte pour une session d’application particulière.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur de contexte défini par l’application.

### <a name="remarks"></a>Notes

[OnStatusCallback](#onstatuscallback) utilise l’ID de contexte renvoyé par `GetContext` pour signaler l’état d’une application particulière. Par exemple, lorsqu’un utilisateur active une demande Internet qui implique de retourner des informations d’État, le rappel d’État utilise l’ID de contexte pour signaler l’état de cette demande particulière. Si l’utilisateur active deux requêtes Internet distinctes qui impliquent de retourner des informations d’État, `OnStatusCallback` utilise les identificateurs de contexte pour retourner l’état de leurs demandes correspondantes. Par conséquent, l’identificateur de contexte est utilisé pour toutes les opérations de rappel d’État, et il est associé à la session jusqu’à la fin de la session.

Pour plus d’informations sur les opérations asynchrones, consultez l’article [premières étapes Internet : wininet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a> CInternetSession :: GetCookie

Cette fonction membre implémente le comportement de la fonction Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), comme décrit dans la SDK Windows.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Paramètres

*pstrUrl*<br/>
Pointeur vers une chaîne contenant l’URL.

*pstrCookieName*<br/>
Pointeur vers une chaîne contenant le nom du cookie à obtenir pour l’URL spécifiée.

*pstrCookieData*<br/>
Dans la première surcharge, pointeur vers une chaîne contenant l’adresse de la mémoire tampon qui reçoit les données de cookie. Cette valeur peut être NULL. Dans la deuxième surcharge, référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) pour recevoir les données de cookie.

*dwBufLen*<br/>
Variable spécifiant la taille de la mémoire tampon *pstrCookieData* . Si la fonction est réussie, la mémoire tampon reçoit la quantité de données copiées dans la mémoire tampon *pstrCookieData* . Si *pstrCookieData* a la valeur null, ce paramètre reçoit une valeur qui spécifie la taille de la mémoire tampon nécessaire pour copier toutes les données de cookie.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, ou FALSe dans le cas contraire. Si l’appel échoue, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour déterminer la cause de l’erreur. Les valeurs d’erreur suivantes s’appliquent :

- ERROR_NO_MORE_ITEMS il n’existe aucun cookie pour l’URL spécifiée et tous ses parents.

- ERROR_INSUFFICIENT_BUFFER la valeur passée dans *dwBufLen* est insuffisante pour copier toutes les données de cookie. La valeur retournée dans *dwBufLen* correspond à la taille de la mémoire tampon nécessaire à l’extraction de toutes les données.

### <a name="remarks"></a>Notes

Dans la deuxième surcharge, MFC récupère les données de cookie dans l' `CString` objet fourni.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a> CInternetSession :: GetCookieLength

Appelez cette fonction membre pour récupérer la longueur du cookie stocké dans la mémoire tampon.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Paramètres

*pstrUrl*<br/>
Pointeur vers une chaîne contenant l’URL

*pstrCookieName*<br/>
Pointeur vers une chaîne contenant le nom du cookie.

### <a name="return-value"></a>Valeur renvoyée

Valeur DWORD indiquant la longueur du cookie, stockée dans la mémoire tampon. Zéro si aucun cookie portant le nom indiqué par *pstrCookieName* n’existe.

### <a name="remarks"></a>Notes

Cette valeur est utilisée par [getCookie](#getcookie).

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a> CInternetSession :: GetFtpConnection

Appelez cette fonction membre pour établir une connexion FTP et obtenir un pointeur vers un `CFtpConnection` objet.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Paramètres

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur FTP.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de l’utilisateur qui doit se connecter. Si la valeur est NULL, la valeur par défaut est Anonymous.

*pstrPassword*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont tous les deux null, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* a la valeur null (ou une chaîne vide) mais que *pstrUserName* n’a pas la valeur null, un mot de passe vide est utilisé. Le tableau suivant décrit le comportement des quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Nom d’utilisateur envoyé au serveur FTP | Mot de passe envoyé au serveur FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL ou «»   |   NULL ou «»   |         façon         |      Nom de messagerie de l’utilisateur      |
| Chaîne non NULL |   NULL ou «»   |       *pstrUserName*        |             " "             |
|      NULL       | Chaîne non NULL |            ERROR            |            ERROR            |
| Chaîne non NULL | Chaîne non NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive*<br/>
Spécifie le mode passif ou actif pour cette session FTP. Si la valeur est TRUE, elle définit l’API Win32 `dwFlag` sur INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CFtpConnection](../../mfc/reference/cftpconnection-class.md) . Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

`GetFtpConnection` établit une connexion à un serveur FTP et crée et retourne un pointeur vers un `CFTPConnection` objet. Elle n’effectue aucune opération spécifique sur le serveur. Si vous envisagez de lire ou d’écrire dans des fichiers, par exemple, vous devez effectuer ces opérations comme des étapes distinctes. Consultez les classes [CFtpConnection](../../mfc/reference/cftpconnection-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) pour plus d’informations sur la recherche de fichiers, l’ouverture de fichiers et la lecture ou l’écriture dans des fichiers. Consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour connaître les étapes à suivre pour effectuer des tâches courantes de connexion FTP.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a> CInternetSession :: GetGopherConnection

Appelez cette fonction membre pour établir une nouvelle connexion Gopher et obtenir un pointeur vers un `CGopherConnection` objet.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur Gopher.

*pstrUserName*<br/>
Pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*<br/>
Pointeur vers une chaîne contenant le mot de passe d’accès.

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) . Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

`GetGopherConnection` établit une connexion à un serveur Gopher et crée et retourne un pointeur vers un `CGopherConnection` objet. Elle n’effectue aucune opération spécifique sur le serveur. Si vous envisagez de lire ou d’écrire des données, par exemple, vous devez effectuer ces opérations comme des étapes distinctes. Pour plus d’informations sur la recherche de fichiers, l’ouverture de fichiers et la lecture ou l’écriture dans des fichiers, consultez les classes [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)et [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) . Pour plus d’informations sur la navigation sur un site FTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour connaître les étapes à suivre pour effectuer des tâches courantes de connexion Gopher.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a> CInternetSession :: GetHttpConnection

Appelez cette fonction membre pour établir une connexion HTTP et obtenir un pointeur vers un `CHttpConnection` objet.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Paramètres

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur HTTP.

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*pstrUserName*<br/>
Pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*<br/>
Pointeur vers une chaîne contenant le mot de passe d’accès.

*dwFlags*<br/>
Toute combinaison d' `INTERNET_FLAG_*` indicateurs. Consultez le tableau de la section **Notes** de [CHttpConnection :: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) pour obtenir une description des valeurs *dwFlags* .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CHttpConnection](../../mfc/reference/chttpconnection-class.md) . Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) levé.

### <a name="remarks"></a>Notes

`GetHttpConnection` établit une connexion à un serveur HTTP, puis crée et retourne un pointeur vers un `CHttpConnection` objet. Elle n’effectue aucune opération spécifique sur le serveur. Si vous prévoyez d’interroger un en-tête HTTP, par exemple, vous devez effectuer cette opération en tant qu’étape distincte. Consultez les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) pour plus d’informations sur les opérations que vous pouvez effectuer à l’aide d’une connexion à un serveur http. Pour plus d’informations sur l’exploration d’un site HTTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour connaître les étapes à suivre pour effectuer des tâches de connexion http courantes.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a> CInternetSession :: OnStatusCallback

Cette fonction membre est appelée par l’infrastructure pour mettre à jour l’État lorsque le rappel d’État est activé et qu’une opération est en attente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Paramètres

*dwContext*<br/>
Valeur de contexte fournie par l’application.

*dwInternetStatus*<br/>
Code d’État qui indique la raison pour laquelle le rappel est effectué. Pour obtenir un tableau des valeurs possibles, consultez la **section Notes** .

*lpvStatusInformation*<br/>
Pointeur vers une mémoire tampon qui contient des informations pertinentes sur ce rappel.

*dwStatusInformationLength*<br/>
Taille de *lpvStatusInformation*.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [EnableStatusCallback](#enablestatuscallback) pour tirer parti du rappel d’État.

Le paramètre *dwInternetStatus* indique l’opération en cours d’exécution et détermine ce que sera le contenu de *lpvStatusInformation* . *dwStatusInformationLength* indique la longueur des données incluses dans *lpvStatusInformation*. Les valeurs d’État suivantes pour *dwInternetStatus* sont définies comme suit :

|Valeur|Signification|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Recherche de l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|L’adresse IP du nom contenu dans *lpvStatusInformation* a été trouvée.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Connexion à l’adresse de socket ([sockaddr](/windows/win32/winsock/sockaddr-2)) vers laquelle pointe *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Connexion réussie à l’adresse de socket (SOCKADDR) vers laquelle pointe *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Envoi de la demande d’informations au serveur. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_ REQUEST_SENT|Envoi réussi de la demande d’informations au serveur. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_RECEIVING_RESPONSE|En attente de la réponse du serveur à une demande. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Réception réussie d’une réponse du serveur. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_CLOSING_CONNECTION|Fermeture de la connexion au serveur. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_CONNECTION_CLOSED|La connexion au serveur a été fermée. Le paramètre *lpvStatusInformation* a la valeur null.|
|INTERNET_STATUS_HANDLE_CREATED|Utilisé par la fonction d’API Win32 [internetconnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) pour indiquer qu’elle a créé le nouveau handle. Cela permet à l’application d’appeler la fonction Win32 [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) à partir d’un autre thread si la connexion prend trop de temps. Pour plus d’informations sur ces fonctions, consultez Windows SDKfor.|
|INTERNET_STATUS_HANDLE_CLOSING|Cette valeur de handle a été terminée avec succès.|

Substituez cette fonction membre pour exiger une action avant l’exécution d’une routine de rappel d’État.

> [!NOTE]
> Les rappels d’État ont besoin d’une protection de l’état des threads. Si vous utilisez MFC dans une bibliothèque partagée, ajoutez la ligne suivante au début de votre remplacement :

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Pour plus d’informations sur les opérations asynchrones, consultez l’article [premières étapes Internet : wininet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a> CInternetSession :: OpenURL

Appelez cette fonction membre pour envoyer la demande spécifiée au serveur HTTP et autoriser le client à spécifier des en-têtes RFC822, MIME ou HTTP supplémentaires à envoyer avec la demande.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Paramètres

*pstrURL*<br/>
Pointeur vers le nom de l’URL à laquelle commencer la lecture. Seules les URL commençant par le fichier :, FTP :, Gopher : ou http : sont prises en charge. Déclare si *pstrURL* a la valeur null.

*dwContext*<br/>
Valeur définie par l’application passée avec le handle retourné dans le rappel.

*dwFlags*<br/>
Indicateurs décrivant comment gérer cette connexion. Pour plus d’informations sur les indicateurs valides, consultez la **section Notes** . Les indicateurs valides sont les suivants :

- INTERNET_FLAG_TRANSFER_ASCII la valeur par défaut. Transférez le fichier au format texte ASCII.

- INTERNET_FLAG_TRANSFER_BINARY transférer le fichier en tant que fichier binaire.

- INTERNET_FLAG_RELOAD d’extraire les données du câble, même si elles sont mises en cache localement.

- INTERNET_FLAG_DONT_CACHE ne mettez pas en cache les données, localement ou dans les passerelles.

- INTERNET_FLAG_SECURE cet indicateur est applicable uniquement aux requêtes HTTP. Il demande des transactions sécurisées sur le câble avec protocole SSL ou PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT si possible, réutilisez les connexions existantes sur le serveur pour les nouvelles demandes générées par `OpenUrl` au lieu de créer une nouvelle session pour chaque demande de connexion.

- INTERNET_FLAG_PASSIVE utilisé pour un site FTP. Utilise la sémantique FTP passive. Utilisé avec [CInternetConnection,](../../mfc/reference/cinternetconnection-class.md) de `OpenURL` .

*pstrHeaders*<br/>
Pointeur vers une chaîne contenant les en-têtes à envoyer au serveur HTTP.

*dwHeadersLength*<br/>
Longueur, en caractères, des en-têtes supplémentaires. Si la valeur est-1L et *pstrHeaders* est non null, *pstrHeaders* est supposé être terminé par zéro et la longueur est calculée.

### <a name="return-value"></a>Valeur renvoyée

Retourne un descripteur de fichier pour les services Internet FTP, GOPHER, HTTP et de type de fichier uniquement. Retourne NULL si l’analyse a échoué.

Le pointeur `OpenURL` retourné dépend du type de service de *pstrURL*. Le tableau ci-dessous illustre les pointeurs possibles qui `OpenURL` peuvent être retournés.

|Type d’URL|Retours|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Notes

Le paramètre *dwFlags* doit inclure INTERNET_FLAG_TRANSFER_ASCII ou INTERNET_FLAG_TRANSFER_BINARY, mais pas les deux. Les indicateurs restants peuvent être combinés avec **l’opérateur or** au niveau du bit ( **&#124;**).

`OpenURL`, qui encapsule la fonction Win32 `InternetOpenURL` , autorise uniquement le téléchargement, la récupération et la lecture des données à partir d’un serveur Internet. `OpenURL` n’autorise pas la manipulation de fichiers sur un emplacement distant, donc il ne requiert aucun objet [CInternetConnection,](../../mfc/reference/cinternetconnection-class.md) .

Pour utiliser des fonctions spécifiques à la connexion (c’est-à-dire spécifiques au protocole), telles que l’écriture dans un fichier, vous devez ouvrir une session, puis ouvrir un type particulier de connexion, puis utiliser cette connexion pour ouvrir un fichier dans le mode souhaité. `CInternetConnection`Pour plus d’informations sur les fonctions spécifiques à la connexion, consultez.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a> CInternetSession :: Operator HINTERNET

Utilisez cet opérateur pour obtenir le handle Windows pour la session Internet en cours.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a> CInternetSession :: SetCookie

Définit un cookie pour l’URL spécifiée.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Paramètres

*pstrUrl*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie l’URL pour laquelle le cookie doit être défini.

*pstrCookieName*<br/>
Pointeur vers une chaîne contenant le nom du cookie.

*pstrCookieData*<br/>
Pointeur vers une chaîne contenant les données de chaîne réelles à associer à l’URL.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, ou FALSe dans le cas contraire. Pour recevoir le code d’erreur spécifique, appelez `GetLastError.`

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)de message Win32, comme décrit dans la SDK Windows.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a> CInternetSession :: SetOption

Appelez cette fonction membre pour définir les options de la session Internet.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*Valeur dwOption*<br/>
Option Internet à définir. Pour obtenir la liste des options possibles, consultez [indicateurs d’option](/windows/win32/WinInet/option-flags) dans le SDKfor Windows.

*lpBuffer*<br/>
Mémoire tampon qui contient la valeur de l’option.

*dwBufferLength*<br/>
Longueur de *lpBuffer* ou taille de *dwValue*.

*dwValue*<br/>
Valeur DWORD qui contient la valeur de l’option.

*dwFlags*<br/>
Indique diverses options de mise en cache. La valeur par défaut est 0. Les valeurs possibles sont :

- INTERNET_FLAG_DONT_CACHE ne mettez pas en cache les données, que ce soit localement ou sur un serveur de passerelle.

- Les opérations de téléchargement INTERNET_FLAG_OFFLINE sont satisfaites uniquement via le cache persistant. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être associé à l’opérateur **or au niveau du** bit ( **&#124;**).

### <a name="return-value"></a>Valeur renvoyée

Si l’opération a réussi, la valeur TRUE est retournée. Si une erreur s’est produite, la valeur FALSe est retournée. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection, classe](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
