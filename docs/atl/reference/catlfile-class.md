---
title: CAtlFile, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 83a0a89bf6e2e21be33cf8c6003228111eff5394
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168109"
---
# <a name="catlfile-class"></a>CAtlFile, classe

Cette classe fournit un wrapper fin autour de l’API de gestion des fichiers Windows.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlFile : public CHandle
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlFile :: Create](#create)|Appelez cette méthode pour créer ou ouvrir un fichier.|
|[CAtlFile :: Flush](#flush)|Appelez cette méthode pour effacer les mémoires tampons pour le fichier et provoquer l’écriture de toutes les données mises en mémoire tampon dans le fichier.|
|[CAtlFile :: GetOverlappedResult](#getoverlappedresult)|Appelez cette méthode pour obtenir les résultats d’une opération Overlapped sur le fichier.|
|[CAtlFile :: GetPosition](#getposition)|Appelez cette méthode pour récupérer la position actuelle du pointeur de fichier à partir du fichier.|
|[CAtlFile :: est à obtenir](#getsize)|Appelez cette méthode pour récupérer la taille en octets du fichier.|
|[CAtlFile::LockRange](#lockrange)|Appelez cette méthode pour verrouiller une région dans le fichier afin d’empêcher d’autres processus d’y accéder.|
|[CAtlFile :: lecture](#read)|Appelez cette méthode pour lire les données d’un fichier en commençant à la position indiquée par le pointeur de fichier.|
|[CAtlFile :: Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier.|
|[CAtlFile :: configure](#setsize)|Appelez cette méthode pour définir la taille du fichier.|
|[CAtlFile::UnlockRange](#unlockrange)|Appelez cette méthode pour déverrouiller une région du fichier.|
|[CAtlFile :: Write](#write)|Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAtlFile :: m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` un objet|

## <a name="remarks"></a>Notes

Utilisez cette classe lorsque les besoins en matière de gestion des fichiers sont relativement simples, mais qu’une abstraction plus grande que celle fournie par l’API Windows est requise, sans inclure les dépendances MFC.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Spécifications

**En-tête :** atlfile. h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

Constructeur.

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Paramètres

*txt*<br/>
Objet de fichier.

*hFile*<br/>
Descripteur de fichier.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Le constructeur de copie transfère la propriété du handle de fichier de `CAtlFile` l’objet d’origine vers l’objet nouvellement construit.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile :: Create

Appelez cette méthode pour créer ou ouvrir un fichier.

```cpp
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*szFilename*<br/>
Nom du fichier.

*dwDesiredAccess*<br/>
Accès souhaité. Consultez *dwDesiredAccess* dans [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) dans le SDK Windows.

*dwShareMode*<br/>
Mode de partage. Consultez *dwShareMode* dans `CreateFile`.

*dwCreationDisposition*<br/>
Disposition de la création. Consultez *dwCreationDisposition* dans `CreateFile`.

*dwFlagsAndAttributes*<br/>
Indicateurs et attributs. Consultez *dwFlagsAndAttributes* dans `CreateFile`.

*lpsa*<br/>
Attributs de sécurité. Consultez *lpSecurityAttributes* dans `CreateFile`.

*hTemplateFile*<br/>
Fichier de modèle. Consultez *hTemplateFile* dans `CreateFile`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) pour créer ou ouvrir le fichier.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile :: Flush

Appelez cette méthode pour effacer les mémoires tampons pour le fichier et provoquer l’écriture de toutes les données mises en mémoire tampon dans le fichier.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) pour vider les données mises en mémoire tampon dans le fichier.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile :: GetOverlappedResult

Appelez cette méthode pour obtenir les résultats d’une opération Overlapped sur le fichier.

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Paramètres

*pOverlapped*<br/>
Structure OVERLAPPED. Consultez *lpOverlapped* dans [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) dans le SDK Windows.

*dwBytesTransferred*<br/>
Octets transférés. Consultez *lpNumberOfBytesTransferred* dans `GetOverlappedResult`.

*bWait*<br/>
Option wait. Consultez *bWait* dans `GetOverlappedResult`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) pour obtenir les résultats d’une opération Overlapped sur le fichier.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile :: GetPosition

Appelez cette méthode pour atteindre la position actuelle du pointeur de fichier.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Position en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) pour atteindre la position actuelle du pointeur de fichier.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile :: est à obtenir

Appelez cette méthode pour récupérer la taille en octets du fichier.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen*<br/>
Nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) pour récupérer la taille en octets du fichier.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Appelez cette méthode pour verrouiller une région dans le fichier afin d’empêcher d’autres processus d’y accéder.

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Position dans le fichier où le verrou doit commencer.

*nCount*<br/>
Longueur de la plage d’octets à verrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [lockfile](/windows/win32/api/fileapi/nf-fileapi-lockfile) pour verrouiller une région dans le fichier. Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plusieurs régions d’un fichier, mais aucune région se chevauchant n’est autorisée. Lorsque vous déverrouillez une région à l’aide de [CAtlFile :: UnlockRange](#unlockrange), la plage d’octets doit correspondre exactement à la région précédemment verrouillée. `LockRange`ne fusionne pas les régions adjacentes ; Si deux régions verrouillées sont adjacentes, vous devez déverrouiller chacune d’elles séparément.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile :: m_pTM

Pointeur vers un `CAtlTransactionManager` objet.

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

## <a name="catlfileread"></a><a name="read"></a>CAtlFile :: lecture

Appelez cette méthode pour lire les données d’un fichier en commençant à la position indiquée par le pointeur de fichier.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Pointeur vers la mémoire tampon qui recevra les données lues à partir du fichier.

*nBufSize*<br/>
Taille de la mémoire tampon en octets.

*nBytesRead*<br/>
Nombre d'octets lus.

*pOverlapped*<br/>
Structure OVERLAPPED. Consultez *lpOverlapped* dans [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
Routine de saisie semi-automatique. Consultez *lpCompletionRoutine* dans [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Les trois premières formes appellent [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), le dernier [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) pour lire les données à partir du fichier. Utilisez [CAtlFile :: Seek](#seek) pour déplacer le pointeur de fichier.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile :: Seek

Appelez cette méthode pour déplacer le pointeur de fichier du fichier.

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
Offset à partir du point de départ donné par *dwFrom*.

*dwFrom*<br/>
Point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) pour déplacer le pointeur de fichier.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile :: configure

Appelez cette méthode pour définir la taille du fichier.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNewLen*<br/>
Nouvelle longueur du fichier, en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) et [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) pour définir la taille du fichier. Au retour, le pointeur de fichier est positionné à la fin du fichier.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Appelez cette méthode pour déverrouiller une région du fichier.

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Position dans le fichier où le déverrouillage doit commencer.

*nCount*<br/>
Longueur de la plage d’octets à déverrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) pour déverrouiller une région du fichier.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile :: Write

Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Mémoire tampon contenant les données à écrire dans le fichier.

*nBufSize*<br/>
Nombre d’octets à transférer à partir de la mémoire tampon.

*pOverlapped*<br/>
Structure OVERLAPPED. Consultez *lpOverlapped* dans [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
Routine de saisie semi-automatique. Consultez *lpCompletionRoutine* dans [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) dans le SDK Windows.

*pnBytesWritten*<br/>
Octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Les trois premières formes appellent [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), le dernier appelle [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) pour écrire des données dans le fichier. Utilisez [CAtlFile :: Seek](#seek) pour déplacer le pointeur de fichier.

## <a name="see-also"></a>Voir aussi

[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CHandle, classe](../../atl/reference/chandle-class.md)
