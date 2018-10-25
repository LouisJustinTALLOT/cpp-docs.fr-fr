---
title: CInternetSession, classe | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14b5b68f33bd6d16f791784ceb24bf22a2806fa9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055032"
---
# <a name="cinternetsession-class"></a>CInternetSession, classe

Crée et initialise une ou plusieurs sessions Internet simultanées et, si nécessaire, décrit votre connexion à un serveur proxy.

## <a name="syntax"></a>Syntaxe

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Construit un objet `CInternetSession`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetSession::Close](#close)|Ferme la connexion Internet lors de la fin de la session Internet.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Établit une routine de rappel d’état.|
|[CInternetSession::GetContext](#getcontext)|Ferme la connexion Internet lors de la fin de la session Internet.|
|[CInternetSession::GetCookie](#getcookie)|Retourne les cookies pour l’URL spécifiée et tous les parents de son URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Récupère la variable en spécifiant la longueur du cookie stocké dans la mémoire tampon.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Ouvre une session FTP avec un serveur. L’utilisateur se connecte.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Ouvre un serveur gopher pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Ouvre un serveur HTTP pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Met à jour l’état d’une opération lorsque le rappel d’état est activé.|
|[CInternetSession::OpenURL](#openurl)|Analyse et ouvre une URL.|
|[CInternetSession::SetCookie](#setcookie)|Définit un cookie pour l’URL spécifiée.|
|[CInternetSession::SetOption](#setoption)|Définit les options pour la session Internet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Handle vers la session Internet actuel.|

## <a name="remarks"></a>Notes

Si votre connexion Internet doit être maintenue pendant la durée d’une application, vous pouvez créer un `CInternetSession` membre de la classe [CWinApp](../../mfc/reference/cwinapp-class.md).

Une fois que vous avez établi une session Internet, vous pouvez appeler [OpenURL](#openurl). `CInternetSession` analyse ensuite l’URL pour vous en appelant la fonction globale [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Quel que soit son type de protocole, `CInternetSession` interprète l’URL et il gère pour vous. Il peut gérer les demandes pour les fichiers locaux identifiés avec la ressource d’URL « file:// ». `OpenURL` Retourne un pointeur vers un [CStdioFile](../../mfc/reference/cstdiofile-class.md) objet si le nom que vous transmettez est un fichier local.

Si vous ouvrez une URL sur un serveur Internet à l’aide `OpenURL`, vous pouvez lire des informations à partir du site. Si vous souhaitez effectuer des actions de service spécifique (par exemple, HTTP, FTP ou gopher) sur les fichiers situés sur un serveur, vous devez établir la connexion appropriée avec ce serveur. Pour ouvrir un type particulier de connexion directe à un service particulier, utilisez une des fonctions membres suivantes :

- [GetGopherConnection](#getgopherconnection) pour ouvrir une connexion à un service gopher.

- [GetHttpConnection](#gethttpconnection) pour ouvrir une connexion à un service HTTP.

- [GetFtpConnection](#getftpconnection) pour ouvrir une connexion à un service FTP.

[SetOption](#setoption) vous permet de définir les options de requête de votre session, telles que les valeurs de délai d’attente, nombre de nouvelles tentatives, et ainsi de suite.

`CInternetSession` fonctions membres [SetCookie](#setcookie), [GetCookie](#getcookie), et [GetCookieLength](#getcookielength) fournissent les moyens de gérer une base de données de cookie Win32, par le biais duquel les scripts et les serveurs de tenir à jour informations d’état sur la station de travail client.

Pour plus d’informations sur les tâches de programmation de base Internet, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md). Pour obtenir des informations générales sur l’utilisation des classes WinInet MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` lève une [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) pour les types de service non pris en charge. Seuls les types de service suivants ne sont actuellement gérées : FTP, HTTP, gopher et fichier.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

Cette fonction membre est appelée quand un `CInternetSession` objet est créé.

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
Un pointeur vers une chaîne qui identifie le nom de l’application ou d’une entité appelant les fonctions d’Internet (par exemple, « navigateur Microsoft Internet »). Si *pstrAgent* a la valeur NULL (valeur par défaut), le framework appelle la fonction globale [AfxGetAppName](application-information-and-management.md#afxgetappname), qui retourne une chaîne se terminant par null qui contient un nom de l’application. Certains protocoles utilisent cette chaîne pour identifier votre application sur le serveur.

*dwContext*<br/>
L’identificateur de contexte pour l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](#onstatuscallback). La valeur par défaut est défini sur 1 ; Toutefois, vous pouvez affecter explicitement un ID de contexte spécifique pour l’opération. L’objet et n’importe quel travail qu’elle effectue sera associés à cet ID de contexte.

*dwAccessType*<br/>
Le type d’accès requis. Les valeurs valides, seul qui peut-être être fournie sont les suivantes :

- INTERNET_OPEN_TYPE_PRECONFIG se connecter avec préconfigurée dans le Registre. Ce type d’accès est défini comme la valeur par défaut. Pour vous connecter via un proxy TIS, définir *dwAccessType* à cette valeur ; vous ensuite définir le Registre en conséquence.

- INTERNET_OPEN_TYPE_DIRECT se connecter directement à Internet.

- INTERNET_OPEN_TYPE_PROXY se connecter via un proxy CERN.

Pour plus d’informations sur la connexion avec différents types de proxy, consultez [étapes dans une Application de Client FTP typique](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Le nom du proxy CERN préféré si *dwAccessType* est défini comme INTERNET_OPEN_TYPE_PROXY. La valeur par défaut est NULL.

*pstrProxyBypass*<br/>
Un pointeur vers une chaîne contenant une liste facultative d’adresses du serveur. Ces adresses peuvent être ignorés lors de l’utilisation de l’accès proxy. Si une valeur NULL est fournie, la liste de contournement lira à partir du Registre. Ce paramètre n’est significatif uniquement si *dwAccessType* INTERNET_OPEN_TYPE_PROXY a la valeur.

*dwFlags*<br/>
Indique les différentes options de mise en cache. La valeur par défaut est définie sur 0. Les valeurs possibles sont les suivantes :

- Faire INTERNET_FLAG_DONT_CACHE met pas en cache les données, localement ou dans des serveurs de passerelle.

- Télécharger INTERNET_FLAG_OFFLINE les opérations sont satisfaites via le cache persistant uniquement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être combiné avec l’opérateur de bits **ou** ( **&#124;**) opérateur.

### <a name="remarks"></a>Notes

`CInternetSession` la première fonction Internet est appelée par une application. Il initialise les structures de données internes et le prépare pour les appels suivants à partir de l’application.

Si aucune connexion Internet ne peut être ouverts, `CInternetSession` lève une [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Exemple

Consultez l’exemple de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Appelez cette fonction membre lorsque votre application a terminé d’utiliser le `CInternetSession` objet.

```cpp
virtual void Close();
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

Appelez cette fonction membre pour activer le rappel d’état.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActivez*<br/>
Spécifie si le rappel est activé ou désactivé. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminer la cause de l’échec en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

Lors du traitement de rappel d’état, vous pouvez fournir l’état sur la progression de l’opération (par exemple, la résolution de nom, la connexion au serveur et ainsi de suite) dans la barre d’état de l’application. Affichage de l’état de l’opération est particulièrement souhaitable pendant une opération à long terme.

Étant donné que les rappels se produisent pendant le traitement de la demande, l’application doit passer que peu de temps que possible dans le rappel pour éviter la dégradation du débit de données pour le réseau. Par exemple, la mise en place d’une boîte de dialogue dans un rappel peut être une opération longue que le serveur met fin à la requête.

Le rappel d’état ne peut pas être supprimé tant que tous les rappels sont en attente.

Pour gérer les opérations de façon asynchrone, vous devez créer votre propre thread ou utiliser les fonctions de WinInet sans MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Appelez cette fonction membre pour obtenir la valeur de contexte pour une session d’application particulier.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur de retour

Le contexte défini par l’application identificateur.

### <a name="remarks"></a>Notes

[OnStatusCallback](#onstatuscallback) utilise l’ID de contexte retourné par `GetContext` pour signaler l’état d’une application particulière. Par exemple, lorsqu’un utilisateur lance une demande Internet qui consiste à retourner des informations d’état, le rappel d’état utilise l’ID de contexte pour signaler l’état lors de cette requête particulière. Si l’utilisateur Active deux distinct que ces deux options impliquent retournant des informations d’état, les demandes Internet `OnStatusCallback` utilise les identificateurs de contexte pour obtenir l’état concernant leurs demandes correspondants. Par conséquent, l’identificateur de contexte est utilisé pour toutes les opérations de rappel d’état, et il est associé à la session jusqu'à ce que la session soit terminée.

Pour plus d’informations sur les opérations asynchrones, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Cette fonction membre implémente le comportement de la fonction Win32 [InternetGetCookie](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea), comme décrit dans le SDK Windows.

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
Un pointeur vers une chaîne contenant l’URL.

*pstrCookieName*<br/>
Un pointeur vers une chaîne contenant le nom du cookie à obtenir pour l’URL spécifiée.

*pstrCookieData*<br/>
Dans la première surcharge, un pointeur vers une chaîne contenant l’adresse de la mémoire tampon qui reçoit les données de cookie. Cette valeur peut être NULL. Dans la seconde surcharge, une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet devant recevoir les données de cookie.

*dwBufLen*<br/>
La variable en spécifiant la taille de la *pstrCookieData* mémoire tampon. Si la fonction réussit, la mémoire tampon reçoit la quantité de données copiée dans le *pstrCookieData* mémoire tampon. Si *pstrCookieData* est NULL, ce paramètre reçoit une valeur qui spécifie la taille de la mémoire tampon nécessaire pour copier toutes les données de cookie.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE en cas de réussite, ou FALSE dans le cas contraire. Si l’appel échoue, appelez la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) pour déterminer la cause de l’erreur. Les valeurs d’erreur suivants s’appliquent :

- ERROR_NO_MORE_ITEMS il n’existe aucun cookie pour l’URL spécifiée et tous ses parents.

- ERROR_INSUFFICIENT_BUFFER la valeur passée dans *dwBufLen* est insuffisant pour copier toutes les données de cookie. La valeur retournée dans *dwBufLen* est la taille de la mémoire tampon nécessaire pour obtenir toutes les données.

### <a name="remarks"></a>Notes

Dans la seconde surcharge, MFC récupère les données de cookie dans fourni `CString` objet.

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

Appelez cette fonction membre pour obtenir la longueur du cookie stocké dans la mémoire tampon.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Paramètres

*pstrUrl*<br/>
Un pointeur vers une chaîne contenant l’URL

*pstrCookieName*<br/>
Un pointeur vers une chaîne contenant le nom du cookie.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui indique la longueur du cookie, stockées dans la mémoire tampon. Zéro si aucun cookie portant le nom indiqué par *pstrCookieName* existe.

### <a name="remarks"></a>Notes

Cette valeur est utilisée par [GetCookie](#getcookie).

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

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
Un pointeur vers une chaîne contenant le nom du serveur FTP.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur pour vous connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword*<br/>
Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux *pstrPassword* et *pstrUserName* ont la valeur NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide), mais *pstrUserName* n’est pas NULL, un mot de passe vide est utilisée. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou « »|NULL ou « »|« anonyme »|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou « »|*pstrUserName*|" "|
|NULL|Chaîne non NULL|ERREUR|ERREUR||
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*%nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive*<br/>
Spécifie le mode actif ou passif pour cette session FTP. Si la valeur est TRUE, elle définit l’API Win32 `dwFlag` à INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CFtpConnection](../../mfc/reference/cftpconnection-class.md) objet. Si l’appel échoue, déterminer la cause de l’échec en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetFtpConnection` se connecte à un serveur FTP et crée et retourne un pointeur vers un `CFTPConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous avez l’intention de lire ou écrire dans des fichiers, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [CFtpConnection](../../mfc/reference/cftpconnection-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) pour plus d’informations sur la recherche de fichiers, ouvrir des fichiers et lecture ou écriture dans des fichiers. Consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion FTP.

### <a name="example"></a>Exemple

Consultez l’exemple de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Appelez cette fonction membre pour établir une nouvelle connexion gopher et obtenir un pointeur vers un `CGopherConnection` objet.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pstrServer*<br/>
Un pointeur vers une chaîne contenant le nom du serveur gopher.

*pstrUserName*<br/>
Un pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*<br/>
Un pointeur vers une chaîne contenant le mot de passe d’accès.

*%nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet. Si l’appel échoue, déterminer la cause de l’échec en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetGopherConnection` se connecte à un serveur gopher et crée et retourne un pointeur vers un `CGopherConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous avez l’intention de lire ou écrire des données, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), et [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) pour plus d’informations sur la recherche de fichiers, ouvrir des fichiers et lecture ou écriture dans des fichiers. Pour plus d’informations sur la navigation d’un site FTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion gopher.

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

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
Un pointeur vers une chaîne contenant le nom du serveur HTTP.

*%nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*pstrUserName*<br/>
Un pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*<br/>
Un pointeur vers une chaîne contenant le mot de passe d’accès.

*dwFlags*<br/>
N’importe quelle combinaison de le `INTERNET_FLAG_*` indicateurs. Consultez le tableau dans le **remarques** section de [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) pour obtenir une description de *dwFlags* valeurs.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) objet. Si l’appel échoue, déterminer la cause de l’échec en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetHttpConnection` se connecte à un serveur HTTP et crée et retourne un pointeur vers un `CHttpConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous prévoyez d’interroger un en-tête HTTP, vous devez effectuer cette opération comme une étape distincte. Consultez les classes [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) pour plus d’informations sur les opérations que vous pouvez effectuer à l’aide d’une connexion à un serveur HTTP. Pour plus d’informations sur la navigation d’un site HTTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion HTTP.

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

Cette fonction membre est appelée par l’infrastructure pour mettre à jour l’état lorsque le rappel d’état est activé et une opération est en attente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Paramètres

*dwContext*<br/>
La valeur de contexte fournie par l’application.

*dwInternetStatus*<br/>
Un code d’état qui indique pourquoi le rappel est en cours. Consultez **remarques** pour une table de valeurs possibles.

*lpvStatusInformation*<br/>
Pointeur vers une mémoire tampon contenant les informations pertinentes pour ce rappel.

*dwStatusInformationLength*<br/>
La taille de *lpvStatusInformation*.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [EnableStatusCallback](#enablestatuscallback) pour tirer parti de rappel d’état.

Le *dwInternetStatus* paramètre indique l’opération en cours d’exécution et détermine la nature du contenu de *lpvStatusInformation* sera. *dwStatusInformationLength* indique la longueur des données incluses dans *lpvStatusInformation*. Valeurs de l’état suivant pour *dwInternetStatus* sont définis comme suit :

|Value|Signification|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Recherche de l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Réussi à trouver l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Connexion à l’adresse de socket ([SOCKADDR](../../mfc/reference/sockaddr-structure.md)) vers lequel pointe *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Connecté à l’adresse de socket (SOCKADDR) vers lequel pointé *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Envoi de la demande d’informations sur le serveur. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Correctement envoyé la demande d’informations sur le serveur. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Attend que le serveur à répondre à une demande. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Réception d’une réponse à partir du serveur. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Fermeture de la connexion au serveur. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Fermé avec succès la connexion au serveur. Le *lpvStatusInformation* paramètre est NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Utilisé par la fonction API Win32 [InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta) pour indiquer qu’il a créé le nouveau handle. Cela permet à la fonction application Win32 [InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle) à partir d’un autre thread si la connexion est trop longue. Consultez le SDKfor Windows plus d’informations sur ces fonctions.|
|INTERNET_STATUS_HANDLE_CLOSING|Cette valeur de handle a été arrêtée correctement.|

Remplacez cette fonction membre pour exiger une action avant l’exécution d’une routine de rappel d’état.

> [!NOTE]
> Rappels d’état requièrent une protection de l’état du thread. Si vous utilisez MFC dans une bibliothèque partagée, ajoutez la ligne suivante au début du remplacement :

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Pour plus d’informations sur les opérations asynchrones, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>  CInternetSession::OpenURL

Appeler ce membre de fonction pour envoyer la demande spécifiée pour le serveur HTTP et permettre au client de spécifier RFC822 supplémentaires, MIME ou en-têtes HTTP à envoyer avec la demande.

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
Un pointeur vers le nom de l’URL pour commencer la lecture. Seules les URL commençant par le fichier :, ftp :, gopher :, ou http : sont pris en charge. Déclare si *pstrURL* a la valeur NULL.

*dwContext*<br/>
Une valeur définie par l’application passé avec le handle retourné dans le rappel.

*dwFlags*<br/>
Indicateurs décrivant comment gérer cette connexion. Consultez **remarques** pour plus d’informations sur les indicateurs valides. Les indicateurs valides sont :

- INTERNET_FLAG_TRANSFER_ASCII la valeur par défaut. Transférez le fichier en tant que texte ASCII.

- INTERNET_FLAG_TRANSFER_BINARY transférer le fichier comme un fichier binaire.

- INTERNET_FLAG_RELOAD obtenir les données depuis le câble, même s’il est mis en cache localement.

- Faire INTERNET_FLAG_DONT_CACHE met pas en cache les données, localement ou dans les passerelles.

- INTERNET_FLAG_SECURE cet indicateur s’applique aux requêtes HTTP uniquement. Il demande des transactions sécurisées sur le câble avec (Secure Sockets Layer) ou de pourcentage.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT si possible, réutiliser les connexions existantes sur le serveur pour les nouvelles requêtes générées par `OpenUrl` au lieu de créer une nouvelle session pour chaque demande de connexion.

- INTERNET_FLAG_PASSIVE utilisé pour un site FTP. Utilise FTP passif. Utilisé avec [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de `OpenURL`.

*pstrHeaders*<br/>
Un pointeur vers une chaîne contenant les en-têtes à envoyer au serveur HTTP.

*dwHeadersLength*<br/>
La longueur, en caractères, des en-têtes supplémentaires. S’il s’agit-1 L et *pstrHeaders* n’est pas NULL, puis *pstrHeaders* est supposé être égal à zéro s’est arrêté et la longueur est calculée.

### <a name="return-value"></a>Valeur de retour

Retourne un handle de fichier pour les services Internet de type de fichier, HTTP, FTP et GOPHER uniquement. Retourne la valeur NULL si l’analyse a échoué.

Le pointeur qui `OpenURL` retourne dépend *pstrURL*du type de service. Le tableau ci-dessous illustre les pointeurs possible `OpenURL` peut retourner.

|Type d’URL|Returns (Retours)|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|Gopher://|`CGopherFile*`|
|FTP : / /|`CInternetFile*`|

### <a name="remarks"></a>Notes

Le paramètre *dwFlags* doit inclure INTERNET_FLAG_TRANSFER_ASCII ou INTERNET_FLAG_TRANSFER_BINARY, mais pas les deux. Les indicateurs restants peuvent être combinés avec l’opérateur de bits **ou** opérateur ( **&#124;**).

`OpenURL`, qui encapsule la fonction Win32 `InternetOpenURL`, permet de téléchargement uniquement, récupérer et lire les données à partir d’un serveur Internet. `OpenURL` n’autorisant aucune manipulation de fichier sur un emplacement distant, il ne nécessite aucune [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objet.

Pour utiliser spécifique à la connexion (autrement dit, spécifiques au protocole) fonctions, telles que l’écriture dans un fichier, vous devez ouvrir une session, puis ouvrez un type particulier de connexion, puis utiliser cette connexion pour ouvrir un fichier dans le mode souhaité. Consultez `CInternetConnection` pour plus d’informations sur les fonctions spécifiques à la connexion.

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

Utilisez cet opérateur pour obtenir le handle de Windows pour la session Internet actuelle.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

Définit un cookie pour l’URL spécifiée.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Paramètres

*pstrUrl*<br/>
Un pointeur vers une chaîne se terminant par null qui spécifie l’URL pour lequel le cookie doit être défini.

*pstrCookieName*<br/>
Un pointeur vers une chaîne contenant le nom du cookie.

*pstrCookieData*<br/>
Un pointeur vers une chaîne contenant les données de chaîne réelle à associer à l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE en cas de réussite, ou FALSE dans le cas contraire. Pour obtenir le code d’erreur spécifique, appelez `GetLastError.`

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea), comme décrit dans le SDK Windows.

## <a name="setoption"></a>  CInternetSession::SetOption

Appelez cette fonction membre pour définir des options pour la session Internet.

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

*dwOption*<br/>
L’option Internet à définir. Consultez [indicateurs d’Option](/windows/desktop/WinInet/option-flags) dans la liste des options possibles de SDKfor Windows.

*lpBuffer*<br/>
Une mémoire tampon qui contient le paramètre d’option.

*dwBufferLength*<br/>
La longueur de *lpBuffer* ou la taille de *dwValue*.

*dwValue*<br/>
Valeur DWORD qui contient le paramètre d’option.

*dwFlags*<br/>
Indique les différentes options de mise en cache. La valeur par défaut est définie sur 0. Les valeurs possibles sont les suivantes :

- Faire INTERNET_FLAG_DONT_CACHE met pas en cache les données, localement ou dans des serveurs de passerelle.

- Télécharger INTERNET_FLAG_OFFLINE les opérations sont satisfaites via le cache persistant uniquement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être combiné avec l’opérateur de bits **ou** ( **&#124;**) opérateur.

### <a name="return-value"></a>Valeur de retour

Si l’opération a réussi, la valeur TRUE est retournée. Si une erreur s’est produite, la valeur FALSE est retournée. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection, classe](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
