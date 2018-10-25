---
title: CPictureHolder, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef97b1340d91d672b64a403fd70cec69861a05ba
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062104"
---
# <a name="cpictureholder-class"></a>CPictureHolder, classe

Implémente une propriété Picture, qui permet à l’utilisateur d’afficher une image dans votre contrôle.

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
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Crée un `CPictureHolder` objet à partir d’une image bitmap.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Crée un `CPictureHolder` objet à partir d’une icône.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Crée un `CPictureHolder` objet à partir d’un métafichier.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans l’Explorateur de propriétés d’un conteneur de contrôle.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Retourne le `CPictureHolder` l’objet `IDispatch` interface.|
|[CPictureHolder::GetType](#gettype)|Indique si le `CPictureHolder` objet est une image bitmap, métafichier ou une icône.|
|[CPictureHolder::Render](#render)|Restitue l’image.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Définit le `CPictureHolder` l’objet `IDispatch` interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Pointeur vers un objet image.|

## <a name="remarks"></a>Notes

`CPictureHolder` n’a pas d’une classe de base.

Avec la propriété Picture stockée, le développeur peut spécifier un bitmap, une icône ou un métafichier pour l’affichage.

Pour plus d’informations sur la création de propriétés picture personnalisées, consultez l’article [contrôles ActiveX MFC : utilisation des images dans un contrôle ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPictureHolder`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxctl.h

##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder

Construit un objet `CPictureHolder`.

```
CPictureHolder();
```

##  <a name="createempty"></a>  CPictureHolder::CreateEmpty

Crée un vide `CPictureHolder` de l’objet et le connecte à un `IPicture` interface.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet est créé avec succès ; sinon 0.

##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap

Utilise une image bitmap pour initialiser l’objet de l’image dans un `CPictureHolder`.

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

*idResource*<br/>
ID de ressource d’une ressource bitmap.

*pBitmap*<br/>
Pointeur vers un [CBitmap](../../mfc/reference/cbitmap-class.md) objet.

*pPal*<br/>
Pointeur vers un [CPalette](../../mfc/reference/cpalette-class.md) objet.

*bTransferOwnership*<br/>
Indique si l’objet image prendra possession des objets bitmap et de la palette.

*hbm*<br/>
Handle vers la bitmap à partir de laquelle le `CPictureHolder` objet est créé.

*hPal*<br/>
Handle de la palette utilisée pour le rendu de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet est créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur TRUE, l’appelant ne doit pas utiliser l’image bitmap ou objet de la palette de toute façon après cet appel retourne. Si *bTransferOwnership* est FALSE, l’appelant est chargé de s’assurer que les objets bitmap et palette restent valides pour la durée de vie de l’objet image.

##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon

Utilise une icône pour initialiser l’objet de l’image dans un `CPictureHolder`.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*idResource*<br/>
ID de ressource d’une ressource bitmap.

*hIcon*<br/>
Handle de l’icône à partir de laquelle le `CPictureHolder` objet est créé.

*bTransferOwnership*<br/>
Indique si l’objet image prendra possession de l’objet de l’icône.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet est créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur TRUE, l’appelant ne doit pas utiliser l’objet icône en aucune façon après le retour de cet appel. Si *bTransferOwnership* est FALSE, l’appelant est chargé de s’assurer que l’objet icône reste valide pendant la durée de vie de l’objet image.

##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile

Utilise un métafichier pour initialiser l’objet de l’image dans un `CPictureHolder`.

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*HMF*<br/>
Handle du métafichier utilisé pour créer le `CPictureHolder` objet.

*xExt*<br/>
X étendue de l’image.

*yExt*<br/>
Étendue de Y de l’image.

*bTransferOwnership*<br/>
Indique si l’objet image prendra possession de l’objet du métafichier.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet est créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur TRUE, l’appelant ne doit pas utiliser l’objet de métafichier en aucune façon après le retour de cet appel. Si *bTransferOwnership* est FALSE, l’appelant est chargé de s’assurer que l’objet du métafichier reste valide pendant la durée de vie de l’objet image.

##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString

Récupère la chaîne qui est affichée dans l’Explorateur de propriétés d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui doit contenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la chaîne est correctement récupérée ; sinon 0.

##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch

Cette fonction retourne un pointeur vers le `CPictureHolder` l’objet `IPictureDisp` interface.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `CPictureHolder` l’objet `IPictureDisp` interface.

### <a name="remarks"></a>Notes

L’appelant doit appeler `Release` sur ce pointeur lorsque terminé avec lui.

##  <a name="gettype"></a>  CPictureHolder::GetType

Indique si l’image est une bitmap, métafichier ou icône.

```
short GetType();
```

### <a name="return-value"></a>Valeur de retour

Une valeur indiquant le type de l’image. Les valeurs possibles et leurs significations sont les suivantes :

|Value|Signification|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` unititialized d’objet.|
|PICTYPE_NONE|`CPictureHolder` l’objet est vide.|
|PICTYPE_BITMAP|Image est une image bitmap.|
|PICTYPE_METAFILE|L’image est un métafichier.|
|PICTYPE_ICON|Image est une icône.|

##  <a name="m_ppict"></a>  CPictureHolder::m_pPict

Un pointeur vers le `CPictureHolder` l’objet `IPicture` interface.

```
LPPICTURE m_pPict;
```

##  <a name="render"></a>  CPictureHolder::Render

Restitue l’image dans le rectangle référencé par *rcRender*.

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte d’affichage dans lequel l’image doit être restitué.

*rcRender*<br/>
Rectangle dans lequel l’image doit être restitué.

*rcWBounds*<br/>
Un rectangle qui représente le rectangle englobant de l’objet de rendu de l’image. Pour un contrôle, ce rectangle est le *rcBounds* paramètre passé à une substitution de [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch

Se connecte le `CPictureHolder` de l’objet à un `IPictureDisp` interface.

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Paramètres

*argument pDisp*<br/>
Pointeur vers le nouveau `IPictureDisp` interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder, classe](../../mfc/reference/cfontholder-class.md)
