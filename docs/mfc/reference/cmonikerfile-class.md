---
title: CMonikerFile, classe
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504569"
---
# <a name="cmonikerfile-class"></a>CMonikerFile, classe

Représente un flux de données ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) nommé par un [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Syntaxe

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construit un objet `CMonikerFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMonikerFile::Close](#close)|Détache et libère le flux et libère le moniker.|
|[CMonikerFile::Detach](#detach)|Détache le `IMoniker` de cet `CMonikerFile` objet.|
|[CMonikerFile::GetMoniker](#getmoniker)|Retourne le moniker actuel.|
|[CMonikerFile:: Open](#open)|Ouvre le fichier spécifié pour obtenir un flux.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtient le contexte de liaison ou crée un contexte de liaison initialisé par défaut.|

## <a name="remarks"></a>Notes

Un moniker contient des informations très semblables à un nom de chemin d’accès à un fichier. Si vous avez un pointeur vers l’interface d' `IMoniker` un objet moniker, vous pouvez accéder au fichier identifié sans avoir d’autres informations spécifiques sur l’emplacement réel du fichier.

Dérivée `COleStreamFile`de `CMonikerFile` , prend un moniker ou une représentation sous forme de chaîne qu’il peut créer dans un moniker et se lie au flux pour lequel le moniker est un nom. Vous pouvez ensuite lire et écrire dans ce flux. Le but réel de `CMonikerFile` est de fournir un accès simple `IStream`aux objets nommés `IMoniker`par s afin que vous n’ayez pas à vous connecter à un flux vous- `CFile` même, mais que vous avez des fonctionnalités dans le flux.

`CMonikerFile`ne peut pas être utilisé pour effectuer une liaison à d’autres éléments qu’un flux. Si vous souhaitez effectuer une liaison au stockage ou à un objet, vous devez `IMoniker` utiliser l’interface directement.

Pour plus d’informations sur les flux et les monikers, consultez [COleStreamFile](../../mfc/reference/colestreamfile-class.md) dans *MFC Reference* et [IStream](/windows/win32/api/objidl/nn-objidl-istream) et [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Configuration requise

**En-tête:** AFXOLE. h

##  <a name="close"></a>  CMonikerFile::Close

Appelez cette fonction pour détacher et libérer le flux et libérer le moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelé sur des flux de flux qui ne sont pas ouverts ou déjà fermés.

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

Construit un objet `CMonikerFile`.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

Appelez cette fonction pour créer un contexte de liaison initialisé par défaut.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, elle est définie en conséquence.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le contexte de liaison [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) avec lequel établir une liaison en cas de réussite; Sinon, NULL. Si l’instance a été ouverte avec `IBindHost` une interface, le contexte `IBindHost`de liaison est récupéré à partir de. S’il n’existe `IBindHost` aucune interface ou si l’interface ne retourne pas de contexte de liaison, un contexte de liaison est créé. Pour obtenir une description de l’interface [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) , consultez la SDK Windows.

### <a name="remarks"></a>Notes

Un contexte de liaison est un objet qui stocke des informations sur une opération de liaison de moniker particulière. Vous pouvez remplacer cette fonction pour fournir un contexte de liaison personnalisé.

##  <a name="detach"></a>  CMonikerFile::Detach

Appelez cette fonction pour fermer le flux.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, elle est définie en conséquence.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

Appelez cette fonction pour récupérer un pointeur vers le moniker actuel.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface du moniker en cours ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Notes

Étant `CMonikerFile` donné que n’est pas une interface, le pointeur retourné n’incrémente pas le nombre de références (à l’aide de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)) et `CMonikerFile` le moniker est libéré lorsque l’objet est libéré. Si vous souhaitez conserver le moniker ou le libérer vous-même, vous devez `AddRef` le faire.

##  <a name="open"></a>  CMonikerFile::Open

Appelez cette fonction membre pour ouvrir un fichier ou un objet moniker.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
URL ou nom de fichier du fichier à ouvrir.

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, elle est définie en conséquence.

*pMoniker*<br/>
Pointeur vers l’interface `IMoniker` de moniker à utiliser pour obtenir un flux.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le paramètre *lpszURL* ne peut pas être utilisé sur un Macintosh. Seule la forme *pMoniker* de `Open` peut être utilisée sur un Macintosh.

Vous pouvez utiliser une URL ou un nom de fichier pour le paramètre *lpszURL* . Par exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[COleStreamFile, classe](../../mfc/reference/colestreamfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
