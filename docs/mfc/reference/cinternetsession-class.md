---
title: CInternetSession, classe
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
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372377"
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
|[CInternetSession::Fermer](#close)|Ferme la connexion Internet lorsque la session Internet est terminée.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Établit une routine de rappel de statut.|
|[CInternetSession::GetContext](#getcontext)|Ferme la connexion Internet lorsque la session Internet est terminée.|
|[CInternetSession::GetCookie](#getcookie)|Renvoie les cookies pour l’URL spécifiée et toutes ses URL parentes.|
|[CInternetSession::GetCookieLength](#getcookielength)|Récupère la variable spécifiant la longueur du cookie stocké dans le tampon.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Ouvre une session FTP avec un serveur. Connexions sur l’utilisateur.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Ouvre un serveur gopher pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Ouvre un serveur HTTP pour une application qui tente d’ouvrir une connexion.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Mise à jour de l’état d’une opération lorsque le rappel d’état est activé.|
|[CInternetSession::OpenURL](#openurl)|Parses et ouvre une URL.|
|[CInternetSession::SetCookie](#setcookie)|Définit un cookie pour l’URL spécifiée.|
|[CInternetSession::SetOption](#setoption)|Définit les options pour la session Internet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetSession::opérateur HINTERNET](#operator_hinternet)|Une poignée pour la session Internet en cours.|

## <a name="remarks"></a>Notes

Si votre connexion Internet doit être maintenue pendant toute la `CInternetSession` durée d’une application, vous pouvez créer un membre de la classe [CWinApp](../../mfc/reference/cwinapp-class.md).

Une fois que vous avez établi une session Internet, vous pouvez appeler [OpenURL](#openurl). `CInternetSession`puis analyse l’URL pour vous en appelant la fonction globale [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Quel que soit `CInternetSession` son type de protocole, interprète l’URL et la gère pour vous. Il peut traiter les demandes de fichiers locaux identifiés avec la ressource URL "file://". `OpenURL`retournera un pointeur à un objet [CStdioFile](../../mfc/reference/cstdiofile-class.md) si le nom que vous passez, il s’agit d’un fichier local.

Si vous ouvrez une URL `OpenURL`sur un serveur Internet à l’aide, vous pouvez lire les informations du site. Si vous souhaitez effectuer des actions spécifiques au service (par exemple, HTTP, FTP ou gopher) sur des fichiers situés sur un serveur, vous devez établir la connexion appropriée avec ce serveur. Pour ouvrir un type particulier de connexion directement à un service particulier, utilisez l’une des fonctions suivantes :

- [GetGopherConnection](#getgopherconnection) pour ouvrir une connexion à un service de gopher.

- [GetHttpConnection](#gethttpconnection) pour ouvrir une connexion à un service HTTP.

- [GetFtpConnection](#getftpconnection) pour ouvrir une connexion à un service FTP.

[SetOption](#setoption) vous permet de définir les options de requête de votre session, telles que les valeurs de temps d’attente, le nombre de retries, et ainsi de suite.

`CInternetSession`fonctions [membres SetCookie](#setcookie), [GetCookie](#getcookie), et [GetCookieLength](#getcookielength) fournissent les moyens de gérer une base de données de cookies Win32, grâce à laquelle les serveurs et les scripts de maintenir les informations de l’état sur le poste de travail client.

Pour plus d’informations sur les tâches de programmation Internet de base, voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md). Pour plus d’informations générales sur l’utilisation des classes MFC WinInet, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`lancera un [AfxThrowNotSup supportedException](exception-processing.md#afxthrownotsupportedexception) pour les types de services non pris en service. Seuls les types de service suivants sont actuellement pris en charge : FTP, HTTP, gopher et fichier.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>CInternetSession::CInternetSession

Cette fonction de membre `CInternetSession` est appelée lorsqu’un objet est créé.

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
Un pointeur vers une chaîne qui identifie le nom de l’application ou de l’entité appelant les fonctions Internet (par exemple, "Microsoft Internet Browser"). Si *pstrAgent* est NULL (la valeur par défaut), le cadre appelle la fonction globale [AfxGetAppName](application-information-and-management.md#afxgetappname), qui renvoie une chaîne non terminée contenant le nom d’une application. Certains protocoles utilisent cette chaîne pour identifier votre application sur le serveur.

*dwContexte*<br/>
L’identifiant de contexte pour l’opération. *dwContext* identifie les informations sur l’état de l’opération retournées par [CInternetSession::OnStatusCallback](#onstatuscallback). La valeur par défaut est réglée à 1; toutefois, vous pouvez affecter explicitement une pièce d’identité de contexte spécifique pour l’opération. L’objet et tout travail qu’il fait sera associé à cette pièce d’identité contextuelle.

*dwAccessType dwAccessType*<br/>
Le type d’accès requis. Voici des valeurs valides, dont l’une peut être fournie :

- INTERNET_OPEN_TYPE_PRECONFIG Connectez-vous à l’aide de paramètres préconfigurés dans le registre. Ce type d’accès est défini comme par défaut. Pour vous connecter par l’intermédiaire d’un proxy TIS, *définissez dwAccessType* à cette valeur; vous définissez ensuite le registre de façon appropriée.

- INTERNET_OPEN_TYPE_DIRECT Connectez-vous directement à Internet.

- INTERNET_OPEN_TYPE_PROXY Connectez-vous par l’intermédiaire d’un proxy du CERN.

Pour plus d’informations sur la connexion avec différents types de procurations, voir [Steps in a Typical FTP Client Application](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName (en)*<br/>
Le nom du proxy préféré du CERN si *dwAccessType* est défini comme INTERNET_OPEN_TYPE_PROXY. La valeur par défaut est NULL.

*pstrProxyBypass*<br/>
Un pointeur à une chaîne contenant une liste facultative des adresses serveur. Ces adresses peuvent être contournées lors de l’utilisation de l’accès proxy. Si une valeur NULL est fournie, la liste de contournement sera lue à partir du registre. Ce paramètre n’est significatif que si *dwAccessType* est réglé pour INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Indique diverses options de mise en cache. La valeur par défaut est réglée à 0. Les valeurs possibles sont :

- INTERNET_FLAG_DONT_CACHE Ne pas mettre en cache les données, que ce soit localement ou dans les serveurs de passerelle.

- INTERNET_FLAG_OFFLINE Les opérations de téléchargement sont satisfaites par le cache persistant seulement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Ce drapeau peut être combiné avec l’opérateur **bitwise OU** ( **&#124;). **

### <a name="remarks"></a>Notes

`CInternetSession`est la première fonction Internet appelée par une application. Il initialise les structures de données internes et se prépare aux appels futurs de l’application.

Si aucune connexion Internet `CInternetSession` ne peut être ouverte, lance un [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Exemple

Voir l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a>CInternetSession::Fermer

Appelez cette fonction de membre lorsque `CInternetSession` votre application a terminé l’utilisation de l’objet.

```cpp
virtual void Close();
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Appelez cette fonction de membre pour activer le rappel de statut.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Précise si le rappel est activé ou désactivé. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

Lors de la gestion de rappel de statut, vous pouvez fournir l’état sur l’avancement de l’opération (comme la résolution du nom, la connexion au serveur, et ainsi de suite) dans la barre d’état de l’application. L’affichage de l’état de fonctionnement est particulièrement souhaitable lors d’une opération à long terme.

Étant donné que les rappels se produisent pendant le traitement de la demande, l’application devrait passer le moins de temps possible dans le rappel pour empêcher la dégradation du débit de données au réseau. Par exemple, la mise en place d’une boîte de dialogue dans un rappel peut être une opération si longue que le serveur met fin à la demande.

Le rappel d’état ne peut pas être supprimé tant que des rappels sont en attente.

Pour gérer toutes les opérations de manière asynchrone, vous devez soit créer votre propre thread, soit utiliser les fonctions WinInet sans MFC.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>CInternetSession::GetContext

Appelez cette fonction de membre pour obtenir la valeur contextuelle d’une session d’application particulière.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur de retour

Le contexte défini par l’application Identifier.

### <a name="remarks"></a>Notes

[OnStatusCallback](#onstatuscallback) utilise le contexte `GetContext` ID retourné pour signaler l’état d’une application particulière. Par exemple, lorsqu’un utilisateur active une demande Internet qui consiste à renvoyer des informations d’état, le rappel d’état utilise l’ID contextuelle pour signaler l’état de cette demande particulière. Si l’utilisateur active deux demandes Internet distinctes `OnStatusCallback` qui impliquent toutes deux le retour des informations d’état, utilise les identifiants contextuelles pour retourner l’état de leurs demandes correspondantes. Par conséquent, l’identifiant de contexte est utilisé pour toutes les opérations de rappel d’état, et il est associé à la session jusqu’à la fin de la session.

Pour plus d’informations sur les opérations asynchrones, voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>CInternetSession::GetCookie

Cette fonction membre implémente le comportement de la fonction Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), tel que décrit dans le SDK Windows.

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

*pstrUrl (pstrUrl)*<br/>
Un pointeur à une chaîne contenant l’URL.

*pstrCookieName*<br/>
Un pointeur à une chaîne contenant le nom du cookie pour obtenir pour l’URL spécifiée.

*pstrCookieData (en)*<br/>
Dans la première surcharge, un pointeur à une chaîne contenant l’adresse du tampon qui reçoit les données de cookie. Cette valeur peut être NULL. Dans la deuxième surcharge, une référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) pour recevoir les données de cookie.

*dwBufLen*<br/>
La variable spécifiant la taille du tampon *pstrCookieData.* Si la fonction réussit, le tampon reçoit la quantité de données copiées sur le tampon *pstrCookieData.* Si *pstrCookieData* est NULL, ce paramètre reçoit une valeur qui spécifie la taille du tampon nécessaire pour copier toutes les données de cookies.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI en cas de succès, ou FALSE autrement. Si l’appel échoue, appelez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour déterminer la cause de l’erreur. Les valeurs d’erreur suivantes s’appliquent :

- ERROR_NO_MORE_ITEMS Il n’y a pas de cookie pour l’URL spécifiée et tous ses parents.

- ERROR_INSUFFICIENT_BUFFER La valeur passée en *dwBufLen* est insuffisante pour copier toutes les données de cookies. La valeur retournée dans *dwBufLen* est la taille du tampon nécessaire pour obtenir toutes les données.

### <a name="remarks"></a>Notes

Dans la deuxième surcharge, MFC récupère les `CString` données de cookie dans l’objet fourni.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>CInternetSession::GetCookieLength

Appelez cette fonction de membre pour obtenir la longueur du cookie stocké dans le tampon.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Paramètres

*pstrUrl (pstrUrl)*<br/>
Un pointeur à une chaîne contenant l’URL

*pstrCookieName*<br/>
Un pointeur à une chaîne contenant le nom du cookie.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD indiquant la longueur du cookie, stockée dans le tampon. Zéro si aucun cookie avec le nom indiqué par *pstrCookieName* existe.

### <a name="remarks"></a>Notes

Cette valeur est utilisée par [GetCookie](#getcookie).

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Appelez cette fonction de membre pour établir une `CFtpConnection` connexion FTP et obtenir un pointeur à un objet.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Paramètres

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur FTP.

*pstrUserName (en)*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom de l’utilisateur à se connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne non terminée qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide) mais *pstrUserName n’est* pas NULL, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement des quatre réglages possibles de *pstrUserName* et *pstrPassword*:

| *pstrUserName (en)*  | *pstrPassword (pstrPassword)*  | Nom d’utilisateur envoyé au serveur FTP | Mot de passe envoyé au serveur FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL ou "   |   NULL ou "   |         "anonyme"         |      Nom de l’e-mail de l’utilisateur      |
| Chaîne non-NULL |   NULL ou "   |       *pstrUserName (en)*        |             " "             |
|      NULL       | Chaîne non-NULL |            ERROR            |            ERROR            |
| Chaîne non-NULL | Chaîne non-NULL |       *pstrUserName (en)*        |       *pstrPassword (pstrPassword)*        |

*nPort (en)*<br/>
Un numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive (en)*<br/>
Spécifie le mode passif ou actif pour cette session FTP. S’il est défini à TRUE, `dwFlag` il définit l’API Win32 à INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Valeur de retour

Un pointeur pour un objet [CFtpConnection.](../../mfc/reference/cftpconnection-class.md) Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

`GetFtpConnection`se connecte à un serveur FTP, et `CFTPConnection` crée et renvoie un pointeur à un objet. Il n’effectue aucune opération spécifique sur le serveur. Si vous avez l’intention de lire ou d’écrire dans des fichiers, par exemple, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [CFtpConnection](../../mfc/reference/cftpconnection-class.md) et [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) pour obtenir des informations sur la recherche de fichiers, l’ouverture de fichiers et la lecture ou l’écriture de fichiers. Voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes dans l’exécution des tâches de connexion FTP commune.

### <a name="example"></a>Exemple

Voir l’exemple pour [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Appelez cette fonction de membre pour établir une nouvelle `CGopherConnection` connexion de gopher et obtenir un pointeur à un objet.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur gopher.

*pstrUserName (en)*<br/>
Un pointeur à une chaîne contenant le nom d’utilisateur.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne contenant le mot de passe d’accès.

*nPort (en)*<br/>
Un numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md) Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

`GetGopherConnection`se connecte à un serveur gopher, et `CGopherConnection` crée et renvoie un pointeur à un objet. Il n’effectue aucune opération spécifique sur le serveur. Si vous avez l’intention de lire ou d’écrire des données, par exemple, vous devez effectuer ces opérations en tant qu’étapes distinctes. Consultez les classes [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)et [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) pour obtenir des informations sur la recherche de fichiers, l’ouverture de fichiers et la lecture ou l’écriture de fichiers. Pour plus d’informations sur la navigation d’un site FTP, consultez la fonction membre [OpenURL](#openurl). Voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes dans l’exécution des tâches de connexion gopher commune.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Appelez cette fonction de membre pour établir une `CHttpConnection` connexion HTTP et obtenir un pointeur à un objet.

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

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur HTTP.

*nPort (en)*<br/>
Un numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*pstrUserName (en)*<br/>
Un pointeur à une chaîne contenant le nom d’utilisateur.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne contenant le mot de passe d’accès.

*dwflags*<br/>
Toute combinaison `INTERNET_FLAG_*` des drapeaux. Voir le tableau dans la section **Remarques** de [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) pour une description des valeurs *dwFlags.*

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CHttpConnection.](../../mfc/reference/chttpconnection-class.md) Si l’appel échoue, déterminez la cause de l’échec en examinant l’objet [CInternetException](../../mfc/reference/cinternetexception-class.md) lancé.

### <a name="remarks"></a>Notes

`GetHttpConnection`se connecte à un serveur HTTP, et `CHttpConnection` crée et renvoie un pointeur à un objet. Il n’effectue aucune opération spécifique sur le serveur. Si vous avez l’intention de poser une question d’en-tête HTTP, par exemple, vous devez effectuer cette opération comme une étape distincte. Consultez les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) pour obtenir des informations sur les opérations que vous pouvez effectuer en utilisant une connexion à un serveur HTTP. Pour plus d’informations sur la navigation d’un site HTTP, consultez la fonction membre [OpenURL](#openurl). Voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md) pour les étapes dans l’exécution des tâches de connexion HTTP commune.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Cette fonction de membre est appelée par le cadre pour mettre à jour l’état lorsque le rappel de statut est activé et qu’une opération est en attente.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Paramètres

*dwContexte*<br/>
La valeur contextuelle fournie par l’application.

*dwInternetStatus*<br/>
Un code d’état qui indique pourquoi le rappel est effectué. Voir **Remarques** pour une table de valeurs possibles.

*lpvStatusInformation*<br/>
Un pointeur vers un tampon contenant des informations pertinentes à ce rappel.

*dwStatusInformationLength*<br/>
La taille de *lpvStatusInformation*.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [EnableStatusCallback](#enablestatuscallback) pour profiter du rappel de statut.

Le *paramètre dwInternetStatus* indique l’opération effectuée et détermine le contenu de *lpvStatusInformation.* *dwStatusInformationLength* indique la longueur des données incluses dans *lpvStatusInformation*. Les valeurs de statut suivantes pour *dwInternetStatus* sont définies comme suit :

|Value|Signification|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Rechercher l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|A trouvé avec succès l’adresse IP du nom contenu dans *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Connexion à l’adresse de prise ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) pointé par *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Connexion avec succès à l’adresse de prise (SOCKADDR) pointée vers *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Envoi de la demande d’informations au serveur. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_ REQUEST_SENT|A envoyé avec succès la demande d’informations au serveur. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|En attendant que le serveur réponde à une demande. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|A reçu avec succès une réponse du serveur. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Fermer la connexion au serveur. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|A conclu avec succès la connexion au serveur. Le *paramètre lpvStatusInformation* est NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Utilisé par la fonction Win32 API [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) pour indiquer qu’il a créé la nouvelle poignée. Cela permet à l’application d’appeler la fonction Win32 [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) à partir d’un autre thread si la connexion prend trop de temps. Consultez le Windows SDKfor pour plus d’informations sur ces fonctions.|
|INTERNET_STATUS_HANDLE_CLOSING|A terminé avec succès cette valeur de poignée.|

Remplacer cette fonction de membre pour exiger une certaine action avant qu’une routine de rappel de statut soit effectuée.

> [!NOTE]
> Les rappels de statut ont besoin d’une protection de thread-état. Si vous utilisez MFC dans une bibliothèque partagée, ajoutez la ligne suivante au début de votre remplacement :

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Pour plus d’informations sur les opérations asynchrones, voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>CInternetSession::OpenURL

Appelez cette fonction membre pour envoyer la demande spécifiée au serveur HTTP et permettre au client de spécifier des en-têtes supplémentaires de RFC822, MIME ou HTTP à envoyer avec la demande.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Paramètres

*pstrURL (pstrURL)*<br/>
Un pointeur sur le nom de l’URL pour commencer la lecture. Seules les URL commençant par le fichier :, ftp :, gopher : ou http:// : are supported. Affirme si *pstrURL* est NULL.

*dwContexte*<br/>
Une valeur définie par l’application a été adoptée avec la poignée retournée en rappel.

*dwFlags*<br/>
Les drapeaux décrivant comment gérer cette connexion. Voir **Remarques** pour plus d’informations sur les drapeaux valides. Les drapeaux valides sont les :

- INTERNET_FLAG_TRANSFER_ASCII La valeur par défaut. Transférer le fichier sous forme de texte ASCII.

- INTERNET_FLAG_TRANSFER_BINARY Transférer le fichier sous forme de fichier binaire.

- INTERNET_FLAG_RELOAD Obtenez les données du fil même si elles sont mises en cache localement.

- INTERNET_FLAG_DONT_CACHE Ne cachez pas les données, que ce soit localement ou dans les passerelles.

- INTERNET_FLAG_SECURE Ce drapeau s’applique uniquement aux demandes DE HTTP. Il demande des transactions sécurisées sur le fil avec Secure Sockets Layer ou PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Si possible, réutilisez les connexions existantes `OpenUrl` au serveur pour les nouvelles demandes générées au lieu de créer une nouvelle session pour chaque demande de connexion.

- INTERNET_FLAG_PASSIVE utilisé pour un site FTP. Utilise la sémantique passive FTP. Utilisé avec [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) de `OpenURL`.

*pstrHeaders*<br/>
Un pointeur à une chaîne contenant les en-têtes à envoyer au serveur HTTP.

*dwHeadersLength*<br/>
La longueur, en caractères, des en-têtes supplémentaires. Si c’est -1L et *pstrHeaders* est non-NULL, puis *pstrHeaders* est supposé être zéro terminé et la longueur est calculée.

### <a name="return-value"></a>Valeur de retour

Retourne une poignée de fichiers pour les services Internet de type FTP, GOPHER, HTTP et FILE uniquement. Retourne NULL si l’analyse a échoué.

Le pointeur qui `OpenURL` revient dépend du type de service de *pstrURL.* Le tableau ci-dessous illustre `OpenURL` les indications possibles peuvent revenir.

|Type d’URL|Retours|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Notes

Le paramètre *dwFlags* doit inclure INTERNET_FLAG_TRANSFER_ASCII ou INTERNET_FLAG_TRANSFER_BINARY, mais pas les deux. Les drapeaux restants peuvent être combinés avec l’opérateur **BITwise OR** ( **&#124;**).

`OpenURL`, qui enveloppe la fonction `InternetOpenURL`Win32 , permet uniquement de télécharger, récupérer et lire les données à partir d’un serveur Internet. `OpenURL`ne permet aucune manipulation de fichier sur un emplacement distant, de sorte qu’il ne nécessite pas [d’objet CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

Pour utiliser des fonctions spécifiques à la connexion (c’est-à-dire spécifiques au protocole), telles que l’écriture sur un fichier, vous devez ouvrir une session, puis ouvrir un type particulier de connexion, puis utiliser cette connexion pour ouvrir un fichier dans le mode désiré. Voir `CInternetConnection` pour plus d’informations sur les fonctions spécifiques à la connexion.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetSession::opérateur HINTERNET

Utilisez cet opérateur pour obtenir la poignée Windows pour la session Internet en cours.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>CInternetSession::SetCookie

Définit un cookie pour l’URL spécifiée.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Paramètres

*pstrUrl (pstrUrl)*<br/>
Un pointeur à une chaîne non terminée qui spécifie l’URL pour laquelle le cookie doit être réglé.

*pstrCookieName*<br/>
Un pointeur à une chaîne contenant le nom du cookie.

*pstrCookieData (en)*<br/>
Un pointeur à une chaîne contenant les données de chaîne réelles pour s’associer à l’URL.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI en cas de succès, ou FALSE autrement. Pour obtenir le code d’erreur spécifique, appelez`GetLastError.`

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), tel que décrit dans le Windows SDK.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>CInternetSession::SetOption

Appelez cette fonction de membre pour définir des options pour la session Internet.

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
L’option Internet à définir. Voir [Les indicateurs d’option](/windows/win32/WinInet/option-flags) dans windows SDKfor une liste des options possibles.

*lpBuffer*<br/>
Un tampon qui contient le paramètre d’option.

*dwBufferLength*<br/>
La longueur de *lpBuffer* ou la taille de *dwValue*.

*dwValue dwValue*<br/>
Un DWORD qui contient le paramètre d’option.

*dwFlags*<br/>
Indique diverses options de mise en cache. La valeur par défaut est réglée à 0. Les valeurs possibles sont :

- INTERNET_FLAG_DONT_CACHE Ne pas mettre en cache les données, que ce soit localement ou dans les serveurs de passerelle.

- INTERNET_FLAG_OFFLINE Les opérations de téléchargement sont satisfaites par le cache persistant seulement. Si l’élément n’existe pas dans le cache, un code d’erreur approprié est retourné. Ce drapeau peut être combiné avec l’opérateur **bitwise OU** ( **&#124;). **

### <a name="return-value"></a>Valeur de retour

Si l’opération a été couronnée de succès, une valeur de TRUE est retournée. En cas d’erreur, une valeur de FALSE est retournée. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[Classe CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
