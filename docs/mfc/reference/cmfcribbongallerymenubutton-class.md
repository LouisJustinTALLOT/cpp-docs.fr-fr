---
title: Cmfcribbongallerymenubutton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
ms.openlocfilehash: b63eab7c1e4d03a9103795892603b819eb7d02f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236934"
---
# <a name="cmfcribbongallerymenubutton-class"></a>Cmfcribbongallerymenubutton, classe

Implémente un bouton de menu de ruban qui contient des galeries de ruban.
Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Construit et initialise un objet `CMFCRibbonGalleryMenuButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Substitue [CMFCToolBarMenuButton::CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom).)|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Substitue [CMFCToolBarMenuButton::CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Substitue `CMFCToolBarMenuButton::HasButton`.)|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Substitue [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|

### <a name="remarks"></a>Notes

Le bouton de menu de galerie s'affiche sous forme de menu contextuel avec une flèche. Quand l'utilisateur clique sur ce bouton, une galerie d'images s'affiche. Quand vous construisez un bouton de menu de galerie, vous devez spécifier une liste d'images qui contient ces images.

## <a name="example"></a>Exemple

L'exemple suivant montre comment afficher une galerie de puces dans un bouton de menu :

```
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)
{
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)
{
    CMFCToolBarButton* pExButton =
    pMenuBar->GetButton(nBulletIndex);
ASSERT_VALID (pExButton);

    CMFCRibbonGalleryMenuButton paletteBullet (
    pExButton->m_nID,
    pExButton->GetImage (),
    pExButton->m_strText);

InitBulletPalette (&paletteBullet.GetPalette ());

    pMenuBar->ReplaceButton (ID_PARA_BULLETS,
    paletteBullet);

}
}
```

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonPaletteGallery.h

##  <a name="copyfrom"></a>  CMFCRibbonGalleryMenuButton::CopyFrom

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

[in] *src*<br/>

### <a name="remarks"></a>Notes

##  <a name="cmfcribbongallerymenubutton"></a>  CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton

Crée et initialise un [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md) objet.

```
CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    CMFCToolBarImages& imagesPalette);

CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    UINT uiImagesPaletteResID = 0,
    int cxPaletteImage = 0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
L’ID de commande du bouton. Il s’agit de la valeur envoyée dans le message WM_COMMAND lorsque l’utilisateur clique sur ce bouton.

*iImage*<br/>
L’index de l’image à afficher avec le bouton de menu de galerie. Les images sont stockées dans le *imagesPalette* paramètre.

*lpszText*<br/>
Le texte à afficher sur le bouton de menu.

*imagesPalette*<br/>
Contient la liste des images à afficher dans la galerie.

*uiImagesPaletteResID*<br/>
L’ID de ressource de la liste d’images pour les images à afficher dans la galerie.

*cxPaletteImage*<br/>
Spécifie la largeur en pixels de l’image à afficher dans la galerie.

### <a name="remarks"></a>Notes

Le bouton de menu de galerie s’affiche sous forme de menu contextuel qui comporte une flèche. Quand l'utilisateur clique sur ce bouton, une galerie d'images s'affiche.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le constructeur de la `CMFCRibbonGalleryMenuButton` classe. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

##  <a name="createpopupmenu"></a>  CMFCRibbonGalleryMenuButton::CreatePopupMenu

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getpalette"></a>  CMFCRibbonGalleryMenuButton::GetPalette

```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="hasbutton"></a>  CMFCRibbonGalleryMenuButton::HasButton

```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isemptymenuallowed"></a>  CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarMenuButton, classe](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[CMFCRibbonGallery, classe](../../mfc/reference/cmfcribbongallery-class.md)
