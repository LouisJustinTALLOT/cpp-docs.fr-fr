---
title: Classe CFtpConnection
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
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373777"
---
# <a name="cftpconnection-class"></a>Classe CFtpConnection

Gère votre connexion FTP à un serveur Internet et permet la manipulation directe des répertoires et des fichiers sur ce serveur.

## <a name="syntax"></a>Syntaxe

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Construit un objet `CFtpConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFtpConnection::Commande](#command)|Envoie une commande directement à un serveur FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Crée un répertoire sur le serveur.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Obtient le répertoire actuel pour cette connexion.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtient le répertoire actuel pour cette connexion comme URL.|
|[CFtpConnection::GetFile](#getfile)|Obtient un fichier à partir du serveur connecté|
|[CFtpConnection::OpenFile](#openfile)|Ouvre un fichier sur le serveur connecté.|
|[CFtpConnection::PutFile](#putfile)|Place un fichier sur le serveur.|
|[CFtpConnection::Supprimer](#remove)|Supprime un fichier du serveur.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Supprime l’annuaire spécifié du serveur.|
|[CFtpConnection::Rename](#rename)|Renomme un fichier sur le serveur.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Définit l’annuaire FTP actuel.|

## <a name="remarks"></a>Notes

FTP est l’un des trois services Internet reconnus par les classes MFC WinInet.

Pour communiquer avec un serveur Internet FTP, vous devez d’abord créer un `CFtpConnection` exemple de [CInternetSession,](../../mfc/reference/cinternetsession-class.md)puis créer un objet. Vous ne `CFtpConnection` créez jamais un objet directement; plutôt, appelez [CInternetSession:GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), `CFtpConnection` qui crée l’objet et retourne un pointeur à elle.

Pour en savoir `CFtpConnection` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la communication avec les deux autres services pris en charge, HTTP et gopher, voir les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Exemple

  Voir l’exemple dans la vue d’ensemble de la classe [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Cette fonction de membre `CFtpConnection` est appelée à construire un objet.

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
Un pointeur à l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) connexe.

*hConnecté*<br/>
La poignée Windows de la session Internet actuelle.

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur FTP.

*dwContexte*<br/>
L’identifiant de contexte pour l’opération. *dwContext* identifie les informations sur l’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est réglée à 1; toutefois, vous pouvez affecter explicitement une pièce d’identité de contexte spécifique pour l’opération. L’objet et tout travail qu’il fait sera associé à cette pièce d’identité contextuelle.

*pstrUserName (en)*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom de l’utilisateur à se connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne non terminée qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide) mais *pstrUserName n’est* pas NULL, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement des quatre réglages possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou "|NULL ou "|"anonyme"|Nom de l’e-mail de l’utilisateur|
|Chaîne non-NULL|NULL ou "|*pstrUserName (en)*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Chaîne non-NULL|Chaîne non-NULL|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|

*nPort (en)*<br/>
Un numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive (en)*<br/>
Spécifie le mode passif ou actif pour cette session FTP. S’il est réglé sur TRUE, il définit le Win32 API *dwFlag* à INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Notes

Vous ne `CFtpConnection` créez jamais un objet directement. Au lieu de cela, appelez [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), qui crée l’objet. `CFptConnection`

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtpConnection::Commande

Envoie une commande directement à un serveur FTP.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pszCommand (en)*<br/>
Pointeur vers une chaîne contenant la commande à envoyer.

*eResponse*<br/>
Précise si une réponse est attendue du serveur FTP. Il peut s'agir de l'une des valeurs suivantes :

- `CmdRespNone`Aucune réponse n’est attendue.
- `CmdRespRead`Une réponse est attendue.
- `CmdRespWrite`Pas utilisé.

Le CmdResponseType est un membre de CFtpConnection, défini en *afxinet.h*.

*dwFlags*<br/>
Valeur contenant les indicateurs qui contrôlent cette fonction. Pour une liste complète, voir [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContexte*<br/>
Pointeur vers une valeur contenant une valeur définie par l'application utilisée pour identifier le contexte de l'application dans les rappels.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité de la fonction [FTPCommand,](/windows/win32/api/wininet/nf-wininet-ftpcommandw) telle que décrite dans le SDK Windows.

En cas d’erreur, MFC lance une exception de type [CInternetException](../../mfc/reference/cinternetexception-class.md).

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtpConnection::CreateDirectory

Appelez cette fonction de membre pour créer un répertoire sur le serveur connecté.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName (en)*<br/>
Un pointeur à une chaîne contenant le nom de l’annuaire à créer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Windows [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez `GetCurrentDirectory` pour déterminer l’annuaire de travail actuel pour cette connexion au serveur. Ne présumez pas que le système distant vous a connecté au répertoire racine.

Le `pstrDirName` paramètre peut être soit un nom de fichier partiellement ou entièrement qualifié par rapport à l’annuaire actuel. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `CreateDirectory`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Appelez cette fonction de membre pour obtenir le nom de l’annuaire actuel.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName (en)*<br/>
Une référence à une chaîne qui recevra le nom de l’annuaire.

*pstrDirName (en)*<br/>
Un pointeur à une chaîne qui recevra le nom de l’annuaire.

*lpdwLen*<br/>
Un pointeur à un DWORD qui contient les informations suivantes:

|||
|-|-|
|À l’entrée|La taille du tampon référencé par *pstrDirName*.|
|Au retour|Le nombre de caractères stockés à *pstrDirName*. Si la fonction du membre échoue et ERROR_INSUFFICIENT_BUFFER est retournée, *puis lpdwLen* contient le nombre d’octets que l’application doit attribuer afin de recevoir la chaîne.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Pour obtenir le nom d’annuaire comme URL à la place, appelez [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Les paramètres *pstrDirName* ou *strDirName* peuvent être soit des noms de fichiers partiellement qualifiés par rapport à l’annuaire actuel, soit entièrement qualifiés. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `GetCurrentDirectory`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Appelez cette fonction de membre pour obtenir le nom de l’annuaire actuel comme URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName (en)*<br/>
Une référence à une chaîne qui recevra le nom de l’annuaire.

*pstrDirName (en)*<br/>
Un pointeur à une chaîne qui recevra le nom de l’annuaire.

*lpdwLen*<br/>
Un pointeur à un DWORD qui contient les informations suivantes:

|||
|-|-|
|À l’entrée|La taille du tampon référencé par *pstrDirName*.|
|Au retour|Le nombre de caractères stockés à *pstrDirName*. Si la fonction du membre échoue et ERROR_INSUFFICIENT_BUFFER est retournée, *puis lpdwLen* contient le nombre d’octets que l’application doit attribuer afin de recevoir la chaîne.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetCurrentDirectoryAsURL`se comporte de la même façon que [GetCurrentDirectory](#getcurrentdirectory)

Le *paramètre strDirName* peut être soit des noms de fichiers partiellement qualifiés par rapport à l’annuaire actuel, soit entièrement qualifiés. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `GetCurrentDirectoryAsURL`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtpConnection::GetFile

Appelez cette fonction de membre pour obtenir un fichier à partir d’un serveur FTP et le stocker sur la machine locale.

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
Un pointeur à une chaîne non terminée contenant le nom d’un fichier à récupérer sur le serveur FTP.

*pstrLocalFile*<br/>
Un pointeur à une chaîne non terminée contenant le nom du fichier à créer sur le système local.

*bFailIfExistes*<br/>
Indique si le nom du fichier peut déjà être utilisé par un fichier existant. Si le nom de fichier local existe déjà, et ce paramètre est VRAI, `GetFile` échoue. Dans `GetFile` le cas contraire, effacera la copie existante du fichier.

*dwAttributes*<br/>
Indique les attributs du fichier. Il peut s’agir de n’importe quelle combinaison des drapeaux FILE_ATTRIBUTE_ suivants.

- FILE_ATTRIBUTE_ARCHIVE Le fichier est un fichier d’archives. Les applications utilisent cet attribut pour marquer les fichiers pour la sauvegarde ou la suppression.

- FILE_ATTRIBUTE_COMPRESSED Le fichier ou l’annuaire est comprimé. Pour un fichier, la compression signifie que toutes les données du fichier sont compressées. Pour un répertoire, la compression est la valeur par défaut pour les fichiers et sous-directeurs nouvellement créés.

- FILE_ATTRIBUTE_DIRECTORY Le dossier est un répertoire.

- FILE_ATTRIBUTE_NORMAL Le fichier n’a pas d’autres attributs définis. Cet attribut n’est valable que s’il est utilisé seul. Tous les autres attributs de fichiers l’emportent sur FILE_ATTRIBUTE_NORMAL :

- FILE_ATTRIBUTE_HIDDEN Le fichier est caché. Il ne doit pas être inclus dans une liste d’annuaire ordinaire.

- FILE_ATTRIBUTE_READONLY Le fichier est lu uniquement. Les applications peuvent lire le fichier, mais ne peuvent pas l’écrire ou le supprimer.

- FILE_ATTRIBUTE_SYSTEM Le fichier fait partie ou est utilisé exclusivement par le système d’exploitation.

- FILE_ATTRIBUTE_TEMPORARY Le fichier est utilisé pour le stockage temporaire. Les demandes ne doivent être écrites au fichier que si cela est absolument nécessaire. La plupart des données du fichier restent en mémoire sans être rincés dans les médias car le fichier sera bientôt supprimé.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles le transfert se produit. Ce paramètre peut être l’une des valeurs *dwFlags décrites* dans [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) dans le SDK Windows.

*dwContexte*<br/>
L’identifiant de contexte pour la récupération du fichier. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetFile`est une routine de haut niveau qui gère tous les frais généraux associés à la lecture d’un fichier à partir d’un serveur FTP et le stocker localement. Les applications qui ne récupèrent que les données du `OpenFile` fichier, ou qui nécessitent un contrôle étroit sur le transfert de fichiers, doivent être utilisées et [CInternetFile::Lire plutôt.](../../mfc/reference/cinternetfile-class.md#read)

Si *dwFlags* est FILE_TRANSFER_TYPE_ASCII, la traduction des données de fichiers convertit également les caractères de contrôle et de formatage en équivalents Windows. Le transfert par défaut est en mode binaire, où le fichier est téléchargé dans le même format qu’il est stocké sur le serveur.

*PstrRemoteFile* et *pstrLocalFile* peuvent être soit des noms de fichiers partiellement qualifiés par rapport à l’annuaire actuel, soit entièrement qualifiés. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `GetFile`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

Remplacer la valeur par défaut *dwContext* pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est associé `CFtpConnection` à cette opération spécifique de l’objet créé par son objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md) La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’opération avec laquelle il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtpConnection::OpenFile

Appelez cette fonction de membre pour ouvrir un fichier situé sur un serveur FTP pour la lecture ou l’écriture.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrFileName (en)*<br/>
Un pointeur à une chaîne contenant le nom du fichier à ouvrir.

*dwAccess*<br/>
Détermine comment le fichier sera consulté. Peut être GENERIC_READ ou GENERIC_WRITE, mais pas les deux.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles les transferts ultérieurs ont lieu. Il peut s’agir de l’une des constantes suivantes FTP_TRANSFER_MD :

- FTP_TRANSFER_TYPE_ASCII Les transferts de fichiers à l’aide de la méthode de transfert FTP ASCII (type A). Convertit les informations de contrôle et de formatage en équivalents locaux.

- FTP_TRANSFER_TYPE_BINARY Le fichier transfère des données à l’aide de la méthode de transfert image (type I) de FTP. Le fichier transfère les données exactement comme elles existent, sans modifications. C’est la méthode de transfert par défaut.

*dwContexte*<br/>
L’identifiant de contexte pour l’ouverture du fichier. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Un pointeur sur un objet [CInternetFile.](../../mfc/reference/cinternetfile-class.md)

### <a name="remarks"></a>Notes

`OpenFile`doivent être utilisés dans les situations suivantes :

- Une application dispose de données qui doivent être envoyées et créées sous forme de fichier sur le serveur FTP, mais ces données ne sont pas dans un fichier local. Une `OpenFile` fois qu’elle ouvre un fichier, l’application utilise [CInternetFile : : Écrivez](../../mfc/reference/cinternetfile-class.md#write) pour envoyer les données de fichiers FTP au serveur.

- Une application doit récupérer un fichier du serveur et le placer dans la mémoire contrôlée par l’application, au lieu de l’écrire sur disque. L’application utilise [CInternetFile:Lire](../../mfc/reference/cinternetfile-class.md#read) après utilisation `OpenFile` pour ouvrir le fichier.

- Une application a besoin d’un niveau de contrôle sur un transfert de fichiers. Par exemple, l’application peut indiquer l’avancement de l’état du transfert de fichiers lors du téléchargement d’un fichier.

Après `OpenFile` avoir appelé `CInternetConnection::Close`et jusqu’à l’appel , l’application ne peut appeler [CInternetFile::Lire](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Ecrire](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`ou [CFtpFileFind:FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Les appels vers d’autres fonctions FTP pour la même session FTP échoueront et définiront le code d’erreur pour FTP_ETRANSFER_IN_PROGRESS.

Le *paramètre pstrFileName* peut être soit un nom de fichier partiellement qualifié par rapport à l’annuaire actuel, soit entièrement qualifié. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `OpenFile`traduit les séparateurs de nom de répertoire aux caractères appropriés avant de l’utiliser.

Remplacer la valeur par défaut *dwContext* pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est associé `CFtpConnection` à cette opération spécifique de l’objet créé par son objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md) La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’opération avec laquelle il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtpConnection::PutFile

Appelez cette fonction de membre pour stocker un fichier sur un serveur FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrLocalFile*<br/>
Un pointeur à une chaîne contenant le nom du fichier à envoyer à partir du système local.

*pstrRemoteFile*<br/>
Un pointeur à une chaîne contenant le nom du fichier à créer sur le serveur FTP.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles le transfert du fichier se produit. Peut être l’une des constantes FTP_TRANSFER_ » décrites dans [OpenFile](#openfile).

*dwContexte*<br/>
L’identifiant de contexte pour le placement du fichier. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`PutFile`est une routine de haut niveau qui gère toutes les opérations associées au stockage d’un fichier sur un serveur FTP. Les applications qui n’envoient que des données, ou qui nécessitent un contrôle plus étroit sur le transfert de fichiers, doivent utiliser [OpenFile](#openfile) et [CInternetFile::Écrire](../../mfc/reference/cinternetfile-class.md#write).

Remplacez `dwContext` la valeur par défaut pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est associé `CFtpConnection` à cette opération spécifique de l’objet créé par son objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md) La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’opération avec laquelle il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtpConnection::Supprimer

Appelez cette fonction de membre pour supprimer le fichier spécifié du serveur connecté.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Paramètres

*pstrFileName (en)*<br/>
Un pointeur à une chaîne contenant le nom du fichier à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le *paramètre pstrFileName* peut être soit un nom de fichier partiellement qualifié par rapport à l’annuaire actuel, soit entièrement qualifié. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. La `Remove` fonction traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Appelez cette fonction de membre pour supprimer l’annuaire spécifié du serveur connecté.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName (en)*<br/>
Un pointeur à une chaîne contenant le répertoire à enlever.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer l’annuaire de travail actuel du serveur. Ne présumez pas que le système distant vous a connecté au répertoire racine.

Le *paramètre pstrDirName* peut être soit un nom de fichier partiellement ou entièrement qualifié par rapport à l’annuaire actuel. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `RemoveDirectory`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtpConnection::Rename

Appelez cette fonction de membre pour renommer le fichier spécifié sur le serveur connecté.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Paramètres

*pstrExisting*<br/>
Un pointeur à une chaîne contenant le nom actuel du fichier à renommer.

*pstrNew*<br/>
Un pointeur à une chaîne contenant le nouveau nom du fichier.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les paramètres *pstrExisting* et *pstrNew* peuvent être soit un nom de fichier partiellement qualifié par rapport à l’annuaire actuel, soit entièrement qualifié. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `Rename`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Appelez cette fonction de membre pour passer à un répertoire différent sur le serveur FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName (en)*<br/>
Un pointeur à une chaîne contenant le nom du répertoire.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le *paramètre pstrDirName* peut être soit un nom de fichier partiellement ou entièrement qualifié par rapport à l’annuaire actuel. Une barre oblique inverse ()\\ou une barre oblique avant (/) peut être utilisée comme séparateur d’annuaire pour l’un ou l’autre nom. `SetCurrentDirectory`traduit les séparateurs de nom de répertoire aux caractères appropriés avant qu’ils ne soient utilisés.

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer l’annuaire de travail actuel d’un serveur FTP. Ne présumez pas que le système distant vous a connecté au répertoire racine.

## <a name="see-also"></a>Voir aussi

[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession, classe](../../mfc/reference/cinternetsession-class.md)
