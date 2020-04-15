---
title: Classe CAtlTemporaryFile
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
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321308"
---
# <a name="catltemporaryfile-class"></a>Classe CAtlTemporaryFile

Cette classe fournit des méthodes pour la création et l’utilisation d’un fichier temporaire.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTemporaryFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Constructeur.|
|[CAtlTemporaryFile::CAtlTemporaryFile](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile::Fermer](#close)|Appelez cette méthode pour fermer un fichier temporaire et soit supprimer son contenu ou les stocker sous le nom de fichier spécifié.|
|[CAtlTemporaryFile::Créer](#create)|Appelez cette méthode pour créer un fichier temporaire.|
|[CAtlTemporaryFile::Flush](#flush)|Appelez cette méthode pour forcer toutes les données restantes dans le mémoire tampon à être écrites au fichier temporaire.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Appelez cette méthode pour obtenir la position actuelle pointeur de fichier.|
|[CAtlTemporaryFile::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille dans les octets du fichier temporaire.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Appelez cette méthode pour dissocier `CAtlTemporaryFile` le fichier de l’objet.|
|[CAtlTemporaryFile::HandsOn](#handson)|Appelez cette méthode pour ouvrir un fichier temporaire existant et positionner le pointeur à la fin du fichier.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Appelez cette méthode pour verrouiller une région dans le fichier pour empêcher d’autres processus d’y accéder.|
|[CAtlTemporaryFile::Lire](#read)|Appelez cette méthode pour lire les données du fichier temporaire à partir de la position indiquée par le pointeur de fichier.|
|[CAtlTemporaryFile::Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.|
|[CAtlTemporaryFile::SetSize](#setsize)|Appelez cette méthode pour définir la taille du fichier temporaire.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Appelez cette méthode pour retourner le nom du fichier temporaire.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Appelez cette méthode pour débloquer une région du fichier temporaire.|
|[CAtlTemporaryFile::Ecrire](#write)|Appelez cette méthode pour écrire des données au fichier temporaire à partir de la position indiquée par le pointeur de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile::opérateur HANDLE](#operator_handle)|Retourne une poignée au fichier temporaire.|

## <a name="remarks"></a>Notes

`CAtlTemporaryFile`facilite la création et l’utilisation d’un fichier temporaire. Le fichier est automatiquement nommé, ouvert, fermé et supprimé. Si le contenu du fichier est nécessaire après la fermeture du fichier, il peut être enregistré sur un nouveau fichier avec un nom spécifié.

## <a name="requirements"></a>Spécifications

**En-tête:** atlfile.h

## <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Constructeur.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Un fichier n’est pas réellement ouvert jusqu’à ce qu’un appel soit fait à [CAtlTemporaryFile::Créer](#create).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile::CAtlTemporaryFile

Destructeur.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile::Fermer

Appelez cette méthode pour fermer un fichier temporaire et soit supprimer son contenu ou les stocker sous le nom de fichier spécifié.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*szNewName (en)*<br/>
Le nom du nouveau fichier pour stocker le contenu du fichier temporaire. Si cet argument est NULL, le contenu du fichier temporaire est supprimé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile::Créer

Appelez cette méthode pour créer un fichier temporaire.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*pszDir*<br/>
Le chemin pour le dossier temporaire. Si c’est NULL, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) sera appelé à attribuer un chemin.

*dwDesiredAccess*<br/>
L’accès souhaité. Voir *dwDesiredAccess* dans [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile::Flush

Appelez cette méthode pour forcer toutes les données restantes dans le mémoire tampon à être écrites au fichier temporaire.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlTemporaryFile::HandsOff](#handsoff), sauf que le fichier n’est pas fermé.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile::GetPosition

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

Pour changer la position de pointeur de fichier, utilisez [CAtlTemporaryFile::Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile::GetSize

Appelez cette méthode pour obtenir la taille dans les octets du fichier temporaire.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen (en)*<br/>
Le nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Appelez cette méthode pour dissocier `CAtlTemporaryFile` le fichier de l’objet.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

`HandsOff`et [CAtlTemporaryFile::HandsOn](#handson) sont utilisés pour dissocier le fichier de l’objet, et le rattacher si nécessaire. `HandsOff`forcera toutes les données restantes dans le mémoire tampon à être écrites au fichier temporaire, puis fermera le fichier. Si vous souhaitez fermer et supprimer le fichier de façon permanente, ou si vous souhaitez fermer et conserver le contenu du fichier avec un nom donné, utilisez [CAtlTemporaryFile:Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Appelez cette méthode pour ouvrir un fichier temporaire existant et positionner le pointeur à la fin du fichier.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

[CAtlTemporaryFile::HandsOff](#handsoff) `HandsOn` et sont utilisés pour dissocier le fichier de l’objet, et le rattacher si nécessaire.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Appelez cette méthode pour verrouiller une région dans le fichier temporaire pour empêcher d’autres processus d’y accéder.

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

Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche ne peut être autorisée. Pour débloquer avec succès une région, utilisez [CAtlTemporaryFile::UnlockRange](#unlockrange), en veillant à ce que la plage d’byte corresponde exactement à la région qui était auparavant verrouillée. `LockRange`ne fusionne pas les régions adjacentes; si deux régions verrouillées sont adjacentes, vous devez déverrouiller chacune séparément.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile::opérateur HANDLE

Retourne une poignée au fichier temporaire.

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile::Lire

Appelez cette méthode pour lire les données du fichier temporaire à partir de la position indiquée par le pointeur de fichier.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Pointeur vers le tampon qui recevra les données lues à partir du fichier.

*nBufSize*<br/>
Taille de la mémoire tampon en octets.

*nBytesLire*<br/>
Nombre d'octets lus.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile:Lire](../../atl/reference/catlfile-class.md#read). Pour changer la position du pointeur de fichier, appelez [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile::Seek

Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset (en anglais)*<br/>
Le décalage, dans les octets, à partir du point de départ donné par *dwFrom.*

*dwDe*<br/>
Le point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Pour obtenir la position actuelle pointeur de fichier, appelez [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile::SetSize

Appelez cette méthode pour définir la taille du fichier temporaire.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNounoulen*<br/>
La nouvelle longueur du fichier dans les octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile:SetSize](../../atl/reference/catlfile-class.md#setsize). Au retour, le pointeur de fichier est positionné à la fin du fichier.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Appelez cette méthode pour retourner le nom du fichier temporaire.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie le LPCTSTR pointant vers le nom du fichier.

### <a name="remarks"></a>Notes

Le nom du fichier est généré dans [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) avec un appel à la fonction [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK. L’extension du fichier sera toujours "TFR" pour le fichier temporaire.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Appelez cette méthode pour débloquer une région du fichier temporaire.

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

Appels [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile::Ecrire

Appelez cette méthode pour écrire des données au fichier temporaire à partir de la position indiquée par le pointeur de fichier.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*<br/>
Le tampon contenant les données à écrire au fichier.

*nBufSize*<br/>
Le nombre d’octets à transférer à partir du tampon.

*pnBytesWritten (en)*<br/>
Nombre d’octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::Écrire](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CAtlFile](../../atl/reference/catlfile-class.md)
