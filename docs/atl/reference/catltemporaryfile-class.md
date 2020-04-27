---
title: CAtlTemporaryFile, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: f3d0be66bf0b5a6c07a72c8ae6cc9c90e176728f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167888"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile, classe

Cette classe fournit des méthodes pour la création et l’utilisation d’un fichier temporaire.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlTemporaryFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Constructeur.|
|[CAtlTemporaryFile :: ~ CAtlTemporaryFile](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile :: Close](#close)|Appelez cette méthode pour fermer un fichier temporaire et supprimer son contenu ou le stocker sous le nom de fichier spécifié.|
|[CAtlTemporaryFile :: Create](#create)|Appelez cette méthode pour créer un fichier temporaire.|
|[CAtlTemporaryFile :: Flush](#flush)|Appelez cette méthode pour forcer l’écriture dans le fichier temporaire des données restantes dans la mémoire tampon de fichier.|
|[CAtlTemporaryFile :: GetPosition](#getposition)|Appelez cette méthode pour atteindre la position actuelle du pointeur de fichier.|
|[CAtlTemporaryFile :: est à obtenir](#getsize)|Appelez cette méthode pour récupérer la taille en octets du fichier temporaire.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Appelez cette méthode pour dissocier le fichier de l' `CAtlTemporaryFile` objet.|
|[CAtlTemporaryFile :: HandsOn](#handson)|Appelez cette méthode pour ouvrir un fichier temporaire existant et positionner le pointeur à la fin du fichier.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Appelez cette méthode pour verrouiller une région dans le fichier afin d’empêcher d’autres processus d’y accéder.|
|[CAtlTemporaryFile :: lecture](#read)|Appelez cette méthode pour lire les données du fichier temporaire en commençant à la position indiquée par le pointeur de fichier.|
|[CAtlTemporaryFile :: Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.|
|[CAtlTemporaryFile :: configure](#setsize)|Appelez cette méthode pour définir la taille du fichier temporaire.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Appelez cette méthode pour retourner le nom du fichier temporaire.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Appelez cette méthode pour déverrouiller une région du fichier temporaire.|
|[CAtlTemporaryFile :: Write](#write)|Appelez cette méthode pour écrire des données dans le fichier temporaire en commençant à la position indiquée par le pointeur de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[HANDLE CAtlTemporaryFile :: Operator](#operator_handle)|Retourne un handle vers le fichier temporaire.|

## <a name="remarks"></a>Notes

`CAtlTemporaryFile`facilite la création et l’utilisation d’un fichier temporaire. Le fichier est automatiquement nommé, ouvert, fermé et supprimé. Si le contenu du fichier est nécessaire une fois que le fichier est fermé, il peut être enregistré dans un nouveau fichier avec un nom spécifié.

## <a name="requirements"></a>Spécifications

**En-tête :** atlfile. h

## <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Constructeur.

```cpp
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Un fichier n’est pas réellement ouvert tant qu’un appel à [CAtlTemporaryFile :: Create](#create)n’a pas été effectué.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile :: ~ CAtlTemporaryFile

Destructeur.

```cpp
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [CAtlTemporaryFile :: Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile :: Close

Appelez cette méthode pour fermer un fichier temporaire et supprimer son contenu ou le stocker sous le nom de fichier spécifié.

```cpp
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*szNewName*<br/>
Nom du nouveau fichier dans lequel stocker le contenu du fichier temporaire. Si cet argument a la valeur NULL, le contenu du fichier temporaire est supprimé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile :: Create

Appelez cette méthode pour créer un fichier temporaire.

```cpp
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*pszDir*<br/>
Chemin d’accès du fichier temporaire. Si la valeur est NULL, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) est appelé pour assigner un chemin d’accès.

*dwDesiredAccess*<br/>
Accès souhaité. Consultez *dwDesiredAccess* dans [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile :: Flush

Appelez cette méthode pour forcer l’écriture dans le fichier temporaire des données restantes dans la mémoire tampon de fichier.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlTemporaryFile :: HandsOff](#handsoff), sauf que le fichier n’est pas fermé.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile :: GetPosition

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

Pour modifier la position du pointeur de fichier, utilisez [CAtlTemporaryFile :: Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile :: est à obtenir

Appelez cette méthode pour récupérer la taille en octets du fichier temporaire.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen*<br/>
Nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Appelez cette méthode pour dissocier le fichier de l' `CAtlTemporaryFile` objet.

```cpp
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

`HandsOff`et [CAtlTemporaryFile :: HandsOn](#handson) sont utilisés pour dissocier le fichier de l’objet et le rattacher si nécessaire. `HandsOff`force l’écriture de toutes les données restantes dans le tampon de fichier dans le fichier temporaire, puis ferme le fichier. Si vous souhaitez fermer et supprimer définitivement le fichier, ou si vous souhaitez fermer et conserver le contenu du fichier avec un nom donné, utilisez [CAtlTemporaryFile :: Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile :: HandsOn

Appelez cette méthode pour ouvrir un fichier temporaire existant et positionner le pointeur à la fin du fichier.

```cpp
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

[CAtlTemporaryFile :: HandsOff](#handsoff) et `HandsOn` sont utilisés pour dissocier le fichier de l’objet et le rattacher si nécessaire.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Appelez cette méthode pour verrouiller une région dans le fichier temporaire afin d’empêcher d’autres processus d’y accéder.

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

Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plusieurs régions d’un fichier, mais aucune région se chevauchant n’est autorisée. Pour déverrouiller correctement une région, utilisez [CAtlTemporaryFile :: UnlockRange](#unlockrange), en veillant à ce que la plage d’octets corresponde exactement à la région précédemment verrouillée. `LockRange`ne fusionne pas les régions adjacentes ; Si deux régions verrouillées sont adjacentes, vous devez déverrouiller chacune d’elles séparément.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>HANDLE CAtlTemporaryFile :: Operator

Retourne un handle vers le fichier temporaire.

```cpp
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile :: lecture

Appelez cette méthode pour lire les données du fichier temporaire en commençant à la position indiquée par le pointeur de fichier.

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Pointeur vers la mémoire tampon qui recevra les données lues à partir du fichier.

*nBufSize*<br/>
Taille de la mémoire tampon en octets.

*nBytesRead*<br/>
Nombre d'octets lus.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [CAtlFile :: Read](../../atl/reference/catlfile-class.md#read). Pour modifier la position du pointeur de fichier, appelez [CAtlTemporaryFile :: Seek](#seek).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile :: Seek

Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.

```cpp
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
Offset, en octets, à partir du point de départ donné par *dwFrom.*

*dwFrom*<br/>
Point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [CAtlFile :: Seek](../../atl/reference/catlfile-class.md#seek). Pour obtenir la position actuelle du pointeur de fichier, appelez [CAtlTemporaryFile :: GetPosition](#getposition).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile :: configure

Appelez cette méthode pour définir la taille du fichier temporaire.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNewLen*<br/>
Nouvelle longueur du fichier, en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [CAtlFile :: assets](../../atl/reference/catlfile-class.md#setsize). Au retour, le pointeur de fichier est positionné à la fin du fichier.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Appelez cette méthode pour retourner le nom du fichier temporaire.

```cpp
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le LPCTSTR pointant vers le nom de fichier.

### <a name="remarks"></a>Notes

Le nom de fichier est généré dans [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile) avec un appel à la fonction [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)SDK Windows. L’extension de fichier est toujours « TFR » pour le fichier temporaire.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Appelez cette méthode pour déverrouiller une région du fichier temporaire.

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

Appelle [CAtlFile :: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile :: Write

Appelez cette méthode pour écrire des données dans le fichier temporaire en commençant à la position indiquée par le pointeur de fichier.

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Mémoire tampon contenant les données à écrire dans le fichier.

*nBufSize*<br/>
Nombre d’octets à transférer à partir de la mémoire tampon.

*pnBytesWritten*<br/>
Nombre d’octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle [CAtlFile :: Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile :: CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CAtlFile, classe](../../atl/reference/catlfile-class.md)
