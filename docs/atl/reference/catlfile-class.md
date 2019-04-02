---
title: Catlfile, classe
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
ms.openlocfilehash: 0faae50afcd26948bdcb4d4333efb25d5cca33ea
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772967"
---
# <a name="catlfile-class"></a>Catlfile, classe

Cette classe fournit un wrapper fin autour de la Windows API de gestion de fichiers.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
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
|[CAtlFile::Create](#create)|Appelez cette méthode pour créer ou ouvrir un fichier.|
|[CAtlFile::Flush](#flush)|Appelez cette méthode pour effacer les mémoires tampons pour le fichier et de provoquer de toutes les données mises en mémoire tampon à écrire dans le fichier.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Appelez cette méthode pour obtenir les résultats d’une opération avec chevauchement sur le fichier.|
|[CAtlFile::GetPosition](#getposition)|Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier à partir du fichier.|
|[CAtlFile::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille en octets du fichier.|
|[CAtlFile::LockRange](#lockrange)|Appelez cette méthode pour le verrouillage d’une région dans le fichier pour empêcher les autres processus d’y accéder.|
|[CAtlFile::Read](#read)|Appelez cette méthode pour lire des données à partir d’un fichier en commençant à la position indiquée par le pointeur de fichier.|
|[CAtlFile::Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier.|
|[CAtlFile::SetSize](#setsize)|Appelez cette méthode pour définir la taille du fichier.|
|[CAtlFile::UnlockRange](#unlockrange)|Appelez cette méthode pour déverrouiller une région du fichier.|
|[CAtlFile::Write](#write)|Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` objet|

## <a name="remarks"></a>Notes

Utilisez cette classe lorsque les besoins de gestion de fichiers sont relativement simples, mais plus d’abstraction fournit l’API Windows est nécessaire, sans inclure les dépendances MFC.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlfile.h

##  <a name="catlfile"></a>  CAtlFile::CAtlFile

Constructeur.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Paramètres

*fichier*<br/>
L’objet fichier.

*hFile*<br/>
Le handle de fichier.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Le constructeur de copie transfère la propriété du handle de fichier à partir de la version d’origine `CAtlFile` objet à l’objet nouvellement construit.

##  <a name="create"></a>  CAtlFile::Create

Appelez cette méthode pour créer ou ouvrir un fichier.

```
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
L’accès désiré. Consultez *dwDesiredAccess* dans [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) dans le SDK Windows.

*dwShareMode*<br/>
Le mode de partage. Consultez *dwShareMode* dans `CreateFile`.

*dwCreationDisposition*<br/>
La disposition de création. Consultez *dwCreationDisposition* dans `CreateFile`.

*dwFlagsAndAttributes*<br/>
Les indicateurs et les attributs. Consultez *dwFlagsAndAttributes* dans `CreateFile`.

*lpsa*<br/>
Les attributs de sécurité. Consultez *lpSecurityAttributes* dans `CreateFile`.

*hTemplateFile*<br/>
Le fichier de modèle. Consultez *hTemplateFile* dans `CreateFile`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) pour créer ou ouvrir le fichier.

##  <a name="flush"></a>  CAtlFile::Flush

Appelez cette méthode pour effacer les mémoires tampons pour le fichier et de provoquer de toutes les données mises en mémoire tampon à écrire dans le fichier.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [FlushFileBuffers](/windows/desktop/api/fileapi/nf-fileapi-flushfilebuffers) pour vider les données en mémoire tampon dans le fichier.

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

Appelez cette méthode pour obtenir les résultats d’une opération avec chevauchement sur le fichier.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Paramètres

*pOverlapped*<br/>
La structure avec chevauchement. Consultez *lpOverlapped* dans [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) dans le SDK Windows.

*dwBytesTransferred*<br/>
Les octets transférés. Consultez *lpNumberOfBytesTransferred* dans `GetOverlappedResult`.

*bWait*<br/>
L’option d’attente. Consultez *bWait* dans `GetOverlappedResult`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) pour obtenir les résultats d’une opération avec chevauchement sur le fichier.

##  <a name="getposition"></a>  CAtlFile::GetPosition

Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
La position en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) pour obtenir la position actuelle du pointeur de fichier.

##  <a name="getsize"></a>  CAtlFile::GetSize

Appelez cette méthode pour obtenir la taille en octets du fichier.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen*<br/>
Le nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [GetFileSize](/windows/desktop/api/fileapi/nf-fileapi-getfilesize) pour obtenir la taille en octets du fichier.

##  <a name="lockrange"></a>  CAtlFile::LockRange

Appelez cette méthode pour le verrouillage d’une région dans le fichier pour empêcher les autres processus d’y accéder.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Position dans le fichier où le verrou doit commencer.

*nCount*<br/>
La longueur de la plage d’octets à verrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [fichier de verrouillage](/windows/desktop/api/fileapi/nf-fileapi-lockfile) verrouillage d’une région dans le fichier. Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche n’est autorisées. Lorsque vous déverrouillez une région, à l’aide [CAtlFile::UnlockRange](#unlockrange), la plage d’octets doit correspondre exactement à la région qui a été précédemment verrouillée. `LockRange` ne fusionne pas les zones adjacentes ; Si les deux zones verrouillées sont adjacentes, vous devez déverrouiller chacune séparément.

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

Pointeur vers un `CAtlTransactionManager` objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

##  <a name="read"></a>  CAtlFile::Read

Appelez cette méthode pour lire des données à partir d’un fichier en commençant à la position indiquée par le pointeur de fichier.

```
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
La structure avec chevauchement. Consultez *lpOverlapped* dans [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
La routine d’exécution. Consultez *lpCompletionRoutine* dans [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Les trois premiers formulaires appellent [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile), le dernier [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) pour lire les données à partir du fichier. Utilisez [CAtlFile::Seek](#seek) pour déplacer le pointeur de fichier.

##  <a name="seek"></a>  CAtlFile::Seek

Appelez cette méthode pour déplacer le pointeur de fichier du fichier.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
Le décalage à partir du point de départ donné par *dwFrom*.

*dwFrom*<br/>
Le point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) pour déplacer le pointeur de fichier.

##  <a name="setsize"></a>  CAtlFile::SetSize

Appelez cette méthode pour définir la taille du fichier.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNewLen*<br/>
Nouvelle longueur du fichier en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) et [SetEndOfFile](/windows/desktop/api/fileapi/nf-fileapi-setendoffile) pour définir la taille du fichier. En retour, le pointeur de fichier est placé à la fin du fichier.

##  <a name="unlockrange"></a>  CAtlFile::UnlockRange

Appelez cette méthode pour déverrouiller une région du fichier.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Position dans le fichier où le déverrouillage doit commencer.

*nCount*<br/>
La longueur de la plage d’octets à déverrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [UnlockFile](/windows/desktop/api/fileapi/nf-fileapi-unlockfile) pour déverrouiller une région du fichier.

##  <a name="write"></a>  CAtlFile::Write

Appelez cette méthode pour écrire des données dans le fichier en commençant à la position indiquée par le pointeur de fichier.

```
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
La mémoire tampon contenant les données à écrire dans le fichier.

*nBufSize*<br/>
Le nombre d’octets à transférer à partir de la mémoire tampon.

*pOverlapped*<br/>
La structure avec chevauchement. Consultez *lpOverlapped* dans [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
La routine d’exécution. Consultez *lpCompletionRoutine* dans [WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex) dans le SDK Windows.

*pnBytesWritten*<br/>
Octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Les trois premiers formulaires appellent [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile), les appels dernière [WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex) pour écrire des données dans le fichier. Utilisez [CAtlFile::Seek](#seek) pour déplacer le pointeur de fichier.

## <a name="see-also"></a>Voir aussi

[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CHandle, classe](../../atl/reference/chandle-class.md)
