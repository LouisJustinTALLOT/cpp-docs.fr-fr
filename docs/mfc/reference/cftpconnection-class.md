---
title: CFtpConnection, classe
ms.date: 08/29/2019
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: 4ad2262b17208dd634b59f5df4d6e60c300bb3c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832735"
---
# <a name="cftpconnection-class"></a>CFtpConnection, classe

Gère votre connexion FTP à un serveur Internet et permet la manipulation directe des répertoires et des fichiers sur ce serveur.

## <a name="syntax"></a>Syntaxe

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFtpConnection :: CFtpConnection](#cftpconnection)|Construit un objet `CFtpConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFtpConnection :: Command](#command)|Envoie une commande directement à un serveur FTP.|
|[CFtpConnection :: CreateDirectory](#createdirectory)|Crée un répertoire sur le serveur.|
|[CFtpConnection :: GetCurrentDirectory](#getcurrentdirectory)|Obtient le répertoire actif pour cette connexion.|
|[CFtpConnection :: GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtient le répertoire actif pour cette connexion en tant qu’URL.|
|[CFtpConnection :: GetFile](#getfile)|Obtient un fichier à partir du serveur connecté|
|[CFtpConnection :: OpenFile](#openfile)|Ouvre un fichier sur le serveur connecté.|
|[CFtpConnection ::P utFile](#putfile)|Place un fichier sur le serveur.|
|[CFtpConnection :: Remove](#remove)|Supprime un fichier du serveur.|
|[CFtpConnection :: RemoveDirectory](#removedirectory)|Supprime le répertoire spécifié du serveur.|
|[CFtpConnection :: Rename](#rename)|Renomme un fichier sur le serveur.|
|[CFtpConnection :: SetCurrentDirectory](#setcurrentdirectory)|Définit le répertoire FTP actuel.|

## <a name="remarks"></a>Notes

FTP est l’un des trois services Internet reconnus par les classes WinInet MFC.

Pour communiquer avec un serveur Internet FTP, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis créer un `CFtpConnection` objet. Vous ne créez jamais un `CFtpConnection` objet directement ; au lieu de cela, appelez [CInternetSession :: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), qui crée l' `CFtpConnection` objet et retourne un pointeur vers celui-ci.

Pour en savoir plus sur le `CFtpConnection` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la communication avec les deux autres services pris en charge, HTTP et Gopher, consultez les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Exemple

  Consultez l’exemple dans la vue d’ensemble de la classe [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Configuration requise

**En-tête :** AFXINET. h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a> CFtpConnection :: CFtpConnection

Cette fonction membre est appelée pour construire un `CFtpConnection` objet.

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Paramètres

*pSession*<br/>
Pointeur vers l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé.

*hConnected*<br/>
Handle Windows de la session Internet en cours.

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur FTP.

*dwContext*<br/>
Identificateur de contexte de l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est 1 ; Toutefois, vous pouvez assigner explicitement un ID de contexte spécifique pour l’opération. L’objet et tout travail qu’il contient sont associés à cet ID de contexte.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de l’utilisateur qui doit se connecter. Si la valeur est NULL, la valeur par défaut est Anonymous.

*pstrPassword*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont tous les deux null, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* a la valeur null (ou une chaîne vide) mais que *pstrUserName* n’a pas la valeur null, un mot de passe vide est utilisé. Le tableau suivant décrit le comportement des quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou «»|NULL ou «»|façon|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou «»|*pstrUserName*|" "|
|Chaîne NULL non NULL|ERROR|ERROR||
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive*<br/>
Spécifie le mode passif ou actif pour cette session FTP. Si la valeur est TRUE, elle définit le *dwFlag* de l’API Win32 sur INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Notes

Vous ne devez jamais créer un `CFtpConnection` objet directement. Au lieu de cela, appelez [CInternetSession :: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), qui crée l' `CFptConnection` objet.

## <a name="cftpconnectioncommand"></a><a name="command"></a> CFtpConnection :: Command

Envoie une commande directement à un serveur FTP.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pszCommand*<br/>
Pointeur vers une chaîne contenant la commande à envoyer.

*eResponse*<br/>
Spécifie si une réponse est attendue à partir du serveur FTP. Il peut s'agir de l'une des valeurs suivantes :

- `CmdRespNone` Aucune réponse n’est attendue.
- `CmdRespRead` Une réponse est attendue.
- `CmdRespWrite` Non utilisé.

CmdResponseType est membre de CFtpConnection, défini dans *AFXINET. h*.

*dwFlags*<br/>
Valeur contenant les indicateurs qui contrôlent cette fonction. Pour obtenir une liste complète, consultez [getdcbrushcolor](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Pointeur vers une valeur contenant une valeur définie par l'application utilisée pour identifier le contexte de l'application dans les rappels.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la fonction [getdcbrushcolor](/windows/win32/api/wininet/nf-wininet-ftpcommandw) , comme décrit dans la SDK Windows.

Si une erreur se produit, MFC lève une exception de type [CInternetException](../../mfc/reference/cinternetexception-class.md).

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a> CFtpConnection :: CreateDirectory

Appelez cette fonction membre pour créer un répertoire sur le serveur connecté.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Pointeur vers une chaîne contenant le nom du répertoire à créer.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Windows [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez `GetCurrentDirectory` pour déterminer le répertoire de travail actuel pour cette connexion au serveur. Ne partez pas du principe que le système distant vous a connecté au répertoire racine.

Le `pstrDirName` paramètre peut être un nom de fichier partiellement ou complet par rapport au répertoire actif. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `CreateDirectory` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a> CFtpConnection :: GetCurrentDirectory

Appelez cette fonction membre pour récupérer le nom du répertoire actif.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName*<br/>
Référence à une chaîne qui recevra le nom du répertoire.

*pstrDirName*<br/>
Pointeur vers une chaîne qui reçoit le nom du répertoire.

*lpdwLen*<br/>
Pointeur vers une valeur DWORD qui contient les informations suivantes :

À l’entrée : taille de la mémoire tampon référencée par *pstrDirName*.

Au retour : nombre de caractères stockés dans *pstrDirName*. Si la fonction membre échoue et que ERROR_INSUFFICIENT_BUFFER est retourné, *lpdwLen* contient le nombre d’octets que l’application doit allouer pour recevoir la chaîne.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Pour obtenir le nom de répertoire en tant qu’URL, appelez [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Les paramètres *pstrDirName* ou *strDirName* peuvent être des noms de fichiers partiellement qualifiés par rapport au répertoire actif ou complet. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `GetCurrentDirectory` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a> CFtpConnection :: GetCurrentDirectoryAsURL

Appelez cette fonction membre pour obtenir le nom du répertoire actif sous la forme d’une URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName*<br/>
Référence à une chaîne qui recevra le nom du répertoire.

*pstrDirName*<br/>
Pointeur vers une chaîne qui reçoit le nom du répertoire.

*lpdwLen*<br/>
Pointeur vers une valeur DWORD qui contient les informations suivantes :

À l’entrée : taille de la mémoire tampon référencée par *pstrDirName*.

Au retour : nombre de caractères stockés dans *pstrDirName*. Si la fonction membre échoue et que ERROR_INSUFFICIENT_BUFFER est retourné, *lpdwLen* contient le nombre d’octets que l’application doit allouer pour recevoir la chaîne.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetCurrentDirectoryAsURL` se comporte comme [GetCurrentDirectory](#getcurrentdirectory)

Le paramètre *strDirName* peut être un nom de fichier partiellement qualifié par rapport au répertoire actif ou complet. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `GetCurrentDirectoryAsURL` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a> CFtpConnection :: GetFile

Appelez cette fonction membre pour obtenir un fichier à partir d’un serveur FTP et le stocker sur l’ordinateur local.

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrRemoteFile*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom d’un fichier à récupérer à partir du serveur FTP.

*pstrLocalFile*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom du fichier à créer sur le système local.

*bFailIfExists*<br/>
Indique si le nom de fichier peut déjà être utilisé par un fichier existant. Si le nom de fichier local existe déjà et que ce paramètre a la valeur TRUE, `GetFile` échoue. Sinon, `GetFile` efface la copie existante du fichier.

*dwAttributes*<br/>
Indique les attributs du fichier. Il peut s’agir de n’importe quelle combinaison des indicateurs FILE_ATTRIBUTE_ * suivants.

- FILE_ATTRIBUTE_ARCHIVE le fichier est un fichier d’archive. Les applications utilisent cet attribut pour marquer des fichiers pour la sauvegarde ou la suppression.

- FILE_ATTRIBUTE_COMPRESSED le fichier ou le répertoire est compressé. Pour un fichier, la compression signifie que toutes les données du fichier sont compressées. Pour un répertoire, la compression est la valeur par défaut pour les fichiers et les sous-répertoires nouvellement créés.

- FILE_ATTRIBUTE_DIRECTORY le fichier est un répertoire.

- FILE_ATTRIBUTE_NORMAL aucun autre attribut n’est défini pour le fichier. Cet attribut est valide uniquement s’il est utilisé seul. Tous les autres attributs de fichier remplacent FILE_ATTRIBUTE_NORMAL :

- FILE_ATTRIBUTE_HIDDEN le fichier est masqué. Il ne doit pas être inclus dans une liste de répertoires ordinaire.

- FILE_ATTRIBUTE_READONLY le fichier est en lecture seule. Les applications peuvent lire le fichier, mais ne peut pas y écrire ou le supprimer.

- FILE_ATTRIBUTE_SYSTEM le fichier fait partie de ou est utilisé exclusivement par le système d’exploitation.

- FILE_ATTRIBUTE_TEMPORARY le fichier est utilisé pour le stockage temporaire. Les applications doivent écrire dans le fichier uniquement si cela est absolument nécessaire. La plupart des données du fichier sont conservées en mémoire sans être vidées sur le support car le fichier sera bientôt supprimé.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles le transfert se produit. Ce paramètre peut être l’une des valeurs *dwFlags* décrites dans [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) dans le SDK Windows.

*dwContext*<br/>
Identificateur de contexte pour la récupération de fichier. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetFile` est une routine de haut niveau qui gère toute la charge mémoire associée à la lecture d’un fichier à partir d’un serveur FTP et son stockage local. Les applications qui récupèrent uniquement les données de fichier ou qui nécessitent un contrôle étroit sur le transfert de fichiers doivent utiliser `OpenFile` et [CInternetFile :: Read](../../mfc/reference/cinternetfile-class.md#read) à la place.

Si *dwFlags* est FILE_TRANSFER_TYPE_ASCII, la traduction des données de fichier convertit également les caractères de contrôle et de mise en forme en équivalents Windows. Le transfert par défaut est le mode binaire, où le fichier est téléchargé dans le même format que celui dans lequel il est stocké sur le serveur.

*PstrRemoteFile* et *pstrLocalFile* peuvent être des noms de fichiers partiellement qualifiés par rapport au répertoire actif ou qualifiés complets. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `GetFile` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

Remplacez la valeur par défaut de *dwContext* pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de l' `CFtpConnection` objet créé par son objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) . La valeur est retournée à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle elle est identifiée. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a> CFtpConnection :: OpenFile

Appelez cette fonction membre pour ouvrir un fichier situé sur un serveur FTP pour la lecture ou l’écriture.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrFileName*<br/>
Pointeur vers une chaîne contenant le nom du fichier à ouvrir.

*dwAccess*<br/>
Détermine le mode d’accès au fichier. Peut être GENERIC_READ ou GENERIC_WRITE, mais pas les deux.

*dwFlags*<br/>
Spécifie les conditions sous lesquelles les transferts suivants se produisent. Il peut s’agir de l’une des constantes FTP_TRANSFER_ * suivantes :

- FTP_TRANSFER_TYPE_ASCII les transferts de fichiers à l’aide de la méthode de transfert FTP ASCII (type A). Convertit les informations de contrôle et de mise en forme en équivalents locaux.

- FTP_TRANSFER_TYPE_BINARY le fichier transfère les données à l’aide de la méthode de transfert image (type I) de FTP. Le fichier transfère les données exactement telles qu’elles existent, sans aucune modification. Il s’agit de la méthode de transfert par défaut.

*dwContext*<br/>
Identificateur de contexte pour l’ouverture du fichier. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CInternetFile](../../mfc/reference/cinternetfile-class.md) .

### <a name="remarks"></a>Notes

`OpenFile` doit être utilisé dans les situations suivantes :

- Une application contient des données qui doivent être envoyées et créées sous la forme d’un fichier sur le serveur FTP, mais ces données ne se trouvent pas dans un fichier local. Une fois qu' `OpenFile` un fichier est ouvert, l’application utilise [CInternetFile :: Write](../../mfc/reference/cinternetfile-class.md#write) pour envoyer les données du fichier FTP au serveur.

- Une application doit récupérer un fichier du serveur et la placer dans la mémoire contrôlée par l’application, au lieu de l’écrire sur le disque. L’application utilise [CInternetFile :: Read](../../mfc/reference/cinternetfile-class.md#read) après l’utilisation `OpenFile` de pour ouvrir le fichier.

- Une application a besoin d’un niveau de contrôle précis sur un transfert de fichiers. Par exemple, l’application peut souhaiter afficher un contrôle de progression pour indiquer la progression de l’état du transfert de fichiers lors du téléchargement d’un fichier.

Après `OpenFile` l’appel de et jusqu’à l’appel de `CInternetConnection::Close` , l’application peut uniquement appeler [CInternetFile :: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile :: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close` ou [CFtpFileFind :: FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Les appels à d’autres fonctions FTP pour la même session FTP échouent et le code d’erreur est défini sur FTP_ETRANSFER_IN_PROGRESS.

Le paramètre *pstrFileName* peut être un nom de fichier partiellement qualifié par rapport au répertoire actif ou complet. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `OpenFile` convertit les séparateurs de noms de répertoires en caractères appropriés avant de l’utiliser.

Remplacez la valeur par défaut de *dwContext* pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de l' `CFtpConnection` objet créé par son objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) . La valeur est retournée à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle elle est identifiée. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="cftpconnectionputfile"></a><a name="putfile"></a> CFtpConnection ::P utFile

Appelez cette fonction membre pour stocker un fichier sur un serveur FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrLocalFile*<br/>
Pointeur vers une chaîne contenant le nom du fichier à envoyer à partir du système local.

*pstrRemoteFile*<br/>
Pointeur vers une chaîne contenant le nom du fichier à créer sur le serveur FTP.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles le transfert du fichier se produit. Il peut s’agir de l’une des constantes FTP_TRANSFER_ * décrites dans [OpenFile](#openfile).

*dwContext*<br/>
Identificateur de contexte pour le placement du fichier. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`PutFile` est une routine de haut niveau qui gère toutes les opérations associées au stockage d’un fichier sur un serveur FTP. Les applications qui envoient uniquement des données, ou qui requièrent un contrôle plus étroit sur le transfert de fichiers, doivent utiliser [OpenFile](#openfile) et [CInternetFile :: Write](../../mfc/reference/cinternetfile-class.md#write).

Remplacez la valeur `dwContext` par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de l' `CFtpConnection` objet créé par son objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) . La valeur est retournée à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle elle est identifiée. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="cftpconnectionremove"></a><a name="remove"></a> CFtpConnection :: Remove

Appelez cette fonction membre pour supprimer le fichier spécifié du serveur connecté.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Paramètres

*pstrFileName*<br/>
Pointeur vers une chaîne contenant le nom de fichier à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le paramètre *pstrFileName* peut être un nom de fichier partiellement qualifié par rapport au répertoire actif ou complet. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. La `Remove` fonction convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a> CFtpConnection :: RemoveDirectory

Appelez cette fonction membre pour supprimer le répertoire spécifié du serveur connecté.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Pointeur vers une chaîne contenant le répertoire à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer le répertoire de travail actuel du serveur. Ne partez pas du principe que le système distant vous a connecté au répertoire racine.

Le paramètre *pstrDirName* peut être un nom de fichier partiellement ou complet par rapport au répertoire actif. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `RemoveDirectory` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectionrename"></a><a name="rename"></a> CFtpConnection :: Rename

Appelez cette fonction membre pour renommer le fichier spécifié sur le serveur connecté.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Paramètres

*pstrExisting*<br/>
Pointeur vers une chaîne contenant le nom actuel du fichier à renommer.

*pstrNew*<br/>
Pointeur vers une chaîne contenant le nouveau nom du fichier.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les paramètres *pstrExisting* et *pstrNew* peuvent être un nom de fichier partiellement qualifié par rapport au répertoire actif ou complet. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `Rename` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a> CFtpConnection :: SetCurrentDirectory

Appelez cette fonction membre pour basculer vers un autre répertoire sur le serveur FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Pointeur vers une chaîne contenant le nom du répertoire.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le paramètre *pstrDirName* peut être un nom de fichier partiellement ou complet par rapport au répertoire actif. Une barre oblique inverse ( \\ ) ou une barre oblique (/) peut être utilisée comme séparateur de répertoire pour les deux noms. `SetCurrentDirectory` convertit les séparateurs de noms de répertoires en caractères appropriés avant leur utilisation.

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer le répertoire de travail actuel d’un serveur FTP. Ne partez pas du principe que le système distant vous a connecté au répertoire racine.

## <a name="see-also"></a>Voir aussi

[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession (classe)](../../mfc/reference/cinternetsession-class.md)
