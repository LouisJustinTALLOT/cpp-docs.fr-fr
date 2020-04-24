---
title: Classe COleStreamFile
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 202f8381361881ce3b8b62f81da5bfb81a1f952d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753761"
---
# <a name="colestreamfile-class"></a>Classe COleStreamFile

Représente un flux de données (`IStream`) dans un fichier composé dans le cadre du stockage structuré OLE.

## <a name="syntax"></a>Syntaxe

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Construit un objet `COleStreamFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|Associe un flux à l’objet.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crée un flux à partir de la mémoire globale et l’associe à l’objet.|
|[COleStreamFile::CreateStream](#createstream)|Crée un flux et l’associe à l’objet.|
|[COleStreamFile::Detach](#detach)|Dissocie le flux de l’objet.|
|[COleStreamFile::GetStream](#getstream)|Retourne le flux actuel.|
|[COleStreamFile::OpenStream](#openstream)|Ouvre en toute sécurité un flux et l’associe à l’objet.|

## <a name="remarks"></a>Notes

Un `IStorage` objet doit exister avant que le flux puisse être ouvert ou créé à moins qu’il ne s’agit d’un flux de mémoire.

`COleStreamFile`objets sont manipulés exactement comme des objets [CFile.](../../mfc/reference/cfile-class.md)

Pour plus d’informations sur la manipulation des flux et des stockages, voir l’article [Containers: Compound Files](../../mfc/containers-compound-files.md)..

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) et [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Attach

Associe le flux OLE `COleStreamFile` fourni à l’objet.

```cpp
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Points au flux OLE (`IStream`) à associer à l’objet. Ne peut pas avoir la valeur NULL.

### <a name="remarks"></a>Notes

L’objet ne doit pas déjà être associé à un flux OLE.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans windows SDK.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile

Crée un objet `COleStreamFile` .

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Pointeur sur le flux OLE à associer à l’objet.

### <a name="remarks"></a>Notes

Si *lpStream* est NULL, l’objet n’est pas associé à un flux OLE, sinon, l’objet est associé au flux OLE fourni.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans windows SDK.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Crée en toute sécurité un nouveau flux à partir de la mémoire globale et partagée où un échec est une condition normale et attendue.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*Perror*<br/>
Indique un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou NULL qui indique l’état d’achèvement de l’opération de création. Fournissez ce paramètre si vous souhaitez surveiller les exceptions possibles générées par la tentative de créer le flux.

### <a name="return-value"></a>Valeur de retour

Nonzero si le flux est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

La mémoire est attribuée par le sous-système OLE.

Pour plus d’informations, voir [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) dans le SDK Windows.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream

Crée en toute sécurité un nouveau flux dans l’objet de stockage fourni où une défaillance est une condition normale et prévue.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStorage*<br/>
Points à l’objet de stockage OLE qui contient le flux à créer. Ne peut pas avoir la valeur NULL.

*lpszStreamName (en)*<br/>
Nom du flux à créer. Ne peut pas avoir la valeur NULL.

*nOpenFlags*<br/>
Mode d’accès à utiliser lors de l’ouverture du flux. Les modes exclusifs, lus/écrits et de création sont utilisés par défaut. Pour une liste complète des modes disponibles, voir [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*Perror*<br/>
Indique un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou NULL. Fournissez ce paramètre si vous souhaitez surveiller les exceptions possibles générées par la tentative de créer le flux.

### <a name="return-value"></a>Valeur de retour

Nonzero si le flux est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Une exception de fichier sera jetée si l’ouverture échoue et *pError n’est* pas NULL.

Pour plus d’informations, voir [IStorage::CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) in the Windows SDK.

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach

Dissocie le flux de l’objet sans fermer le flux.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers`IStream`le flux ( ) qui a été associé à l’objet.

### <a name="remarks"></a>Notes

Le flux doit être fermé d’une autre façon avant la fin du programme.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans windows SDK.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream

Appelez cette fonction pour retourner un pointeur au flux actuel.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface de flux actuelle ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream

Ouvre un flux existant.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStorage*<br/>
Points à l’objet de stockage OLE qui contient le flux à ouvrir. Ne peut pas avoir la valeur NULL.

*lpszStreamName (en)*<br/>
Nom du flux à ouvrir. Ne peut pas avoir la valeur NULL.

*nOpenFlags*<br/>
Mode d’accès à utiliser lors de l’ouverture du flux. Les modes exclusifs et lus/écriture sont utilisés par défaut. Pour la liste complète des modes disponibles, voir [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*Perror*<br/>
Indique un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou NULL. Fournissez ce paramètre si vous souhaitez surveiller les exceptions possibles générées en essayant d’ouvrir le flux.

### <a name="return-value"></a>Valeur de retour

Nonzero si le flux est ouvert avec succès; sinon 0.

### <a name="remarks"></a>Notes

Une exception de fichier sera jetée si l’ouverture échoue et *pError n’est* pas NULL.

Pour plus d’informations, voir [IStorage::OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
