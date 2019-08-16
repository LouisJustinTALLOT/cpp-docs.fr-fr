---
title: COleStreamFile, classe
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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503688"
---
# <a name="colestreamfile-class"></a>COleStreamFile, classe

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
|[COleStreamFile::OpenStream](#openstream)|Ouvre un flux en toute sécurité et l’associe à l’objet.|

## <a name="remarks"></a>Notes

Un `IStorage` objet doit exister pour permettre l’ouverture ou la création du flux, sauf s’il s’agit d’un flux de mémoire.

`COleStreamFile`les objets sont manipulés exactement comme les objets [CFile](../../mfc/reference/cfile-class.md) .

Pour plus d’informations sur la manipulation des flux et des stockages, [consultez l’article conteneurs: Fichiers](../../mfc/containers-compound-files.md)composés..

Pour plus d’informations, consultez [IStream](/windows/win32/api/objidl/nn-objidl-istream) et [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Configuration requise

**En-tête:** AFXOLE. h

##  <a name="attach"></a>  COleStreamFile::Attach

Associe le flux OLE fourni à `COleStreamFile` l’objet.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Pointe vers le flux OLE (`IStream`) à associer à l’objet. Ne peut pas être Null.

### <a name="remarks"></a>Notes

L’objet ne doit pas déjà être associé à un flux OLE.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile

Crée un objet `COleStreamFile`.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Pointeur vers le flux OLE à associer à l’objet.

### <a name="remarks"></a>Notes

Si *lpStream* a la valeur null, l’objet n’est pas associé à un flux OLE, dans le cas contraire, l’objet est associé au flux OLE fourni.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

Crée en toute sécurité un nouveau flux à partir de la mémoire partagée globale, où une défaillance est une condition normale et attendue.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointe vers un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou null qui indique l’état d’achèvement de l’opération de création. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions générées par la tentative de création du flux.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est correctement créé; Sinon, 0.

### <a name="remarks"></a>Notes

La mémoire est allouée par le sous-système OLE.

Pour plus d’informations, consultez [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) dans le SDK Windows.

##  <a name="createstream"></a>  COleStreamFile::CreateStream

Crée en toute sécurité un nouveau flux dans l’objet de stockage fourni où une défaillance est une condition normale et attendue.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStorage*<br/>
Pointe vers l’objet de stockage OLE qui contient le flux à créer. Ne peut pas être Null.

*lpszStreamName*<br/>
Nom du flux à créer. Ne peut pas être Null.

*nOpenFlags*<br/>
Mode d’accès à utiliser lors de l’ouverture du flux. Les modes exclusif, lecture/écriture et créer sont utilisés par défaut. Pour obtenir la liste complète des modes disponibles, consultez [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Pointe vers un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou null. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions générées par la tentative de création du flux.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est correctement créé; Sinon, 0.

### <a name="remarks"></a>Notes

Une exception de fichier est levée si l’ouverture échoue et *perror* n’a pas la valeur null.

Pour plus d’informations, consultez [IStorage:: CreateStream,](/windows/win32/api/objidl/nf-objidl-istorage-createstream) dans la SDK Windows.

##  <a name="detach"></a>  COleStreamFile::Detach

Dissocie le flux de l’objet sans fermer le flux.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le flux (`IStream`) associé à l’objet.

### <a name="remarks"></a>Notes

Le flux doit être fermé d’une manière ou d’une autre avant que le programme ne se termine.

Pour plus d’informations, voir [IStream](/windows/win32/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="getstream"></a>  COleStreamFile::GetStream

Appelez cette fonction pour retourner un pointeur vers le flux actuel.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream)(active Stream interface).

##  <a name="openstream"></a>  COleStreamFile::OpenStream

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
Pointe vers l’objet de stockage OLE qui contient le flux à ouvrir. Ne peut pas être Null.

*lpszStreamName*<br/>
Nom du flux à ouvrir. Ne peut pas être Null.

*nOpenFlags*<br/>
Mode d’accès à utiliser lors de l’ouverture du flux. Les modes exclusif et lecture/écriture sont utilisés par défaut. Pour obtenir la liste complète des modes disponibles, consultez [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Pointe vers un objet [CFileException](../../mfc/reference/cfileexception-class.md) ou null. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions générées par la tentative d’ouverture du flux.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est ouvert avec succès; Sinon, 0.

### <a name="remarks"></a>Notes

Une exception de fichier est levée si l’ouverture échoue et *perror* n’a pas la valeur null.

Pour plus d’informations, consultez [IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
