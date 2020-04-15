---
title: Classe CAtlTransactionManager
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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321326"
---
# <a name="catltransactionmanager-class"></a>Classe CAtlTransactionManager

La classe CAtlTransactionManager fournit un emballage aux fonctions kernel Transaction Manager (KTM).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTransactionManager;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlTransactionManager](#dtor)|CAtlTransactionManager destructeur.|
|[CAtlTransactionManager](#catltransactionmanager)|Constructeur CAtlTransactionManager.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Fermer](#close)|Ferme un de la poignée de transaction.|
|[Commit](#commit)|Demande que la transaction soit validée.|
|[Créer](#create)|Crée la poignée de transaction.|
|[CreateFile](#createfile)|Crée ou ouvre un fichier, un flux de fichiers ou un répertoire en tant qu’opération de transaction.|
|[DeleteFile](#deletefile)|Supprime un fichier existant en tant qu’opération transactionnée.|
|[FindFirstFile (en)](#findfirstfile)|Recherche un répertoire pour un fichier ou une sous-direction en tant qu’opération de transigement.|
|[GetFileAttributes](#getfileattributes)|Récupère les attributs du système de fichiers pour un fichier ou un répertoire spécifié en tant qu’opération de transaction.|
|[GetFileAttributesEx](#getfileattributesex)|Récupère les attributs du système de fichiers pour un fichier ou un répertoire spécifié en tant qu’opération de transaction.|
|[GetHandle GetHandle](#gethandle)|Retourne la poignée de transaction.|
|[IsFallback (en)](#isfallback)|Détermine si les appels de repli sont activés.|
|[MoveFile](#movefile)|Déplace un fichier existant ou un répertoire, y compris ses enfants, comme une opération de transaction.|
|[RegCreateKeyEx](#regcreatekeyex)|Crée la clé de registre spécifiée et l’associe à une transaction. Si la clé existe déjà, la fonction l’ouvre.|
|[RegDeleteKey (en)](#regdeletekey)|Supprime un sous-clé et ses valeurs de la vue spécifique à la plate-forme spécifiée du registre comme une opération de transaction.|
|[RegOpenKeyEx](#regopenkeyex)|Ouvre la clé de registre spécifiée et l’associe à une transaction.|
|[Restauration](#rollback)|Demande que la transaction soit annulée.|
|[SetFileAttributes](#setfileattributes)|Définit les attributs d’un fichier ou d’un répertoire en tant qu’opération de transaction.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|VRAI si le repli est pris en charge; FALSE autrement.|
|[m_hTransaction](#m_htransaction)|La poignée de transaction.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** atltransactionmanager.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>CAtlTransactionManager

CAtlTransactionManager destructeur.

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Notes

Dans le traitement normal, la transaction est automatiquement validée et fermée. Si le destructeur est appelé lors d’une exception décompressée, la transaction est annulée et fermée.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Constructeur CAtlTransactionManager.

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Paramètres

*bFallback (en)*<br/>
TRUE indique le recul de soutien. En cas d’échec de la fonction de transaction, la classe appelle automatiquement la fonction « non-transacted ». FALSE n’indique aucun appel « de repli ».

*bAutoCreateTransaction*<br/>
TRUE indique que le gestionnaire de transaction est créé automatiquement dans le constructeur. FALSE indique que ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="close"></a><a name="close"></a>Proche

Ferme la poignée de transaction.

```
inline BOOL Close();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Cet emballage appelle `CloseHandle` la fonction. La méthode est automatiquement appelée dans le destructeur.

## <a name="commit"></a><a name="commit"></a>Commettre

Demande que la transaction soit validée.

```
inline BOOL Commit();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Cet emballage appelle `CommitTransaction` la fonction. La méthode est automatiquement appelée dans le destructeur.

## <a name="create"></a><a name="create"></a>Créer

Crée la poignée de transaction.

```
inline BOOL Create();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Cet emballage appelle `CreateTransaction` la fonction. Vérifiez-le pour

## <a name="createfile"></a><a name="createfile"></a>Createfile

Crée ou ouvre un fichier, un flux de fichiers ou un répertoire en tant qu’opération de transaction.

```
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
Le nom d’un objet à créer ou à ouvrir.

*dwDesiredAccess*<br/>
L’accès à l’objet, qui peut être résumé comme lu, écrire, les deux, ou ni l’un ni l’autre (zéro). Les valeurs les plus couramment utilisées sont les GENERIC_READ, les GENERIC_WRITE ou les deux : GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode dwShareMode*<br/>
Le mode de partage d’un objet, qui peut être lu, écrire, les deux, supprimer, tous ceux-ci, ou aucun: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Un pointeur d’une structure SECURITY_ATTRIBUTES qui contient un descripteur de sécurité optionnel et détermine également si la poignée retournée peut être héritée par les processus de l’enfant. Le paramètre peut être NULL.

*dwCreationDisposition*<br/>
Une mesure à prendre sur les fichiers qui existent et n’existent pas. Ce paramètre doit être l’une des valeurs suivantes, qui ne peut être combiné : CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING ou TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Le fichier attribue et les drapeaux. Ce paramètre peut inclure n’importe quelle combinaison des attributs de fichiers disponibles (FILE_ATTRIBUTE_). Tous les autres attributs de fichier remplacent FILE_ATTRIBUTE_NORMAL. Ce paramètre peut également contenir des combinaisons de drapeaux (FILE_FLAG_\*) pour le contrôle du comportement tampon, des modes d’accès et d’autres drapeaux à usage spécial. Celles-ci se combinent\* avec toutes les valeurs FILE_ATTRIBUTE_.

*hTemplateFile*<br/>
Une poignée valide à un fichier de modèle avec le droit d’accès GENERIC_READ. Le fichier modèle fournit des attributs et des attributs étendus pour le fichier qui est en cours de création. Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne une poignée qui peut être utilisée pour accéder à l’objet.

### <a name="remarks"></a>Notes

Cet emballage appelle `CreateFileTransacted` la fonction.

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile (DeleteFile)

Supprime un fichier existant en tant qu’opération transactionnée.

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Nom du fichier à supprimer.

### <a name="remarks"></a>Notes

Cet emballage appelle `DeleteFileTransacted` la fonction.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile (en)

Recherche un répertoire pour un fichier ou une sous-direction en tant qu’opération de transigement.

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
L’annuaire ou le chemin, et le nom du fichier à rechercher. Ce paramètre peut inclure des caractères wildcard, tels qu’un astérisque (MD) ou un point d’interrogation ().

*pNextInfo*<br/>
Un pointeur à la structure WIN32_FIND_DATA qui reçoit des informations sur un fichier trouvé ou sous-direction.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est `FindNextFile` `FindClose`une poignée de recherche utilisée dans un appel ultérieur à ou . Si la fonction échoue ou ne parvient pas à localiser les fichiers de la chaîne de recherche dans le *paramètre lpFileName,* la valeur de retour est INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Notes

Cet emballage appelle `FindFirstFileTransacted` la fonction.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Récupère les attributs du système de fichiers pour un fichier ou un répertoire spécifié en tant qu’opération de transaction.

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Le nom du fichier ou de l’annuaire.

### <a name="remarks"></a>Notes

Cet emballage appelle `GetFileAttributesTransacted` la fonction.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Récupère les attributs du système de fichiers pour un fichier ou un répertoire spécifié en tant qu’opération de transaction.

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Le nom du fichier ou de l’annuaire.

*fInfoLevelId*<br/>
Le niveau d’information d’attribut à récupérer.

*lpFileInformation*<br/>
Un pointeur à un tampon qui reçoit les informations d’attribut. Le type d’informations d’attribut qui est stockée dans ce tampon est déterminé par la valeur de *fInfoLevelId*. Si le *paramètre fInfoLevelId* est GetFileExInfoStandard, ce paramètre indique une structure WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Notes

Cet emballage appelle `GetFileAttributesTransacted` la fonction.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle GetHandle

Retourne la poignée de transaction.

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée de transaction pour une classe. Retourne NULL `CAtlTransactionManager` si le n’est pas attaché à une poignée.

### <a name="remarks"></a>Notes

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback (en)

Détermine si les appels de repli sont activés.

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>Valeur de retour

Returns TRUE est la classe prend en charge les appels de repli. Sinon, la valeur est FALSE.

### <a name="remarks"></a>Notes

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

VRAI si le repli est pris en charge; FALSE autrement.

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Notes

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

La poignée de transaction.

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Notes

## <a name="movefile"></a><a name="movefile"></a>MoveFile (MoveFile)

Déplace un fichier existant ou un répertoire, y compris ses enfants, comme une opération de transaction.

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Paramètres

*lpOldFileName*<br/>
Le nom actuel du fichier ou de l’annuaire existant sur l’ordinateur local.

*lpNewFileName*<br/>
Le nouveau nom pour le fichier ou l’annuaire. Ce nom ne doit pas déjà exister. Un nouveau fichier peut être sur un système de fichiers ou un lecteur différent. Un nouvel annuaire doit être sur le même disque.

### <a name="remarks"></a>Notes

Cet emballage appelle `MoveFileTransacted` la fonction.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Crée la clé de registre spécifiée et l’associe à une transaction. Si la clé existe déjà, la fonction l’ouvre.

```
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

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom d’un sous-clé que cette fonction ouvre ou crée.

*dwReserved*<br/>
Ce paramètre est réservé et doit être nul.

*lpClass*<br/>
La classe définie par l’utilisateur de cette clé. Ce paramètre peut être ignoré. Ce paramètre peut être NULL.

*dwOptions*<br/>
Ce paramètre peut être l’une des valeurs suivantes : REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE ou REG_OPTION_VOLATILE.

*samDesired*<br/>
Un masque qui spécifie les droits d’accès à la clé.

*lpSecurityAttributes*<br/>
Pointeur vers une structure SECURITY_ATTRIBUTES qui détermine si le handle retourné peut être hérité par des processus enfants. Si *lpSecurityAttributes* est NULL, la poignée ne peut pas être héritée.

*phkResult*<br/>
Un pointeur à une variable qui reçoit une poignée à la clé ouverte ou créée. Si la clé n’est pas l’une des `RegCloseKey` clés de registre prédéfinies, appelez la fonction après avoir fini d’utiliser la poignée.

*lpdwDisposition*<br/>
Pointeur d’une variable qui reçoit l’une des valeurs de disposition suivantes : REG_CREATED_NEW_KEY ou REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="remarks"></a>Notes

Cet emballage appelle `RegCreateKeyTransacted` la fonction.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey (en)

Supprime un sous-clé et ses valeurs de la vue spécifique à la plate-forme spécifiée du registre comme une opération de transaction.

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*hKey (en)*|Une poignée à une clé de registre ouvert.|
|*lpSubKey*|Le nom de la clé à supprimer.|

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="remarks"></a>Notes

Cet emballage appelle `RegDeleteKeyTransacted` la fonction.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

Ouvre la clé de registre spécifiée et l’associe à une transaction.

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom du sous-clé du registre à ouvrir.

*ulOptions*<br/>
Ce paramètre est réservé et doit être nul.

*samDesired*<br/>
Un masque qui spécifie les droits d’accès à la clé.

*phkResult*<br/>
Un pointeur à une variable qui reçoit une poignée à la clé ouverte ou créée. Si la clé n’est pas l’une des `RegCloseKey` clés de registre prédéfinies, appelez la fonction après avoir fini d’utiliser la poignée.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h

### <a name="remarks"></a>Notes

Cet emballage appelle `RegOpenKeyTransacted` la fonction.

## <a name="rollback"></a><a name="rollback"></a>Restauration

Demande que la transaction soit annulée.

```
inline BOOL Rollback();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Cet emballage appelle `RollbackTransaction` la fonction.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

Définit les attributs d’un fichier ou d’un répertoire en tant qu’opération de transaction.

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Paramètres

*lpFileName*<br/>
Le nom du fichier ou de l’annuaire.

*dwAttributes*<br/>
Le fichier attribue à définir pour le fichier. Pour plus d’informations, voir [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Notes

Cet emballage appelle `SetFileAttributesTransacted` la fonction.

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
