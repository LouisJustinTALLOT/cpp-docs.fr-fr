---
title: COleStreamFile, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f93b367b207730f331e4a9ae16b191f7a5314e4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399602"
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
|[COleStreamFile::Attach](#attach)|Associe un flux de données à l’objet.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Crée un flux à partir de la mémoire globale et l’associe à l’objet.|
|[COleStreamFile::CreateStream](#createstream)|Crée un flux de données et l’associe à l’objet.|
|[COleStreamFile::Detach](#detach)|Dissocie le flux à partir de l’objet.|
|[COleStreamFile::GetStream](#getstream)|Retourne le flux actuel.|
|[COleStreamFile::OpenStream](#openstream)|En toute sécurité ouvre un flux de données et l’associe à l’objet.|

## <a name="remarks"></a>Notes

Un `IStorage` objet doit exister avant que le flux peut être ouvert ou créé à moins qu’il s’agit d’un flux de mémoire.

`COleStreamFile` les objets sont manipulés exactement comme [CFile](../../mfc/reference/cfile-class.md) objets.

Pour plus d’informations sur la manipulation des flux et les stockages, consultez l’article [conteneurs : fichiers composés](../../mfc/containers-compound-files.md)...

Pour plus d’informations, consultez [IStream](/windows/desktop/api/objidl/nn-objidl-istream) et [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

##  <a name="attach"></a>  COleStreamFile::Attach

Associe le flux de données OLE fourni avec le `COleStreamFile` objet.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Pointe vers un flux OLE (`IStream`) à associer à l’objet. Ne peut pas être Null.

### <a name="remarks"></a>Notes

L’objet ne doit pas déjà être associé à un flux OLE.

Pour plus d’informations, consultez [IStream](/windows/desktop/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile

Crée un objet `COleStreamFile`.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStream*<br/>
Pointeur vers un flux OLE à associer à l’objet.

### <a name="remarks"></a>Notes

Si *lpStream* est NULL, l’objet n’est pas associé à un flux OLE, sinon, l’objet est associé avec le flux de données OLE fourni.

Pour plus d’informations, consultez [IStream](/windows/desktop/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

En toute sécurité crée un flux de données en dehors de la mémoire partagée globale où une défaillance est une condition normale, attendue.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou valeur NULL qui indique l’état d’achèvement de l’opération de création. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions possibles générées en essayant de créer le flux.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

La mémoire est allouée par le sous-système OLE.

Pour plus d’informations, consultez [CreateStreamOnHGlobal](/windows/desktop/api/combaseapi/nf-combaseapi-createstreamonhglobal) dans le SDK Windows.

##  <a name="createstream"></a>  COleStreamFile::CreateStream

En toute sécurité crée un flux de données dans l’objet de stockage fourni où une défaillance est une condition normale, attendue.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpStorage*<br/>
Pointe vers l’objet de stockage OLE qui contient le flux doit être créé. Ne peut pas être Null.

*lpszStreamName*<br/>
Nom du flux doit être créé. Ne peut pas être Null.

*nOpenFlags*<br/>
Mode d’accès à utiliser lors de l’ouverture du flux. Exclusif, lecture/écriture et créer des modes sont utilisés par défaut. Pour obtenir une liste complète des modes disponibles, consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou NULL. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions possibles générées en essayant de créer le flux.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Une exception de fichier sera levée si la fonction open échoue et *pError* n’est pas NULL.

Pour plus d’informations, consultez [IStorage::CreateStream](/windows/desktop/api/objidl/nf-objidl-istorage-createstream) dans le SDK Windows.

##  <a name="detach"></a>  COleStreamFile::Detach

Dissocie le flux à partir de l’objet sans avoir à fermer le flux.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le flux (`IStream`) qui a été associé à l’objet.

### <a name="remarks"></a>Notes

Le flux doit être fermé d’une autre façon avant que le programme se termine.

Pour plus d’informations, consultez [IStream](/windows/desktop/api/objidl/nn-objidl-istream) dans le SDK Windows.

##  <a name="getstream"></a>  COleStreamFile::GetStream

Appelez cette fonction pour retourner un pointeur vers le flux actuel.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’interface de flux de données actuelle ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)).

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
Mode d’accès à utiliser lors de l’ouverture du flux. Exclusif et en lecture/écriture, les modes sont utilisés par défaut. Pour obtenir la liste complète des modes disponibles, consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Pointe vers un [CFileException](../../mfc/reference/cfileexception-class.md) objet ou NULL. Spécifiez ce paramètre si vous souhaitez surveiller les exceptions possibles générées en essayant d’ouvrir le flux de données.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le flux est ouvert avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Une exception de fichier sera levée si la fonction open échoue et *pError* n’est pas NULL.

Pour plus d’informations, consultez [IStorage::OpenStream](/windows/desktop/api/objidl/nf-objidl-istorage-openstream) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)



