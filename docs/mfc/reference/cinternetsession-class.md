---
title: Classe de CInternetSession | Documents Microsoft
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
ms.openlocfilehash: 51fa89f17a546c0b1aec6e1ed53a320f57660687
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322405"
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
|[CInternetSession::CInternetSession](#cinternetsession)|Construit un objet `CInternetSession`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetSession::Close](#close)|Ferme la connexion Internet lors de la fin de la session Internet.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Établit une routine de rappel d’état.|
|[CInternetSession::GetContext](#getcontext)|Ferme la connexion Internet lors de la fin de la session Internet.|
|[CInternetSession::GetCookie](#getcookie)|Retourne les cookies pour l’URL spécifiée et tous les parents de son URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Récupère la variable en spécifiant la longueur du cookie stocké dans la mémoire tampon.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Ouvre une session FTP avec un serveur. Connecte l’utilisateur.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Ouvre un serveur gopher pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Ouvre un serveur HTTP pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Met à jour l’état d’une opération lorsque le rappel d’état est activé.|
|[CInternetSession::OpenURL](#openurl)|Analyse et ouvre une URL.|
|[CInternetSession::SetCookie](#setcookie)|Définit un cookie pour l’URL spécifiée.|
|[CInternetSession::SetOption](#setoption)|Définit les options pour la session Internet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Handle vers la session Internet en cours.|

## <a name="remarks"></a>Notes

Si votre connexion Internet doit être conservée pendant la durée d’une application, vous pouvez créer un `CInternetSession` membre de la classe [CWinApp](../../mfc/reference/cwinapp-class.md).

Une fois que vous avez établi une session Internet, vous pouvez appeler [OpenURL](#openurl). `CInternetSession` analyse ensuite l’URL pour vous en appelant la fonction globale [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Indépendamment de son type de protocole, `CInternetSession` interprète l’URL et le gère pour vous. Il peut gérer les demandes pour les fichiers locaux, identifiés par la ressource d’URL « file:// ». `OpenURL` Retourne un pointeur vers un [CStdioFile](../../mfc/reference/cstdiofile-class.md) objet si le nom que vous passez est un fichier local.

Si vous ouvrez sur un serveur Internet en utilisant une URL `OpenURL`, vous pouvez lire les informations à partir du site. Si vous souhaitez effectuer des actions de service spécifique (par exemple, HTTP, FTP ou gopher) sur les fichiers situés sur un serveur, vous devez établir la connexion appropriée à ce serveur. Pour ouvrir un type particulier de connexion directement à un service particulier, utilisez une des fonctions membres suivantes :

- [GetGopherConnection](#getgopherconnection) pour ouvrir une connexion à un service gopher.

- [GetHttpConnection](#gethttpconnection) pour ouvrir une connexion à un service HTTP.

- [GetFtpConnection](#getftpconnection) pour ouvrir une connexion à un service FTP.

[SetOption](#setoption) vous permet de définir les options de requête de votre session, telles que les valeurs de délai d’attente, le nombre de nouvelles tentatives, et ainsi de suite.

`CInternetSession` fonctions membres [SetCookie](#setcookie), [GetCookie](#getcookie), et [GetCookieLength](#getcookielength) permettent de gérer une base de données de cookie Win32, par le biais duquel les serveurs et les scripts de mettre à jour informations d’état sur la station de travail client.

Pour plus d’informations sur les tâches de programmation Internet base, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md). Pour obtenir des informations générales sur l’utilisation des classes WinInet MFC, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` lève une [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) pour les types de service non pris en charge. Charge actuellement les seuls les types de service suivants : FTP, HTTP, gopher et fichier.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)  
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

*pstrAgent*  
Un pointeur vers une chaîne qui identifie le nom de l’application ou d’une entité appelant les fonctions d’Internet (par exemple, « navigateur Microsoft Internet »). Si *pstrAgent* est **NULL** (la valeur par défaut), le framework appelle la fonction globale [AfxGetAppName](application-information-and-management.md#afxgetappname), qui retourne une chaîne se terminant par null qui contient l’application nom. Certains protocoles utilisent cette chaîne pour identifier votre application sur le serveur.

*dwContext*  
L’identificateur de contexte pour l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](#onstatuscallback). La valeur par défaut est définie sur 1 ; Toutefois, vous pouvez affecter explicitement un ID de contexte spécifiques pour l’opération. L’objet et tout travail qu’elle fournit à associer à cet ID de contexte.

*dwAccessType*  
Le type d’accès requis. Les valeurs valides, un seul d'entre eux peut être fourni sont les suivantes :

- `INTERNET_OPEN_TYPE_PRECONFIG` Se connecter à l’aide de paramètres prédéfinis dans le Registre. Ce type d’accès est défini comme la valeur par défaut. Pour vous connecter via un proxy TIS, définissez *dwAccessType* à cette valeur ; vous puis configurez le Registre correctement.

- `INTERNET_OPEN_TYPE_DIRECT` Se connecter directement à Internet.

- `INTERNET_OPEN_TYPE_PROXY` Se connecter via un proxy CERN.

Pour plus d’informations sur la connexion avec différents types de proxy, consultez [des étapes dans une Application cliente de type FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*  
Le nom du proxy CERN préféré si *dwAccessType* est défini comme `INTERNET_OPEN_TYPE_PROXY`. La valeur par défaut est **NULL**.

*pstrProxyBypass*  
Un pointeur vers une chaîne contenant une liste facultative d’adresses du serveur. Ces adresses peuvent être ignorés lors de l’utilisation d’un accès au proxy. Si un **NULL** valeur est fournie, la liste de contournement lira à partir du Registre. Ce paramètre n’est significatif uniquement si *dwAccessType* a la valeur `INTERNET_OPEN_TYPE_PROXY`.

*dwFlags*  
Indique les différentes options de mise en cache. La valeur par défaut est définie sur 0. Les valeurs possibles sont les suivantes :

- `INTERNET_FLAG_DONT_CACHE` Ne mettez pas en cache les données, localement ou dans des serveurs de passerelle.

- `INTERNET_FLAG_OFFLINE` Les opérations de téléchargement sont satisfaites par le biais du cache persistant uniquement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être combiné avec l’opérateur de bits `OR` ( **&#124;**) (opérateur).

### <a name="remarks"></a>Notes

`CInternetSession` la première fonction Internet est appelée par une application. Il initialise les structures de données internes et les prépare pour les appels ultérieurs à partir de l’application.

Si aucune connexion Internet ne peut être ouverts, `CInternetSession` lève une [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Exemple

Consultez l’exemple de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Appelez cette fonction membre lorsque votre application a terminé la `CInternetSession` objet.

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

*bActivez*  
Spécifie si le rappel est activé ou désactivé. La valeur par défaut est **TRUE**.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

Lors du traitement de rappel d’état, vous pouvez fournir l’état sur la progression de l’opération (par exemple, la résolution de nom, la connexion au serveur et ainsi de suite) dans la barre d’état de l’application. Affichage de l’état de l’opération est particulièrement appropriée lors d’une opération à long terme.

Étant donné que les rappels se produisent pendant le traitement de la demande, l’application doit consacrer moins de temps que possible dans le rappel pour empêcher une dégradation du débit de données sur le réseau. Par exemple, la mise en place d’une boîte de dialogue dans un rappel peut être une opération longue que le serveur met fin à la demande.

Le rappel d’état ne peut pas être supprimé tant que tous les rappels sont en attente.

Pour gérer toutes les opérations de façon asynchrone, vous devez créer votre propre thread ou utiliser les fonctions WinInet sans MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Appelez cette fonction membre pour obtenir la valeur de contexte pour une session d’application particulier.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur de retour

Le contexte défini par l’application identificateur.

### <a name="remarks"></a>Notes

[OnStatusCallback](#onstatuscallback) utilise l’ID de contexte retournée par `GetContext` pour signaler l’état d’une application particulière. Par exemple, lorsqu’un utilisateur lance une demande Internet qui implique le retour d’informations d’état, le rappel d’état utilise l’ID de contexte pour signaler l’état sur cette requête particulière. Si l’utilisateur Active deux que les deux impliquent retournant des informations d’état, les demandes Internet `OnStatusCallback` utilise les identificateurs de contexte pour retourner l’état concernant leurs demandes correspondants. Par conséquent, l’identificateur de contexte est utilisé pour toutes les opérations de rappel d’état, et il est associé à la session jusqu'à ce que la session est terminée.

Pour plus d’informations sur les opérations asynchrones, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Cette fonction membre implémente le comportement de la fonction Win32 [InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710), comme décrit dans le Kit de développement logiciel Windows.

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

*pstrUrl*  
Un pointeur vers une chaîne contenant l’URL.

*pstrCookieName*  
Un pointeur vers une chaîne contenant le nom du cookie à obtenir pour l’URL spécifiée.

*pstrCookieData*  
Dans la première surcharge, un pointeur vers une chaîne contenant l’adresse de la mémoire tampon qui reçoit les données de cookie. Cette valeur peut être **NULL**. Dans la seconde surcharge, une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet pour recevoir les données de cookie.

*dwBufLen*  
La variable en spécifiant la taille de la *pstrCookieData* mémoire tampon. Si la fonction réussit, la mémoire tampon reçoit la quantité de données copiée dans le *pstrCookieData* mémoire tampon. Si *pstrCookieData* est **NULL**, ce paramètre reçoit une valeur qui spécifie la taille de la mémoire tampon nécessaire de copier toutes les données de cookie.

### <a name="return-value"></a>Valeur de retour

Retourne **TRUE** en cas de réussite, ou **FALSE** dans le cas contraire. Si l’appel échoue, appelez la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) pour déterminer la cause de l’erreur. Les valeurs d’erreur suivantes s’appliquent :

- `ERROR_NO_MORE_ITEMS` Il n’existe aucun cookie pour l’URL spécifiée et tous ses parents.

- `ERROR_INSUFFICIENT_BUFFER` La valeur transmise dans *dwBufLen* est insuffisant pour copier toutes les données de cookie. La valeur retournée dans *dwBufLen* est la taille de la mémoire tampon nécessaire pour obtenir toutes les données.

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

*pstrUrl*  
Un pointeur vers une chaîne contenant l’URL

*pstrCookieName*  
Un pointeur vers une chaîne contenant le nom du cookie.

### <a name="return-value"></a>Valeur de retour

A `DWORD` valeur indiquant la longueur du cookie, stockée dans la mémoire tampon. Zéro si aucun cookie portant le nom indiqué par *pstrCookieName* existe.

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

*pstrServer*  
Un pointeur vers une chaîne contenant le nom du serveur FTP.

*pstrUserName*  
Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur de se connecter. Si **NULL**, la valeur par défaut est anonyme.

*pstrPassword*  
Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux *pstrPassword* et *pstrUserName* sont **NULL**, le mot de passe anonyme par défaut est le nom d’utilisateur par courrier électronique. Si *pstrPassword* est **NULL** (ou une chaîne vide), mais *pstrUserName* n’est pas **NULL**, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|**NULL** ou « »|**NULL** ou « »|« anonyme »|Nom de l’utilisateur par courrier électronique|
|Non-**NULL** chaîne|**NULL** ou « »|*pstrUserName*|" "|
|**NULL**|Non-**NULL** chaîne|**ERREUR**|**ERREUR**||
|Non-**NULL** chaîne|Non-**NULL** chaîne|*pstrUserName*|*pstrPassword*|

*%nPort*  
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive*  
Spécifie le mode passif ou actif pour cette session FTP. Si la valeur **TRUE**, il définit l’API Win32 `dwFlag` à `INTERNET_FLAG_PASSIVE`.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CFtpConnection](../../mfc/reference/cftpconnection-class.md) objet. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetFtpConnection` se connecte à un serveur FTP, crée et retourne un pointeur vers un `CFTPConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous souhaitez lire ou écrire dans des fichiers, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [CFtpConnection](../../mfc/reference/cftpconnection-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) pour plus d’informations sur la recherche de fichiers, ouvrir des fichiers et lire ou écrire dans des fichiers. Consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion FTP.

### <a name="example"></a>Exemple

Consultez l’exemple de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Appelez cette fonction membre pour établir une connexion gopher et obtenir un pointeur vers un `CGopherConnection` objet.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pstrServer*  
Un pointeur vers une chaîne contenant le nom du serveur gopher.

*pstrUserName*  
Un pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*  
Un pointeur vers une chaîne contenant le mot de passe.

*%nPort*  
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetGopherConnection` se connecte à un serveur gopher, crée et retourne un pointeur vers un `CGopherConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous souhaitez lire ou écrire des données, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), et [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) pour plus d’informations sur la recherche de fichiers, ouvrir des fichiers et lire ou écrire dans des fichiers. Pour plus d’informations sur la navigation d’un site FTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion gopher.

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

*pstrServer*  
Un pointeur vers une chaîne contenant le nom du serveur HTTP.

*%nPort*  
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*pstrUserName*  
Un pointeur vers une chaîne contenant le nom d’utilisateur.

*pstrPassword*  
Un pointeur vers une chaîne contenant le mot de passe.

*dwFlags*  
N’importe quelle combinaison de le `INTERNET_FLAG_*` indicateurs. Consultez le tableau dans le **remarques** section de [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) pour obtenir une description de `dwFlags` valeurs.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) objet. Si l’appel échoue, déterminer la cause du problème en examinant la levée [CInternetException](../../mfc/reference/cinternetexception-class.md) objet.

### <a name="remarks"></a>Notes

`GetHttpConnection` se connecte à un serveur HTTP, crée et retourne un pointeur vers un `CHttpConnection` objet. Il n’effectue pas une opération spécifique sur le serveur. Par exemple, si vous prévoyez d’interroger un en-tête HTTP, vous devez effectuer cette opération comme une étape distincte. Consultez les classes [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) pour plus d’informations sur les opérations que vous pouvez effectuer à l’aide d’une connexion à un serveur HTTP. Pour plus d’informations sur la navigation d’un site HTTP, consultez la fonction membre [OpenURL](#openurl). Consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes de l’exécution des tâches courantes de connexion HTTP.

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

*dwContext*  
La valeur de contexte fournie par l’application.

*dwInternetStatus*  
Un code d’état qui indique la raison pour laquelle le rappel est effectué. Consultez **remarques** pour une table de valeurs possibles.

*lpvStatusInformation*  
Pointeur vers une mémoire tampon contenant les informations relatives à ce rappel.

*dwStatusInformationLength*  
La taille de *lpvStatusInformation*.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [EnableStatusCallback](#enablestatuscallback) pour tirer parti de rappel d’état.

Le *dwInternetStatus* paramètre indique que l’opération en cours d’exécution et détermine la nature du contenu de *lpvStatusInformation* sera. *dwStatusInformationLength* indique la longueur des données incluses dans *lpvStatusInformation*. Les valeurs de l’état suivant pour *dwInternetStatus* sont définies comme suit :

|Value|Signification|
|-----------|-------------|
|`INTERNET_STATUS_RESOLVING_NAME`|Recherche de l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|`INTERNET_STATUS_NAME_RESOLVED`|Réussi à trouver l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|Connexion à l’adresse de socket ([SOCKADDR](../../mfc/reference/sockaddr-structure.md)) vers lequel pointe *lpvStatusInformation*.|
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|Correctement connecté à l’adresse de socket (`SOCKADDR`) vers lequel pointe *lpvStatusInformation*.|
|`INTERNET_STATUS_SENDING_REQUEST`|Envoi de la demande d’informations sur le serveur. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_ REQUEST_SENT`|Envoyé la demande d’informations sur le serveur. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_RECEIVING_RESPONSE`|En attente pour le serveur à répondre à une demande. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_RESPONSE_RECEIVED`|Réception d’une réponse à partir du serveur. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_CLOSING_CONNECTION`|Ferme la connexion au serveur. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_CONNECTION_CLOSED`|Correctement fermé la connexion au serveur. Le *lpvStatusInformation* paramètre est **NULL**.|
|`INTERNET_STATUS_HANDLE_CREATED`|Utilisé par la fonction API Win32 [InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363) pour indiquer qu’il a créé le nouveau handle. Cela permet à la fonction application Win32 [InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350) à partir d’un autre thread si la connexion est trop longue. Consultez le SDKfor Windows plus d’informations sur ces fonctions.|
|`INTERNET_STATUS_HANDLE_CLOSING`|Cette valeur du handle a été arrêtée correctement.|

Remplacez cette fonction membre pour demander une action avant l’exécution d’une routine de rappel d’état.

> [!NOTE]
> Rappels d’état besoin d’une protection de l’état du thread. Si vous utilisez MFC dans une bibliothèque partagée, ajoutez la ligne suivante au début de votre remplacement :

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

*pstrURL*  
Pointeur vers le nom de l’URL de la lecture doit commencer. Seules les URL commençant par le fichier :, ftp :, gopher :, ou http : sont pris en charge. Déclare si *pstrURL* est **NULL**.

*dwContext*  
Une valeur définie par l’application passé avec le handle retourné dans le rappel.

*dwFlags*  
Les indicateurs qui décrivent comment gérer cette connexion. Consultez **remarques** pour plus d’informations sur les indicateurs valides. Les indicateurs valides sont :

- `INTERNET_FLAG_TRANSFER_ASCII` La valeur par défaut. Transférez le fichier au format texte ASCII.

- `INTERNET_FLAG_TRANSFER_BINARY` Transférez le fichier dans un fichier binaire.

- `INTERNET_FLAG_RELOAD` Obtenir les données provenant du câble, même s’il est mis en cache localement.

- `INTERNET_FLAG_DONT_CACHE` Ne mettez pas en cache les données, localement ou dans les passerelles.

- `INTERNET_FLAG_SECURE` Cet indicateur est applicable aux demandes HTTP uniquement. Il demande la sécurité des transactions sur le câble avec Secure Sockets Layer ou pourcentage.

- `INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT` Si possible, de réutiliser les connexions existantes sur le serveur pour les nouvelles requêtes générées par `OpenUrl` au lieu de créer une nouvelle session pour chaque demande de connexion.

- `INTERNET_FLAG_PASSIVE` Utilisé pour un site FTP. Utilise FTP passif. Utilisé avec [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de `OpenURL`.

*pstrHeaders*  
Un pointeur vers une chaîne contenant les en-têtes à envoyer au serveur HTTP.

*dwHeadersLength*  
La longueur, en caractères, d’en-têtes supplémentaires. S’il s’agit-1 L et *pstrHeaders* est non -**NULL**, puis *pstrHeaders* est supposé zéro arrêtée et la longueur est calculée.

### <a name="return-value"></a>Valeur de retour

Retourne un handle de fichier pour les services FTP, GOPHER, HTTP et type de fichier Internet uniquement. Retourne **NULL** si l’analyse a échoué.

Le pointeur qui `OpenURL` retourne dépend *pstrURL*du type de service. Le tableau ci-dessous illustre les pointeurs possibles `OpenURL` peut retourner.

|Type d’URL|Returns (Retours)|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|Gopher://|`CGopherFile*`|
|FTP : / /|`CInternetFile*`|

### <a name="remarks"></a>Notes

Le paramètre *dwFlags* doit inclure `INTERNET_FLAG_TRANSFER_ASCII` ou `INTERNET_FLAG_TRANSFER_BINARY`, mais pas les deux. Les indicateurs restants peuvent être combinées avec l’opérateur de bits `OR` (opérateur) ( **&#124;**).

`OpenURL`, qui encapsule la fonction Win32 `InternetOpenURL`, permet le téléchargement uniquement, la récupération et la lecture des données à partir d’un serveur Internet. `OpenURL` ne permet d’aucune manipulation de fichier sur un emplacement distant, afin qu’il ne nécessite aucune [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objet.

Pour utiliser spécifique à la connexion (autrement dit, spécifiques au protocole) des fonctions, telles que l’écriture dans un fichier, vous devez ouvrir une session, puis ouvrez un type particulier de connexion, puis utiliser cette connexion pour ouvrir un fichier dans le mode souhaité. Consultez `CInternetConnection` pour plus d’informations sur les fonctions spécifiques à la connexion.

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

Cet opérateur permet d’obtenir le handle Windows pour la session Internet.

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

*pstrUrl*  
Un pointeur vers une chaîne se terminant par null qui spécifie l’URL pour lequel le cookie doit être défini.

*pstrCookieName*  
Un pointeur vers une chaîne contenant le nom du cookie.

*pstrCookieData*  
Un pointeur vers une chaîne contenant les données de chaîne réelle à associer à l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne **TRUE** en cas de réussite, ou **FALSE** dans le cas contraire. Pour obtenir le code d’erreur spécifique, appelez **GetLastError.**

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107), comme décrit dans le Kit de développement logiciel Windows.

## <a name="setoption"></a>  CInternetSession::SetOption

Appelez cette fonction membre pour définir les options pour la session Internet.

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

*dwOption*  
L’option Internet à définir. Consultez [indicateurs d’Option](http://msdn.microsoft.com/library/windows/desktop/aa385328) dans la liste des options possibles de SDKfor Windows.

*lpBuffer*  
Une mémoire tampon qui contient le paramètre d’option.

*dwBufferLength*  
La longueur de *lpBuffer* ou la taille de *dwValue*.

*dwValue*  
Un `DWORD` qui contient le paramètre d’option.

*dwFlags*  
Indique les différentes options de mise en cache. La valeur par défaut est définie sur 0. Les valeurs possibles sont les suivantes :

- `INTERNET_FLAG_DONT_CACHE` Ne mettez pas en cache les données, localement ou dans des serveurs de passerelle.

- `INTERNET_FLAG_OFFLINE` Les opérations de téléchargement sont satisfaites par le biais du cache persistant uniquement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Cet indicateur peut être combiné avec l’opérateur de bits `OR` ( **&#124;**) (opérateur).

### <a name="return-value"></a>Valeur de retour

Si l’opération a réussi, la valeur **TRUE** est retourné. Si une erreur s’est produite, une valeur de **FALSE** est retourné. Si l’appel échoue, la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelé pour déterminer la cause de l’erreur.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)  
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)  
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)  
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)  
[CFtpConnection, classe](../../mfc/reference/cftpconnection-class.md)  
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)  
