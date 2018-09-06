---
title: Catltemporaryfile, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30a0080dd576add0433421bb465d89b2967b9acd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753121"
---
# <a name="catltemporaryfile-class"></a>Catltemporaryfile, classe

Cette classe fournit des méthodes pour la création et l’utilisation d’un fichier temporaire.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
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
|[CAtlTemporaryFile::Close](#close)|Appelez cette méthode pour fermer un fichier temporaire et soit supprimer son contenu ou les stocker sous le nom de fichier spécifié.|
|[CAtlTemporaryFile::Create](#create)|Appelez cette méthode pour créer un fichier temporaire.|
|[CAtlTemporaryFile::Flush](#flush)|Appelez cette méthode pour forcer les données restantes dans la mémoire tampon de fichier à écrire dans le fichier temporaire.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier.|
|[CAtlTemporaryFile::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille en octets du fichier temporaire.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Appelez cette méthode pour dissocier le fichier à partir de la `CAtlTemporaryFile` objet.|
|[CAtlTemporaryFile::HandsOn](#handson)|Appelez cette méthode pour ouvrir un fichier temporaire existant et placez le pointeur à la fin du fichier.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Appelez cette méthode pour le verrouillage d’une région dans le fichier pour empêcher les autres processus d’y accéder.|
|[CAtlTemporaryFile::Read](#read)|Appelez cette méthode pour lire les données à partir du fichier temporaire, en commençant à la position indiquée par le pointeur de fichier.|
|[CAtlTemporaryFile::Seek](#seek)|Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.|
|[CAtlTemporaryFile::SetSize](#setsize)|Appelez cette méthode pour définir la taille du fichier temporaire.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Appelez cette méthode pour retourner le nom du fichier temporaire.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Appelez cette méthode pour déverrouiller une région du fichier temporaire.|
|[CAtlTemporaryFile::Write](#write)|Appelez cette méthode pour écrire des données dans le fichier temporaire, en commençant à la position indiquée par le pointeur de fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlTemporaryFile::operator HANDLE](#operator_handle)|Retourne un handle vers le fichier temporaire.|

## <a name="remarks"></a>Notes

`CAtlTemporaryFile` rend plus facile créer et utiliser un fichier temporaire. Le fichier est automatiquement nommé ouvert, fermé et supprimé. Si le contenu du fichier est nécessaire une fois que le fichier est fermé, ils peuvent être enregistrés dans un nouveau fichier avec un nom spécifié.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlfile.h

## <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

Constructeur.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Un fichier n’est pas ouvert jusqu'à ce qu’un appel est effectué pour [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>  CAtlTemporaryFile :: ~ CAtlTemporaryFile

Destructeur.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [CAtlTemporaryFile::Close](#close).

##  <a name="close"></a>  CAtlTemporaryFile::Close

Appelez cette méthode pour fermer un fichier temporaire et soit supprimer son contenu ou les stocker sous le nom de fichier spécifié.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*szNewName*  
Le nom du nouveau fichier stocker le contenu du fichier temporaire dans. Si cet argument est NULL, le contenu du fichier temporaire est supprimé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>  CAtlTemporaryFile::Create

Appelez cette méthode pour créer un fichier temporaire.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*pszDir*  
Le chemin d’accès pour le fichier temporaire. Si ce paramètre est NULL, [GetTempPath](/windows/desktop/api/fileapi/nf-fileapi-gettemppatha) sera appelé pour affecter un chemin d’accès.

*dwDesiredAccess*  
L’accès désiré. Consultez *dwDesiredAccess* dans [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>  CAtlTemporaryFile::Flush

Appelez cette méthode pour forcer les données restantes dans la mémoire tampon de fichier à écrire dans le fichier temporaire.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlTemporaryFile::HandsOff](#handsoff), sauf que le fichier n’est pas fermé.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

Appelez cette méthode pour obtenir la position actuelle du pointeur de fichier.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Paramètres

*nPos*  
La position en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Pour modifier la position du pointeur de fichier, utilisez [CAtlTemporaryFile::Seek](#seek).

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

Appelez cette méthode pour obtenir la taille en octets du fichier temporaire.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Paramètres

*nLen*  
Le nombre d’octets dans le fichier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff

Appelez cette méthode pour dissocier le fichier à partir de la `CAtlTemporaryFile` objet.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`HandsOff` et [CAtlTemporaryFile::HandsOn](#handson) servent à dissocier le fichier à partir de l’objet et la rattachez à si nécessaire. `HandsOff` sera forcer les données restantes dans la mémoire tampon de fichier à écrire dans le fichier temporaire, puis fermez le fichier. Si vous souhaitez fermer et supprimer le fichier de façon permanente, ou si vous souhaitez fermer et conserver le contenu du fichier avec un nom donné, utilisez [CAtlTemporaryFile::Close](#close).

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

Appelez cette méthode pour ouvrir un fichier temporaire existant et placez le pointeur à la fin du fichier.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

[CAtlTemporaryFile::HandsOff](#handsoff) et `HandsOn` servent à dissocier le fichier à partir de l’objet et la rattachez à si nécessaire.

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

Appelez cette méthode pour le verrouillage d’une région dans le fichier temporaire pour empêcher les autres processus d’y accéder.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*  
Position dans le fichier où le verrou doit commencer.

*nCount*  
La longueur de la plage d’octets à verrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche n’est autorisées. Pour déverrouiller avec succès une région, utilisez [CAtlTemporaryFile::UnlockRange](#unlockrange), en garantissant la plage d’octets correspond exactement à la région qui a été précédemment verrouillée. `LockRange` ne fusionne pas les zones adjacentes ; Si les deux zones verrouillées sont adjacentes, vous devez déverrouiller chacune séparément.

##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator HANDLE

Retourne un handle vers le fichier temporaire.

```  
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

Appelez cette méthode pour lire les données à partir du fichier temporaire, en commençant à la position indiquée par le pointeur de fichier.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*  
Pointeur vers la mémoire tampon qui recevra les données lues à partir du fichier.

*nBufSize*  
Taille de la mémoire tampon en octets.

*nBytesRead*  
Nombre d'octets lus.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Pour modifier la position du pointeur de fichier, appelez [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

Appelez cette méthode pour déplacer le pointeur de fichier du fichier temporaire.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Paramètres

*nOffset*  
Offset, en octets, du point de départ donnée par *dwFrom.*

*dwFrom*  
Le point de départ (FILE_BEGIN, FILE_CURRENT ou FILE_END).

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Pour obtenir la position actuelle du pointeur de fichier, appelez [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

Appelez cette méthode pour définir la taille du fichier temporaire.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Paramètres

*nNewLen*  
Nouvelle longueur du fichier en octets.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). En retour, le pointeur de fichier est placé à la fin du fichier.

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

Appelez cette méthode pour retourner le nom de fichier temporaire.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le LPCTSTR pointant vers le nom de fichier.

### <a name="remarks"></a>Notes

Le nom de fichier est généré dans [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) avec un appel à la [GetTempFile](/windows/desktop/api/fileapi/nf-fileapi-gettempfilenamea)fonction du Kit de développement logiciel Windows. L’extension de fichier sera toujours « TFR » pour le fichier temporaire.

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

Appelez cette méthode pour déverrouiller une région du fichier temporaire.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Paramètres

*nPos*  
Position dans le fichier où le déverrouillage doit commencer.

*nCount*  
La longueur de la plage d’octets à déverrouiller.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>  CAtlTemporaryFile::Write

Appelez cette méthode pour écrire des données dans le fichier temporaire, en commençant à la position indiquée par le pointeur de fichier.

```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*pBuffer*  
La mémoire tampon contenant les données à écrire dans le fichier.

*nBufSize*  
Le nombre d’octets à transférer à partir de la mémoire tampon.

*pnBytesWritten*  
Nombre d'octets écrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Appels [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
[CAtlFile, classe](../../atl/reference/catlfile-class.md)
