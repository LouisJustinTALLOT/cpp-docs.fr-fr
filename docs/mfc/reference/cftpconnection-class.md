---
title: CFtpConnection, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 12ef4de16279c5c2033a95df5928a6dfb7a2a652
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295121"
---
# <a name="cftpconnection-class"></a>CFtpConnection, classe

Gère votre connexion FTP à un serveur Internet et permet une manipulation directe des répertoires et fichiers sur ce serveur.

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
|[CFtpConnection::Command](#command)|Envoie une commande directement à un serveur FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Crée un répertoire sur le serveur.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Obtient le répertoire actif pour cette connexion.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtient le répertoire actif pour cette connexion en tant qu’URL.|
|[CFtpConnection::GetFile](#getfile)|Obtient un fichier à partir du serveur connecté|
|[CFtpConnection::OpenFile](#openfile)|Ouvre un fichier sur le serveur connecté.|
|[CFtpConnection::PutFile](#putfile)|Place un fichier sur le serveur.|
|[CFtpConnection::Remove](#remove)|Supprime un fichier à partir du serveur.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Supprime le répertoire spécifié à partir du serveur.|
|[CFtpConnection::Rename](#rename)|Renomme un fichier sur le serveur.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Définit le répertoire FTP actif.|

## <a name="remarks"></a>Notes

FTP est un des trois services Internet reconnus par les classes WinInet MFC.

Pour communiquer avec un serveur FTP Internet, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis créez un `CFtpConnection` objet. Vous ne créez jamais un `CFtpConnection` objet directement ; au lieu de cela, appelez [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), qui crée le `CFtpConnection` de l’objet et retourne un pointeur vers elle.

Pour en savoir plus sur la façon `CFtpConnection` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la communication avec les deux autres prises en charge les services HTTP et gopher, consultez les classes [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Exemple

  Consultez l’exemple dans le [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) vue d’ensemble de la classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Spécifications

**En-tête :** afxinet.h

##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection

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
Un pointeur vers le connexes [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet.

*hConnected*<br/>
Handle Windows de la session Internet actuel.

*pstrServer*<br/>
Un pointeur vers une chaîne contenant le nom du serveur FTP.

*dwContext*<br/>
L’identificateur de contexte pour l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est défini sur 1 ; Toutefois, vous pouvez affecter explicitement un ID de contexte spécifique pour l’opération. L’objet et n’importe quel travail qu’elle effectue sera associés à cet ID de contexte.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur pour vous connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword*<br/>
Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux *pstrPassword* et *pstrUserName* ont la valeur NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide), mais *pstrUserName* n’est pas NULL, un mot de passe vide est utilisée. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou « »|NULL ou « »|« anonyme »|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou « »|*pstrUserName*|" "|
|Chaîne Non-NULL NULL|ERROR|ERROR||
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

*bPassive*<br/>
Spécifie le mode actif ou passif pour cette session FTP. Si la valeur est TRUE, elle définit l’API Win32 *dwFlag* à INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Notes

Vous ne créez jamais un `CFtpConnection` directement l’objet. Au lieu de cela, appelez [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), ce qui crée le `CFptConnection` objet.

##  <a name="command"></a>  CFtpConnection::Command

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
Détermine si une réponse du serveur FTP est attendue. Peut avoir l'une des valeurs suivantes :

- `CmdRespNone` Aucune réponse n’est attendue.

- `CmdRespRead` Une réponse est attendue.

*dwFlags*<br/>
Valeur contenant les indicateurs qui contrôlent cette fonction. Pour obtenir la liste complète, consultez [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda).

*dwContext*<br/>
Pointeur vers une valeur contenant une valeur définie par l'application utilisée pour identifier le contexte de l'application dans les rappels.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité de la [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda) de fonction, comme décrit dans le SDK Windows.

Si une erreur se produit, MFC lève une exception de type [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

Appelez cette fonction membre pour créer un répertoire sur le serveur connecté.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Un pointeur vers une chaîne contenant le nom du répertoire à créer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Windows [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez `GetCurrentDirectory` pour déterminer le répertoire de travail actuel pour cette connexion au serveur. Ne supposez pas que le système distant a vous connecté au répertoire racine.

Le `pstrDirName` paramètre peut être soit un partiellement ou un nom qualifié complet de fichier relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `CreateDirectory` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory

Appelez cette fonction membre pour obtenir le nom du répertoire actif.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName*<br/>
Une référence à une chaîne qui recevra le nom du répertoire.

*pstrDirName*<br/>
Un pointeur vers une chaîne qui recevra le nom du répertoire.

*lpdwLen*<br/>
Un pointeur vers une valeur DWORD qui contient les informations suivantes :

|||
|-|-|
|Sur l’entrée|La taille de la mémoire tampon référencée par *pstrDirName*.|
|Au retour|Le nombre de caractères stockés à *pstrDirName*. Si la fonction membre échoue et ERROR_INSUFFICIENT_BUFFER est retourné, puis *lpdwLen* contient le nombre d’octets que l’application doit allouer afin de recevoir la chaîne.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Pour obtenir le nom du répertoire en tant qu’une URL au lieu de cela, appelez [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Les paramètres *pstrDirName* ou *strDirName* peut être soit noms partiellement qualifiés relatif au répertoire actif ou complet. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `GetCurrentDirectory` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL

Appelez cette fonction membre pour obtenir le nom du répertoire actuel en tant qu’URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Paramètres

*strDirName*<br/>
Une référence à une chaîne qui recevra le nom du répertoire.

*pstrDirName*<br/>
Un pointeur vers une chaîne qui recevra le nom du répertoire.

*lpdwLen*<br/>
Un pointeur vers une valeur DWORD qui contient les informations suivantes :

|||
|-|-|
|Sur l’entrée|La taille de la mémoire tampon référencée par *pstrDirName*.|
|Au retour|Le nombre de caractères stockés à *pstrDirName*. Si la fonction membre échoue et ERROR_INSUFFICIENT_BUFFER est retourné, puis *lpdwLen* contient le nombre d’octets que l’application doit allouer afin de recevoir la chaîne.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetCurrentDirectoryAsURL` se comporte comme [GetCurrentDirectory](#getcurrentdirectory)

Le paramètre *strDirName* peut être soit noms partiellement qualifiés relatif au répertoire actif ou complet. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `GetCurrentDirectoryAsURL` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="getfile"></a>  CFtpConnection::GetFile

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
Pointeur vers une chaîne se terminant par null qui contient le nom d’un fichier à récupérer à partir du serveur FTP.

*pstrLocalFile*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom du fichier à créer sur le système local.

*bFailIfExists*<br/>
Indique si le nom de fichier peut déjà être utilisé par un fichier existant. Si le nom de fichier local existe déjà, et ce paramètre est TRUE, `GetFile` échoue. Sinon, `GetFile` effacera la copie existante du fichier.

*dwAttributes*<br/>
Indique les attributs du fichier. Cela peut être n’importe quelle combinaison des indicateurs FILE_ATTRIBUTE_ * suivants.

- FILE_ATTRIBUTE_ARCHIVE le fichier est un fichier d’archive. Applications utilisent cet attribut pour marquer les fichiers pour la sauvegarde ou la suppression.

- FILE_ATTRIBUTE_COMPRESSED le fichier ou répertoire est compressé. Pour un fichier, la compression signifie que toutes les données dans le fichier est compressé. Pour un répertoire, la compression est la valeur par défaut pour les fichiers nouvellement créés et les sous-répertoires.

- FILE_ATTRIBUTE_DIRECTORY le fichier est un répertoire.

- FILE_ATTRIBUTE_NORMAL le fichier n’a aucuns autres attributs à définir. Cet attribut est valide uniquement si utilisé seul. Tous les autres attributs de fichier remplacent FILE_ATTRIBUTE_NORMAL :

- FILE_ATTRIBUTE_HIDDEN le fichier est masqué. Il doit ne pas être inclus dans une liste de répertoires ordinaire.

- ATTRIBUT_FICHIER_LECTURESEULE le fichier est en lecture seule. Les applications peuvent lire le fichier, mais ne peut pas y écrire ou supprimez-le.

- FILE_ATTRIBUTE_SYSTEM le fichier fait partie d’ou est utilisé exclusivement par le système d’exploitation.

- FILE_ATTRIBUTE_TEMPORARY le fichier est utilisé pour le stockage temporaire. Les applications doivent écrire dans le fichier uniquement en cas de nécessité absolue. La plupart des données du fichier reste en mémoire sans vidés sur le support, car le fichier sera bientôt supprimé.

*dwFlags*<br/>
Spécifie les conditions sous lesquelles le transfert se produit. Ce paramètre peut être une de le *dwFlags* valeurs décrites dans [FtpGetFile](/windows/desktop/api/wininet/nf-wininet-ftpgetfilea) dans le SDK Windows.

*dwContext*<br/>
L’identificateur de contexte pour la récupération de fichier. Consultez **remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`GetFile` est une routine de haut niveau qui gère la surcharge associée à la lecture d’un fichier à partir d’un serveur FTP et en le stockant localement. Qui récupérer uniquement les données de fichier, ou qui requièrent un contrôle fermer le transfert de fichiers, les applications doivent utiliser `OpenFile` et [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) à la place.

Si *dwFlags* FILE_TRANSFER_TYPE_ASCII, traduction de données de fichiers également convertit contrôle et mise en forme des caractères en équivalents de Windows. Le transfert par défaut est en mode binaire, où le fichier est téléchargé dans le même format qu’il est stocké sur le serveur.

Les deux *pstrRemoteFile* et *pstrLocalFile* peut être soit noms partiellement qualifiés relatif au répertoire actif ou complet. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `GetFile` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

Remplacer le *dwContext* par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CFtpConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

##  <a name="openfile"></a>  CFtpConnection::OpenFile

Appelez cette fonction membre pour ouvrir un fichier situé sur un serveur FTP pour la lecture ou écriture.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pstrFileName*<br/>
Un pointeur vers une chaîne contenant le nom du fichier à ouvrir.

*dwAccess*<br/>
Détermine la façon dont le fichier est accessible. Peut être GENERIC_READ ou GENERIC_WRITE, mais pas les deux.

*dwFlags*<br/>
Spécifie les conditions dans lesquelles les transferts suivants se produisent. Il peut s’agir d’une des constantes FTP_TRANSFER_ * suivantes :

- FTP_TRANSFER_TYPE_ASCII le fichier transfère à l’aide de la méthode de transfert FTP ASCII (Type A). Contrôle de convertit et les informations de mise en forme en équivalents locaux.

- FTP_TRANSFER_TYPE_BINARY le fichier transfère les données à l’aide de la méthode de transfert d’Image FTP's (Type I). Les données de transferts de fichiers exactement tel qu’il existent, sans aucune modification. Il s’agit de la méthode de transfert par défaut.

*dwContext*<br/>
L’identificateur de contexte pour l’ouverture du fichier. Consultez **remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CInternetFile](../../mfc/reference/cinternetfile-class.md) objet.

### <a name="remarks"></a>Notes

`OpenFile` doit être utilisé dans les situations suivantes :

- Une application a des données devant être envoyées et créée en tant que fichier sur le serveur FTP, mais que les données ne sont pas dans un fichier local. Une fois `OpenFile` ouvre un fichier, l’application utilise [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) pour envoyer les données de fichier FTP sur le serveur.

- Une application doit récupérer un fichier à partir du serveur et placez-le dans la mémoire contrôlé par l’application, au lieu d’écrire sur disque. L’application utilise [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) après avoir utilisé `OpenFile` pour ouvrir le fichier.

- Une application a besoin d’un niveau de contrôle sur un transfert de fichiers. Par exemple, l’application peut souhaiter afficher une progression contrôle indiquent la progression de l’état de transfert de fichier lors du téléchargement d’un fichier.

Après avoir appelé `OpenFile` et jusqu'à ce que l’appel `CInternetConnection::Close`, l’application peut appeler uniquement [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`, ou [ CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Appels à d’autres fonctions FTP pour la même session FTP échoue et la valeur FTP_ETRANSFER_IN_PROGRESS le code d’erreur.

Le *pstrFileName* paramètre peut être soit un partiellement qualifié nom de fichier qualifié complet ou relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `OpenFile` traduit les séparateurs de nom de répertoire caractères appropriés avant de l’utiliser.

Remplacer le *dwContext* par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CFtpConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

##  <a name="putfile"></a>  CFtpConnection::PutFile

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
Un pointeur vers une chaîne contenant le nom du fichier à envoyer à partir du système local.

*pstrRemoteFile*<br/>
Un pointeur vers une chaîne contenant le nom du fichier à créer sur le serveur FTP.

*dwFlags*<br/>
Spécifie les conditions sous lesquelles le transfert du fichier se produit. Peut être une des constantes FTP_TRANSFER_ * décrites dans [OpenFile](#openfile).

*dwContext*<br/>
L’identificateur de contexte pour placer le fichier. Consultez **remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

`PutFile` est une routine de haut niveau qui gère toutes les opérations associées au stockage d’un fichier sur un serveur FTP. Les applications qui envoient uniquement des données, ou qui nécessitent un contrôle plus en détail sur le transfert de fichiers, doivent utiliser [OpenFile](#openfile) et [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Remplacer le `dwContext` par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CFtpConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

##  <a name="remove"></a>  CFtpConnection::Remove

Appelez cette fonction membre pour supprimer le fichier spécifié à partir du serveur connecté.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Paramètres

*pstrFileName*<br/>
Un pointeur vers une chaîne contenant le nom de fichier à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le *pstrFileName* paramètre peut être soit un partiellement qualifié nom de fichier qualifié complet ou relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. Le `Remove` fonction traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

Appelez cette fonction membre pour supprimer le répertoire spécifié à partir du serveur connecté.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Un pointeur vers une chaîne contenant le répertoire à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer le répertoire de travail actuel du serveur. Ne supposez pas que le système distant a vous connecté au répertoire racine.

Le *pstrDirName* paramètre peut être soit un nom de fichier qualifié complet ou partiel relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `RemoveDirectory` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="rename"></a>  CFtpConnection::Rename

Appelez cette fonction membre pour renommer le fichier spécifié sur le serveur connecté.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Paramètres

*pstrExisting*<br/>
Un pointeur vers une chaîne contenant le nom actuel du fichier à renommer.

*pstrNew*<br/>
Un pointeur vers une chaîne contenant le nom du fichier nouveau.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le *pstrExisting* et *pstrNew* paramètres peuvent être soit un partiellement qualifié nom de fichier qualifié complet ou relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `Rename` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory

Appelez cette fonction membre pour passer à un autre répertoire sur le serveur FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Paramètres

*pstrDirName*<br/>
Un pointeur vers une chaîne contenant le nom du répertoire.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Le *pstrDirName* paramètre peut être soit un nom de fichier qualifié complet ou partiel relatif au répertoire actif. Une barre oblique inverse (\\) ou par une barre oblique (/) peut être utilisée comme séparateur de répertoire pour le nom. `SetCurrentDirectory` traduit les séparateurs de nom de répertoire caractères appropriés avant de les utiliser.

Utilisez [GetCurrentDirectory](#getcurrentdirectory) pour déterminer le répertoire de travail actuel d’un serveur FTP. Ne supposez pas que le système distant a vous connecté au répertoire racine.

## <a name="see-also"></a>Voir aussi

[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession, classe](../../mfc/reference/cinternetsession-class.md)
