---
title: CPictureHolder, classe
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: edb93b05c1187d2c78f4c1120ee76282167c9b49
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753599"
---
# <a name="cpictureholder-class"></a>CPictureHolder, classe

Implémente une propriété Picture, qui permet à l’utilisateur d’afficher une image sous votre contrôle.

## <a name="syntax"></a>Syntaxe

```
class CPictureHolder
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Construit un objet `CPictureHolder`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Crée un objet `CPictureHolder` vide.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Crée `CPictureHolder` un objet à partir d’une bitmap.|
|[CPictureHolder::CreateDeIcon](#createfromicon)|Crée `CPictureHolder` un objet à partir d’une icône.|
|[CPictureHolder::CreateDeMetafile](#createfrommetafile)|Crée `CPictureHolder` un objet à partir d’un métaafile.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans le navigateur de propriété d’un conteneur de contrôle.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Retourne `CPictureHolder` l’interface `IDispatch` de l’objet.|
|[CPictureHolder::GetType](#gettype)|Indique si `CPictureHolder` l’objet est un bitmap, un métaafile, ou une icône.|
|[CPictureHolder::Render](#render)|Rend l’image.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Définit `CPictureHolder` l’interface `IDispatch` de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Un pointeur à un objet d’image.|

## <a name="remarks"></a>Notes

`CPictureHolder`n’a pas de classe de base.

Avec la propriété Picture stock, le développeur peut spécifier un bitmap, icône, ou metafile pour l’affichage.

Pour plus d’informations sur la création de propriétés d’images personnalisées, consultez l’article [MFC ActiveX Controls: Using Pictures in an ActiveX Control](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPictureHolder`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder

Construit un objet `CPictureHolder`.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty

Crée un `CPictureHolder` objet vide et `IPicture` le connecte à une interface.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est créé avec succès; sinon 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap

Utilise un bitmap pour initialiser `CPictureHolder`l’objet d’image dans un .

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*idResource (en)*<br/>
Id de ressource d’une ressource de bitmap.

*pBitmap (en)*<br/>
Pointeur vers un objet [CBitmap.](../../mfc/reference/cbitmap-class.md)

*pPal (en)*<br/>
Pointeur vers un objet [CPalette.](../../mfc/reference/cpalette-class.md)

*bTransferOwnership (en)*<br/>
Indique si l’objet d’image prendra possession des objets de bitmap et de palette.

*Hbm*<br/>
Manipulez la bitmap `CPictureHolder` à partir de laquelle l’objet est créé.

*hpal hpal*<br/>
Poignée à la palette utilisée pour rendre la bitmap.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* est VRAI, l’appelant ne doit pas utiliser le bitmap ou l’objet de palette de quelque façon après ce retour de cet appel. Si *bTransferOwnership* est FALSE, l’appelant est responsable de s’assurer que les objets de bitmap et de palette restent valables pour la durée de vie de l’objet d’image.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateDeIcon

Utilise une icône pour initialiser `CPictureHolder`l’objet d’image dans un .

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*idResource (en)*<br/>
Id de ressource d’une ressource de bitmap.

*hIcon (en)*<br/>
Manipulez l’icône `CPictureHolder` à partir de laquelle l’objet est créé.

*bTransferOwnership (en)*<br/>
Indique si l’objet d’image prendra la propriété de l’objet d’icône.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* est VRAI, l’appelant ne doit pas utiliser l’objet d’icône de quelque façon que ce soit après le retour de cet appel. Si *bTransferOwnership* est FALSE, l’appelant est responsable de s’assurer que l’objet d’icône reste valide pour la durée de vie de l’objet d’image.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateDeMetafile

Utilise un métaafile pour initialiser `CPictureHolder`l’objet d’image dans un .

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*Hmf*<br/>
Poignée au métaafile utilisé `CPictureHolder` pour créer l’objet.

*xExt (en anglais)*<br/>
X étendue de l’image.

*yExt yExt*<br/>
Y étendue de l’image.

*bTransferOwnership (en)*<br/>
Indique si l’objet d’image prendra possession de l’objet métadilile.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* est VRAI, l’appelant ne doit pas utiliser l’objet métaafile de quelque façon que ce soit après le retour de cet appel. Si *bTransferOwnership* est FALSE, l’appelant est chargé de s’assurer que l’objet métaafile reste valide pour la durée de vie de l’objet d’image.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString

Récupère la chaîne qui s’affiche dans le navigateur de propriété d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence au [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est de tenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur de retour

Nonzero si la chaîne est récupérée avec succès; sinon 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch

Cette fonction renvoie `CPictureHolder` un pointeur à l’interface de `IPictureDisp` l’objet.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CPictureHolder` sur `IPictureDisp` l’interface de l’objet.

### <a name="remarks"></a>Notes

L’appelant doit `Release` faire appel à ce pointeur une fois terminé avec elle.

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType

Indique si l’image est un bitmap, metafile, ou icône.

```
short GetType();
```

### <a name="return-value"></a>Valeur de retour

Une valeur indiquant le type d’image. Les valeurs possibles et leurs significations sont les suivantes :

|Valeur|Signification|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`l’objet est unitaire.|
|PICTYPE_NONE|`CPictureHolder`l’objet est vide.|
|PICTYPE_BITMAP|L’image est un bitmap.|
|PICTYPE_METAFILE|L’image est un metafile.|
|PICTYPE_ICON|L’image est une icône.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict

Un pointeur `CPictureHolder` sur `IPicture` l’interface de l’objet.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPictureHolder::Render

Rend l’image dans le rectangle référencé par *rcRender*.

```cpp
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte d’affichage dans lequel l’image doit être rendue.

*rcRender*<br/>
Rectangle dans lequel l’image doit être rendue.

*rcWBounds (en)*<br/>
Un rectangle représentant le rectangle de délimitation de l’objet rendant l’image. Pour un contrôle, ce rectangle est le *paramètre rcBounds* passé à un remplacement de [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch

Connecte `CPictureHolder` l’objet `IPictureDisp` à une interface.

```cpp
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers `IPictureDisp` la nouvelle interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder, classe](../../mfc/reference/cfontholder-class.md)
