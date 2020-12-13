---
description: 'En savoir plus sur : classe CAtlTransactionManager'
title: CAtlTransactionManager, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 25d5ea7e9b4838f483dd7f9ee408cdd5bd4c88cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147184"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager, classe

La classe CAtlTransactionManager fournit un wrapper aux fonctions du gestionnaire de transactions KTM (Kernel Transaction Manager).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|Destructeur CAtlTransactionManager.|
|[CAtlTransactionManager](#catltransactionmanager)|Constructeur CAtlTransactionManager.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Close](#close)|Ferme un handle de transaction.|
|[Commiter](#commit)|Demande que la transaction soit validée.|
|[Créer](#create)|Crée le descripteur de transaction.|
|[CreateFile](#createfile)|Crée ou ouvre un fichier, un flux de fichier ou un répertoire sous la forme d’une opération traitée.|
|[DeleteFile](#deletefile)|Supprime un fichier existant en tant qu’opération traitée.|
|[FindFirstFile](#findfirstfile)|Recherche un fichier ou un sous-répertoire dans un répertoire en tant qu’opération traitée.|
|[GetFileAttributes](#getfileattributes)|Récupère les attributs du système de fichiers d’un fichier ou d’un répertoire spécifié en tant qu’opération traitée.|
|[GetFileAttributesEx](#getfileattributesex)|Récupère les attributs du système de fichiers d’un fichier ou d’un répertoire spécifié en tant qu’opération traitée.|
|[GetHandle,](#gethandle)|Retourne le handle de transaction.|
|[IsFallback](#isfallback)|Détermine si les appels de secours sont activés.|
|[MoveFile](#movefile)|Déplace un fichier existant ou un répertoire, y compris ses enfants, en tant qu’opération traitée.|
|[RegCreateKeyEx](#regcreatekeyex)|Crée la clé de Registre spécifiée et l’associe à une transaction. Si la clé existe déjà, la fonction l’ouvre.|
|[RegDeleteKey](#regdeletekey)|Supprime une sous-clé et ses valeurs de la vue spécifique à la plateforme spécifiée du registre en tant qu’opération traitée.|
|[RegOpenKeyEx](#regopenkeyex)|Ouvre la clé de Registre spécifiée et l’associe à une transaction.|
|[Restauration](#rollback)|Demande que la transaction soit restaurée.|
|[SetFileAttributes](#setfileattributes)|Définit les attributs d’un fichier ou d’un répertoire en tant qu’opération traitée.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|TRUE si le secours est pris en charge ; FALSe dans le cas contraire.|
|[m_hTransaction](#m_htransaction)|Descripteur de transaction.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ATL :: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** atltransactionmanager. h

## <a name="catltransactionmanager"></a><a name="dtor"></a>  ~ CAtlTransactionManager

Destructeur CAtlTransactionManager.

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Notes

Dans un traitement normal, la transaction est automatiquement validée et fermée. Si le destructeur est appelé pendant un déroulement d’exception, la transaction est restaurée et fermée.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a> CAtlTransactionManager

Constructeur CAtlTransactionManager.

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Paramètres

*bFallback*<br/>
TRUE indique que prend en charge le secours. Si la fonction traitée échoue, la classe appelle automatiquement la fonction « non traitée ». FALSe n’indique aucun appel « de secours ».

*bAutoCreateTransaction*<br/>
TRUE indique que le gestionnaire de transactions est créé automatiquement dans le constructeur. FALSe indique qu’il ne l’est pas.

### <a name="remarks"></a>Notes

## <a name="close"></a><a name="close"></a> Plus

Ferme le handle de transaction.

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `CloseHandle` fonction. La méthode est appelée automatiquement dans le destructeur.

## <a name="commit"></a><a name="commit"></a> Valider

Demande que la transaction soit validée.

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `CommitTransaction` fonction. La méthode est appelée automatiquement dans le destructeur.

## <a name="create"></a><a name="create"></a> Créer

Crée le descripteur de transaction.

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `CreateTransaction` fonction. Vérifier

## <a name="createfile"></a><a name="createfile"></a> CreateFile

Crée ou ouvre un fichier, un flux de fichier ou un répertoire sous la forme d’une opération traitée.

```cpp
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom d’un objet à créer ou à ouvrir.

*dwDesiredAccess*<br/>
Accès à l’objet, qui peut être résumé comme lecture, écriture, les deux ou aucun des deux (zéro). Les valeurs les plus couramment utilisées sont GENERIC_READ, GENERIC_WRITE ou les deux : GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
Mode de partage d’un objet, qui peut être lu, écrit, les deux, supprimer, tous ou aucun : 0, FILE_SHARE_DELETE, FILE_SHARE_READ FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Pointeur vers une structure SECURITY_ATTRIBUTES qui contient un descripteur de sécurité facultatif et détermine également si le handle retourné peut être hérité par les processus enfants. Le paramètre peut avoir la valeur NULL.

*dwCreationDisposition*<br/>
Action à effectuer sur les fichiers qui existent et qui n’existent pas. Ce paramètre doit avoir l’une des valeurs suivantes, qui ne peuvent pas être combinées : CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING ou TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Attributs et indicateurs de fichier. Ce paramètre peut inclure n’importe quelle combinaison des attributs de fichier disponibles (FILE_ATTRIBUTE_ *). Tous les autres attributs de fichier remplacent FILE_ATTRIBUTE_NORMAL. Ce paramètre peut également contenir des combinaisons d’indicateurs (FILE_FLAG_ \* ) pour contrôler le comportement de mise en mémoire tampon, les modes d’accès et d’autres indicateurs spéciaux. Celles-ci sont combinées avec toutes les valeurs de FILE_ATTRIBUTE_ \* .

*hTemplateFile*<br/>
Handle valide d’un fichier de modèle avec le droit d’accès GENERIC_READ. Le fichier de modèle fournit des attributs de fichier et des attributs étendus pour le fichier en cours de création. Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle qui peut être utilisé pour accéder à l’objet.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `CreateFileTransacted` fonction.

## <a name="deletefile"></a><a name="deletefile"></a> DeleteFile

Supprime un fichier existant en tant qu’opération traitée.

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom du fichier à supprimer.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `DeleteFileTransacted` fonction.

## <a name="findfirstfile"></a><a name="findfirstfile"></a> FindFirstFile

Recherche un fichier ou un sous-répertoire dans un répertoire en tant qu’opération traitée.

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Répertoire ou chemin d’accès et nom de fichier à rechercher. Ce paramètre peut inclure des caractères génériques, tels qu’un astérisque (*) ou un point d’interrogation ().

*pNextInfo*<br/>
Pointeur vers la structure WIN32_FIND_DATA qui reçoit des informations sur un fichier ou un sous-répertoire trouvé.

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est un handle de recherche utilisé dans un appel ultérieur à `FindNextFile` ou `FindClose` . Si la fonction échoue ou ne parvient pas à trouver des fichiers à partir de la chaîne recherchée dans le paramètre *lpFileName* , la valeur de retour est INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `FindFirstFileTransacted` fonction.

## <a name="getfileattributes"></a><a name="getfileattributes"></a> GetFileAttributes

Récupère les attributs du système de fichiers d’un fichier ou d’un répertoire spécifié en tant qu’opération traitée.

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom du fichier ou du répertoire.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `GetFileAttributesTransacted` fonction.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a> GetFileAttributesEx

Récupère les attributs du système de fichiers d’un fichier ou d’un répertoire spécifié en tant qu’opération traitée.

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom du fichier ou du répertoire.

*fInfoLevelId*<br/>
Niveau des informations d’attribut à récupérer.

*lpFileInformation*<br/>
Pointeur vers une mémoire tampon qui reçoit les informations d’attribut. Le type d’informations d’attribut stocké dans cette mémoire tampon est déterminé par la valeur de *fInfoLevelId*. Si le paramètre *fInfoLevelId* est GetFileExInfoStandard, ce paramètre pointe vers une structure WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `GetFileAttributesTransacted` fonction.

## <a name="gethandle"></a><a name="gethandle"></a> GetHandle,

Retourne le handle de transaction.

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le descripteur de transaction pour une classe. Retourne la valeur NULL si `CAtlTransactionManager` n’est pas attaché à un handle.

### <a name="remarks"></a>Notes

## <a name="isfallback"></a><a name="isfallback"></a> IsFallback

Détermine si les appels de secours sont activés.

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la classe prend en charge les appels de secours. Sinon, la valeur est FALSE.

### <a name="remarks"></a>Notes

## <a name="m_bfallback"></a><a name="m_bfallback"></a> m_bFallback

TRUE si le secours est pris en charge ; FALSe dans le cas contraire.

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>Notes

## <a name="m_htransaction"></a><a name="m_htransaction"></a> m_hTransaction

Descripteur de transaction.

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Notes

## <a name="movefile"></a><a name="movefile"></a> MoveFile

Déplace un fichier existant ou un répertoire, y compris ses enfants, en tant qu’opération traitée.

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Paramètres

*lpOldFileName*<br/>
Nom actuel du fichier ou du répertoire existant sur l’ordinateur local.

*lpNewFileName*<br/>
Nouveau nom du fichier ou du répertoire. Ce nom ne doit pas déjà exister. Un nouveau fichier peut se trouver sur un autre lecteur ou système de fichiers. Un nouveau répertoire doit se trouver sur le même lecteur.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `MoveFileTransacted` fonction.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a> RegCreateKeyEx

Crée la clé de Registre spécifiée et l’associe à une transaction. Si la clé existe déjà, la fonction l’ouvre.

```cpp
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom d’une sous-clé que cette fonction ouvre ou crée.

*dwReserved*<br/>
Ce paramètre est réservé et doit être égal à zéro.

*lpClass*<br/>
Classe définie par l’utilisateur de cette clé. Ce paramètre peut être ignoré. Ce paramètre peut être NULL.

*dwOptions*<br/>
Ce paramètre peut prendre l’une des valeurs suivantes : REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE ou REG_OPTION_VOLATILE.

*samDesired*<br/>
Masque qui spécifie les droits d’accès pour la clé.

*lpSecurityAttributes*<br/>
Pointeur vers une structure SECURITY_ATTRIBUTES qui détermine si le handle retourné peut être hérité par des processus enfants. Si *lpSecurityAttributes* a la valeur null, le handle ne peut pas être hérité.

*phkResult*<br/>
Pointeur vers une variable qui reçoit un handle vers la clé ouverte ou créée. Si la clé ne fait pas partie des clés de Registre prédéfinies, appelez la `RegCloseKey` fonction une fois que vous avez fini d’utiliser le handle.

*lpdwDisposition*<br/>
Pointeur vers une variable qui reçoit l’une des valeurs de disposition suivantes : REG_CREATED_NEW_KEY ou REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `RegCreateKeyTransacted` fonction.

## <a name="regdeletekey"></a><a name="regdeletekey"></a> RegDeleteKey

Supprime une sous-clé et ses valeurs de la vue spécifique à la plateforme spécifiée du registre en tant qu’opération traitée.

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Paramètres

*hKey*\
Handle d’une clé de Registre ouverte.

*lpSubKey*\
Nom de la clé à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `RegDeleteKeyTransacted` fonction.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a> RegOpenKeyEx

Ouvre la clé de Registre spécifiée et l’associe à une transaction.

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom de la sous-clé de Registre à ouvrir.

*ulOptions*<br/>
Ce paramètre est réservé et doit être égal à zéro.

*samDesired*<br/>
Masque qui spécifie les droits d’accès pour la clé.

*phkResult*<br/>
Pointeur vers une variable qui reçoit un handle vers la clé ouverte ou créée. Si la clé ne fait pas partie des clés de Registre prédéfinies, appelez la `RegCloseKey` fonction une fois que vous avez fini d’utiliser le handle.

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h

### <a name="remarks"></a>Notes

Ce wrapper appelle la `RegOpenKeyTransacted` fonction.

## <a name="rollback"></a><a name="rollback"></a> Instruction

Demande que la transaction soit restaurée.

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Ce wrapper appelle la `RollbackTransaction` fonction.

## <a name="setfileattributes"></a><a name="setfileattributes"></a> SetFileAttributes

Définit les attributs d’un fichier ou d’un répertoire en tant qu’opération traitée.

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom du fichier ou du répertoire.

*dwAttributes*<br/>
Attributs de fichier à définir pour le fichier. Pour plus d’informations, consultez [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Notes

Ce wrapper appelle la `SetFileAttributesTransacted` fonction.

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
