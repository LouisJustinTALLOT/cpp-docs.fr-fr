---
title: Classe CMonikerFile
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
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319771"
---
# <a name="cmonikerfile-class"></a>Classe CMonikerFile

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
|[CMonikerFile::Fermer](#close)|Détache et libère le flux et libère le surnom.|
|[CMonikerFile::Detach](#detach)|Détache `IMoniker` `CMonikerFile` l’objet.|
|[CMonikerFile::GetMoniker](#getmoniker)|Retourne le surnom actuel.|
|[CMonikerFile::Ouvert](#open)|Ouvre le fichier spécifié pour obtenir un flux.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtient le contexte de liaison ou crée un contexte de liaison initialisé par défaut.|

## <a name="remarks"></a>Notes

Un surnom contient des informations un peu comme un nom de chemin à un fichier. Si vous avez un pointeur sur `IMoniker` l’interface d’un objet de surnom, vous pouvez accéder au fichier identifié sans avoir d’autres informations spécifiques sur l’endroit où le fichier est réellement situé.

Dérivé `COleStreamFile`de `CMonikerFile` , prend un surnom ou une représentation de cordes qu’il peut faire dans un surnom et se lie au flux pour lequel le surnom est un nom. Vous pouvez ensuite lire et écrire à ce flux. Le but `CMonikerFile` réel est de `IStream`fournir un `IMoniker`accès simple à s nommé par s afin `CFile` que vous n’ayez pas à vous lier à un flux vous-même, mais ont des fonctionnalités pour le flux.

`CMonikerFile`ne peut pas être utilisé pour se lier à autre chose qu’un flux. Si vous souhaitez vous lier au stockage `IMoniker` ou à un objet, vous devez utiliser l’interface directement.

Pour plus d’informations sur les flux et les surnoms, voir [COleStreamFile](../../mfc/reference/colestreamfile-class.md) dans le *MFC Reference* et [IStream](/windows/win32/api/objidl/nn-objidl-istream) et [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) dans windows SDK.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMonikerFile::Fermer

Appelez cette fonction pour détacher et libérer le flux et pour libérer le surnom.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelé sur les cours d’eau non ouverts ou déjà fermés.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Construit un objet `CMonikerFile`.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Appelez cette fonction pour créer un contexte de liaison initialisé par défaut.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Paramètres

*Perror*<br/>
Un pointeur à une exception de fichier. En cas d’erreur, il sera réglé sur la cause.

### <a name="return-value"></a>Valeur de retour

Un pointeur au contexte de liaison [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) à lier avec si réussir; autrement NULL. Si l’instance a `IBindHost` été ouverte avec une interface, le contexte de liaison est récupéré à partir de la `IBindHost`. S’il `IBindHost` n’y a pas d’interface ou si l’interface ne parvient pas à retourner un contexte de liaison, un contexte de liaison est créé. Pour une description de l’interface [IBindHost,](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) voir le SDK Windows.

### <a name="remarks"></a>Notes

Un contexte de liaison est un objet qui stocke des informations sur une opération de liaison de surnom particulier. Vous pouvez remplacer cette fonction pour fournir un contexte de liaison personnalisé.

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMonikerFile::Detach

Appelez cette fonction pour fermer le flux.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*Perror*<br/>
Un pointeur à une exception de fichier. En cas d’erreur, il sera réglé sur la cause.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMonikerFile::GetMoniker

Appelez cette fonction pour récupérer un pointeur sur le surnom actuel.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface de surnom actuel ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Notes

Comme `CMonikerFile` ce n’est pas une interface, le pointeur retourné n’incrémente pas le `CMonikerFile` nombre de références (via [AddRef),](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)et le surnom est libéré lorsque l’objet est libéré. Si vous voulez conserver le surnom ou le libérer `AddRef` vous-même, vous devez-le.

## <a name="cmonikerfileopen"></a><a name="open"></a>CMonikerFile::Ouvert

Appelez cette fonction de membre pour ouvrir un fichier ou un objet de surnom.

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
Une URL ou un nom de fichier du fichier à ouvrir.

*Perror*<br/>
Un pointeur à une exception de fichier. En cas d’erreur, il sera réglé sur la cause.

*pMoniker (en anglais)*<br/>
Un pointeur à l’interface `IMoniker` de surnom à utiliser pour obtenir un flux.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le *paramètre lpszURL* ne peut pas être utilisé sur un Macintosh. Seule la forme de `Open` *pMoniker* peut être utilisée sur un Macintosh.

Vous pouvez utiliser une URL ou un nom de fichier pour le paramètre *lpszURL.* Par exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe COleStreamFile](../../mfc/reference/colestreamfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
