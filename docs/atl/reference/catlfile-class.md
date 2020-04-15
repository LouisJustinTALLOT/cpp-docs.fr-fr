---
title: Classe CAtlFile
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
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318977"
---
# <a name="catlfile-class"></a>Classe CAtlFile

Cette classe fournit un emballage mince autour de l’API de gestion de fichiers Windows.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CAtlFile::Créer](#create)|Appelez cette méthode pour créer ou ouvrir un fichier.|
|[CAtlFile::Flush](#flush)|Appelez cette méthode pour effacer les tampons pour le fichier et faire écrire toutes les données tamponnées au fichier.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Appelez cette méthode pour obtenir les résultats d’une opération qui se chevauche dans le fichier.|
|[CAtlFile::GetPosition](#getposition)|Appelez cette méthode pour obtenir la position actuelle pointeur de fichier à partir du fichier.|
|[CAtlFile::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille dans les octets du fichier.|
|[CAtlFile::LockRange](#lockrange)|Appelez cette méthode pour verrouiller une région dans le fichier pour empêcher d’autres processus d’y accéder.|
|[CAtlFile::Lire](#read)|Appelez cette méthode pour lire les données d’un fichier à partir de la position indiquée par le pointeur de fichier.|
|[CAtlFile::Chercher](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier.|
|[CAtlFile::SetSize](#setsize)|Appelez cette méthode pour définir la taille du fichier.|
|[CAtlFile::UnlockRange](#unlockrange)|Appelez cette méthode pour débloquer une région du fichier.|
|[CAtlFile::Ecrire](#write)|Appelez cette méthode pour écrire des données au fichier à partir de la position indiquée par le pointeur de fichier.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Pointeur `CAtlTransactionManager` à objecter|

## <a name="remarks"></a>Notes

Utilisez cette classe lorsque les besoins de traitement des fichiers sont relativement simples, mais plus d’abstraction que l’API Windows fournit est nécessaire, sans inclure les dépendances MFC.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHandle (CHandle)](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Spécifications

**En-tête:** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

Constructeur.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Paramètres

*Fichier*<br/>
L’objet du fichier.

*hFile (en)*<br/>
La poignée de fichier.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Le constructeur de copie transfère la `CAtlFile` propriété de la poignée de fichier de l’objet d’origine à l’objet nouvellement construit.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile::Créer

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
L’accès souhaité. Voir *dwDesiredAccess* dans [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) in the Windows SDK.

*dwShareMode dwShareMode*<br/>
Le mode partage. Voir *dwShareMode* dans `CreateFile`.

*dwCreationDisposition*<br/>
La disposition de création. Voir *dwCreationDisposition* dans `CreateFile`.

*dwFlagsAndAttributes*<br/>
Les drapeaux et les attributs. Voir *dwFlagsAndAttributes* in `CreateFile`.

*lpsa lpsa*<br/>
Les attributs de sécurité. Voir *lpSecurityAttributes* in `CreateFile`.

*hTemplateFile*<br/>
Le fichier modèle. Voir *hTemplateFile* dans `CreateFile`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) pour créer ou ouvrir le fichier.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile::Flush

Appelez cette méthode pour effacer les tampons pour le fichier et faire écrire toutes les données tamponnées au fichier.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) pour rincer les données tamponnées au fichier.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

Appelez cette méthode pour obtenir les résultats d’une opération qui se chevauche dans le fichier.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Paramètres

*pOverlapped*<br/>
La structure superposée. Voir *lpOverlapped* dans [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) dans le SDK Windows.

*dwBytesTransferred*<br/>
Les octets transférés. Voir *lpNumberOfBytesTransferred* in `GetOverlappedResult`.

*appât*<br/>
L’option d’attente. Voir *appât* dans `GetOverlappedResult`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) pour obtenir les résultats d’une opération qui se chevauche sur le fichier.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile::GetPosition

Appelez cette méthode pour obtenir la position actuelle pointeur de fichier.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
La position dans les octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) pour obtenir la position actuelle de pointeur de fichier.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile::GetSize

Appelez cette méthode pour obtenir la taille dans les octets du fichier.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen (en)*<br/>
Le nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) pour obtenir la taille dans les octets du fichier.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Appelez cette méthode pour verrouiller une région dans le fichier pour empêcher d’autres processus d’y accéder.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
La position dans le fichier où le verrou doit commencer.

*nCompte*<br/>
La longueur de la plage d’ense de fourre-tout à verrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle [LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile) pour verrouiller une région dans le fichier. Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche ne peut être autorisée. Lorsque vous déverrouillez une région, en utilisant [CAtlFile::UnlockRange](#unlockrange), la gamme byte doit correspondre exactement à la région qui était auparavant verrouillée. `LockRange`ne fusionne pas les régions adjacentes; si deux régions verrouillées sont adjacentes, vous devez déverrouiller chacune séparément.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile::m_pTM

Pointeur `CAtlTransactionManager` vers un objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

## <a name="catlfileread"></a><a name="read"></a>CAtlFile::Lire

Appelez cette méthode pour lire les données d’un fichier à partir de la position indiquée par le pointeur de fichier.

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
Pointeur vers le tampon qui recevra les données lues à partir du fichier.

*nBufSize*<br/>
Taille de la mémoire tampon en octets.

*nBytesLire*<br/>
Nombre d'octets lus.

*pOverlapped*<br/>
La structure superposée. Voir *lpOverlapped* dans [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
La routine d’achèvement. Voir *lpCompletionRoutine* dans [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Les trois premiers formulaires appellent [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), le dernier [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) à lire les données du fichier. Utilisez [CAtlFile::Chercher](#seek) à déplacer le pointeur de fichier.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile::Chercher

Appelez cette méthode pour déplacer le pointeur de fichier du fichier.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset (en anglais)*<br/>
Le décalage à partir du point de départ donné par *dwFrom*.

*dwDe*<br/>
Le point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) pour déplacer le pointeur de fichier.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile::SetSize

Appelez cette méthode pour définir la taille du fichier.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNounoulen*<br/>
La nouvelle longueur du fichier dans les octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) et [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) pour définir la taille du fichier. Au retour, le pointeur de fichier est positionné à la fin du fichier.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Appelez cette méthode pour débloquer une région du fichier.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
La position dans le fichier où le déverrouillage doit commencer.

*nCompte*<br/>
La longueur de la plage d’ente à déverrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) pour débloquer une région du fichier.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile::Ecrire

Appelez cette méthode pour écrire des données au fichier à partir de la position indiquée par le pointeur de fichier.

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
Le tampon contenant les données à écrire au fichier.

*nBufSize*<br/>
Le nombre d’octets à transférer à partir du tampon.

*pOverlapped*<br/>
La structure superposée. Voir *lpOverlapped* dans [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) dans le SDK Windows.

*pfnCompletionRoutine*<br/>
La routine d’achèvement. Voir *lpCompletionRoutine* dans [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) dans le Windows SDK.

*pnBytesWritten (en)*<br/>
Les octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Les trois premiers formulaires appellent [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), les derniers appels [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) pour écrire des données sur le fichier. Utilisez [CAtlFile::Chercher](#seek) à déplacer le pointeur de fichier.

## <a name="see-also"></a>Voir aussi

[Échantillon de marquee](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CHandle](../../atl/reference/chandle-class.md)
