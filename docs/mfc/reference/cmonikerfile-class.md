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
ms.openlocfilehash: ecffdb3a6f44f60004cf4f039bdab9c98e212ce1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338036"
---
# <a name="cmonikerfile-class"></a>CMonikerFile, classe

Représente un flux de données ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)) nommé par un [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker).

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
|[CMonikerFile::Detach](#detach)|Détache le `IMoniker` à partir de ce `CMonikerFile` objet.|
|[CMonikerFile::GetMoniker](#getmoniker)|Retourne le moniker actuel.|
|[CMonikerFile::Open](#open)|Ouvre le fichier spécifié pour obtenir un flux de données.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtient le contexte de liaison ou crée un contexte de liaison initialisés par défaut.|

## <a name="remarks"></a>Notes

Un moniker contient des informations à l’instar d’un chemin d’accès vers un fichier. Si vous disposez d’un pointeur vers un objet de moniker `IMoniker` interface, vous pouvez accéder au fichier identifié sans avoir d’autres informations spécifiques sur où se trouve en fait le fichier.

Dérivé `COleStreamFile`, `CMonikerFile` prend un moniker ou une représentation de chaîne pouvant être transformé en moniker et le lie au flux pour lequel le moniker est un nom. Vous pouvez ensuite lire et écrire dans ce flux de données. Le véritable objectif de `CMonikerFile` consiste à fournir un accès simple aux `IStream`s nommé par `IMoniker`s afin que vous n’avez pas à lier à un flux de données vous-même, encore avoir `CFile` fonctionnalité dans le flux.

`CMonikerFile` ne peut pas être utilisé pour lier à autre chose qu’un flux de données. Si vous souhaitez lier à un objet ou de stockage, vous devez utiliser le `IMoniker` interface directement.

Pour plus d’informations sur les flux et des monikers, consultez [COleStreamFile](../../mfc/reference/colestreamfile-class.md) dans le *référence MFC* et [IStream](/windows/desktop/api/objidl/nn-objidl-istream) et [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) dans le Windows SDK.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

##  <a name="close"></a>  CMonikerFile::Close

Appelez cette fonction pour détacher et de libérer le flux et libérer le moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelée sur le flux fermés ou déjà fermés.

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

Construit un objet `CMonikerFile`.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

Appelez cette fonction pour créer un contexte de liaison initialisés par défaut.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, il est fixé à la cause.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le contexte de liaison [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) à lier avec cas de réussite ; sinon, NULL. Si l’instance a été ouvert avec un `IBindHost` interface, le contexte de liaison est récupéré à partir de la `IBindHost`. S’il existe aucune `IBindHost` interface ou l’interface ne peut pas retourner un contexte de liaison, un contexte de liaison est créé. Pour obtenir une description de la [IBindHost](https://msdn.microsoft.com/library/ie/ms775076) l’interface, consultez le kit SDK Windows.

### <a name="remarks"></a>Notes

Un contexte de liaison est un objet qui stocke des informations sur une opération de liaison de moniker particulier. Vous pouvez remplacer cette fonction pour fournir un contexte de liaison personnalisé.

##  <a name="detach"></a>  CMonikerFile::Detach

Appelez cette fonction pour fermer le flux.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, il est fixé à la cause.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

Appelez cette fonction pour récupérer un pointeur vers le moniker actuel.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’interface de moniker actuel ( [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Notes

Dans la mesure où `CMonikerFile` n’est pas une interface, le pointeur retourné n’incrémente pas le décompte de références (via [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)), et le moniker est libéré lorsque la `CMonikerFile` objet est libéré. Si vous souhaitez conserver le moniker ou libérer vous-même, vous devez `AddRef` il.

##  <a name="open"></a>  CMonikerFile::Open

Appelez cette fonction membre pour ouvrir un objet fichier ou de moniker.

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
Une URL ou le nom du fichier à ouvrir.

*pError*<br/>
Pointeur vers une exception de fichier. En cas d’erreur, il est fixé à la cause.

*pMoniker*<br/>
Un pointeur vers l’interface de moniker `IMoniker` à utiliser pour obtenir un flux.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le *lpszURL* paramètre ne peut pas être utilisé sur un Macintosh. Uniquement les *pMoniker* formulaire de `Open` peut être utilisé sur un Macintosh.

Vous pouvez utiliser une URL ou un nom de fichier pour le *lpszURL* paramètre. Exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[COleStreamFile, classe](../../mfc/reference/colestreamfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
