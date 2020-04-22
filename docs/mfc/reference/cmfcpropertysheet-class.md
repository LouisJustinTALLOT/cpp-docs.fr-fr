---
title: CMFCPropertySheet, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: 9b1bb2ce9a957b9cd9f7add983b4da7a228d7a1d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750058"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet, classe

La classe `CMFCPropertySheet` prend en charge une feuille de propriétés où chaque page de propriétés est représentée par un onglet de page, un bouton de barre d'outils, un nœud de contrôle d'arborescence ou un élément de liste.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Construit un objet `CMFCPropertySheet`.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Ajoute une page à la feuille de propriétés.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Ajoute une nouvelle page de propriétés au contrôle d'arborescence.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Ajoute un nouveau nœud au contrôle d'arborescence.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Réserve de l'espace en haut de chaque page pour dessiner un en-tête personnalisé.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Récupère la hauteur de l'en-tête actuel.|
|[CMFCPropertySheet::GetLook](#getlook)|Récupère une valeur d'énumération qui spécifie l'apparence de la feuille de propriétés actuelle.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Réessaie la largeur de la barre de navigation en pixels.|
|[CMFCPropertySheet::GetTab](#gettab)|Récupère l'objet de contrôle d'onglet interne qui prend en charge le contrôle de feuille de propriétés actuel.|
|`CMFCPropertySheet::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Initialise l'apparence du contrôle de feuille de propriétés actuel.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Appelé par l'infrastructure quand une page de propriétés est activée.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Appelé par l'infrastructure pour dessiner un en-tête de page de propriétés personnalisé.|
|`CMFCPropertySheet::OnInitDialog`|Gère le [message WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Overrides [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Appelé par l'infrastructure pour supprimer une page de propriétés d'un contrôle d'arborescence.|
|`CMFCPropertySheet::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Supprime un nœud du contrôle d’arborescence.|
|[CMFCPropertySheet::RemovePage](#removepage)|Supprime une page de propriétés de la feuille de propriétés.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Spécifie la liste des images utilisées dans le contrôle de navigation du volet Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Spécifie l'apparence de la feuille de propriétés.|

## <a name="remarks"></a>Notes

La classe `CMFCPropertySheet` représente les feuilles de propriétés, aussi appelées boîtes de dialogue à onglets. La classe `CMFCPropertySheet` peut afficher une page de propriétés de diverses manières.

Pour utiliser la classe `CMFCPropertySheet` dans votre application, procédez comme suit :

1. Faites dériver une classe de la classe `CMFCPropertySheet` et nommez-la, par exemple, CMyPropertySheet.

1. Construire un objet [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) pour chaque page de propriété.

1. Appelez la [feuille CMFCProperty ::SetLook](#setlook) méthode dans le constructeur CMyPropertySheet. Un paramètre de cette méthode permet de spécifier sous quelle forme les pages de propriétés seront affichées : onglets le long de la bordure supérieure ou gauche de la feuille de propriétés ; onglets dans le style d'une feuille de propriétés Microsoft OneNote ; boutons sur un contrôle de barre d'outils Microsoft Outlook ; nœuds sur un contrôle d'arborescence ; ou liste d'éléments sur le côté gauche de la feuille de propriétés.

1. Si vous créez une feuille de propriété dans le style d’une barre d’outils Microsoft Outlook, appelez la [feuille CMFCProperty ::SetIconsList](#seticonslist) méthode pour associer une liste d’images avec les pages de propriété.

1. Appelez la [feuille CMFCProperty ::Méthode AddPage](#addpage) pour chaque page de propriété.

1. Créez un contrôle `CMFCPropertySheet` et appelez sa méthode `DoModal`.

## <a name="illustrations"></a>Illustrations

L'illustration suivante représente une feuille de propriétés dont le style est celui d'une barre d'outils Microsoft Outlook incorporée. La barre d'outils Outlook s'affiche sur le côté gauche de la feuille de propriétés.

![Contrôles des couleurs CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Contrôles des couleurs CMFCPropertySheet")

L’illustration suivante représente une feuille de propriété qui contient un objet [cmFCPropertyGridCtrl Class.](../../mfc/reference/cmfcpropertygridctrl-class.md) Cet objet est une feuille de propriétés dont le style est celui d'une feuille de propriétés de contrôles communs standard.

![Contrôles de liste et de propriété CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "Contrôles de liste et de propriété CMFCPropertySheet")

L’illustration suivante représente une feuille de propriétés dont le style est celui d’un contrôle d’arborescence.

![Arbre de propriété](../../mfc/reference/media/proptree.png "Arbre de propriété")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertysheet.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>Feuille CMFCProperty::AddPage

Ajoute une page à la feuille de propriétés.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
[dans] Pointeur vers un objet de page. Ce paramètre ne peut pas être NULL.

### <a name="remarks"></a>Notes

Cette méthode ajoute la page de propriété spécifiée comme onglet le plus juste dans la feuille de propriété. Par conséquent, utilisez cette méthode pour ajouter des pages dans l’ordre de gauche à droite.

Si la feuille de propriété est dans le style de Microsoft Outlook, le cadre affiche une liste de boutons de navigation à gauche de la feuille de propriété. Après que cette méthode ajoute une page de propriété, elle ajoute un bouton correspondant à la liste. Pour afficher une page de propriété, cliquez sur son bouton correspondant. Pour plus d’informations sur les styles de feuilles de propriété, voir [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>Feuille CMFCProperty::AddPageToTree

Ajoute une nouvelle page de propriétés au contrôle d'arborescence.

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Paramètres

*pCatégory*<br/>
[dans] Pointeur vers un nœud d’arbre parent, ou NULL pour associer la page spécifiée avec le nœud de haut niveau. Appelez la [feuille CMFCProperty::AddTreeCategory](#addtreecategory) méthode pour obtenir ce pointeur.

*pPage*<br/>
[dans] Pointeur vers un objet de page de propriété.

*nIconNum (en)*<br/>
[dans] Index à base zéro d’une icône, ou -1 si aucune icône n’est utilisée. L’icône s’affiche à côté de la page de propriété de contrôle des arbres lorsque la page n’est pas sélectionnée. La valeur par défaut est -1.

*nSelIconNum (en)*<br/>
[dans] Index à base zéro d’une icône, ou -1 si aucune icône n’est utilisée. L’icône s’affiche à côté de la page de propriété de contrôle des arbres lorsque la page est sélectionnée. La valeur par défaut est -1.

### <a name="remarks"></a>Notes

Cette méthode ajoute une page de propriété comme une feuille d’un contrôle des arbres. Pour ajouter une page `CMFCPropertySheet` de propriété, créez un objet, appelez la [feuille CMFCProperty ::SetLook](#setlook) méthode avec le *paramètre de look* réglé à `CMFCPropertySheet::PropSheetLook_Tree`, puis utilisez cette méthode pour ajouter la page de propriété.

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>Feuille CMFCProperty::AddTreeCategory

Ajoute un nouveau nœud au contrôle d'arborescence.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Le nom du nœud.

*nIconNum (en)*<br/>
[dans] Index à base zéro d’une icône, ou -1 si aucune icône n’est utilisée. L’icône s’affiche à côté de la page de propriété de contrôle des arbres lorsque la page n’est pas sélectionnée. La valeur par défaut est -1.

*nSelectedIconNum*<br/>
[dans] Index à base zéro d’une icône, ou -1 si aucune icône n’est utilisée. L’icône s’affiche à côté de la page de propriété de contrôle des arbres lorsque la page est sélectionnée. La valeur par défaut est -1.

*pParentCatégorie*<br/>
[dans] Pointeur vers un nœud d’arbre parent, ou NULL pour associer la page spécifiée avec le nœud de haut niveau. Définissez ce paramètre avec la [feuille CMFCProperty ::AddTreeCategory](#addtreecategory) méthode.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le nouveau nœud dans le contrôle de l’arbre.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour ajouter un nouveau nœud, qui est également appelé une catégorie, à la commande des arbres. Pour ajouter un nœud, créez `CMFCPropertySheet` un objet, appelez la feuille [CMFCProperty ::SetLook](#setlook) méthode avec le *paramètre de look* réglé à `CMFCPropertySheet::PropSheetLook_Tree`, puis utilisez cette méthode pour ajouter le nœud.

Utilisez la valeur de retour de cette méthode dans les appels suivants à [CMFCPropertySheet:AddPageToTree](#addpagetotree) et [CMFCPropertySheet::AddTreeCategory](#addtreecategory).

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>Feuille CMFCProperty::CMFCPropertySheet

Construit un objet `CMFCPropertySheet`.

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>Paramètres

*pszCaption*<br/>
[dans] Une chaîne qui contient la légende de la feuille de propriété. Ne peut pas avoir la valeur NULL.

*nIDCaption (en)*<br/>
[dans] Une pièce d’identité de ressource qui contient la légende de la feuille de propriété.

*pParentWnd*<br/>
[dans] Pointeur vers la fenêtre parente de la feuille de propriété, ou NULL si la fenêtre parente est la fenêtre principale de la demande. La valeur par défaut est NULL.

*iSelectPage*<br/>
[dans] L’indice zéro de la page de propriété supérieure. La valeur par défaut est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez les paramètres de la feuille CProperty : : Constructeur de la [feuille de cproperty.](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>Feuille CMFCProperty::EnablePageHeader

Réserve de l'espace en haut de chaque page pour dessiner un en-tête personnalisé.

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Paramètres

*nHeaderHeight*<br/>
[dans] La hauteur de l’en-tête, en pixels.

### <a name="remarks"></a>Notes

Pour utiliser la valeur du paramètre *nHeaderHeight* pour dessiner un en-tête personnalisé, remplacez la [feuille CMFCProperty ::OnDrawPageHeader](#ondrawpageheader) méthode.

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>Feuille CMFCProperty::GetHeaderHeight

Récupère la hauteur de l'en-tête actuel.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Valeur de retour

La hauteur de l’en-tête, en pixels.

### <a name="remarks"></a>Notes

Appelez la [feuille CMFCProperty ::EnablePageHeader](#enablepageheader) méthode avant d’appeler cette méthode.

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>Feuille CMFCProperty::GetLook

Récupère une valeur d'énumération qui spécifie l'apparence de la feuille de propriétés actuelle.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Valeur de retour

Une des valeurs de recensement qui spécifie l’apparence de la feuille de propriété. Pour une liste de valeurs possibles, voir le tableau de recensement dans la section Remarques de [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>Feuille CMFCProperty::GetNavBarWidth

Obtient la largeur de la barre de navigation.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la barre de navigation en pixels.

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>Feuille CMFCProperty::GetTab

Récupère l'objet de contrôle d'onglet interne qui prend en charge le contrôle de feuille de propriétés actuel.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet de contrôle interne de l’onglet.

### <a name="remarks"></a>Notes

Vous pouvez définir une feuille de propriété de sorte qu’elle apparaît dans différents styles, tels qu’un contrôle d’arbre, une liste de boutons de navigation, ou un ensemble de pages tabbed.

Avant d’appeler cette méthode, appelez la [feuille CMFCProperty ::SetLook](#setlook) méthode pour définir l’apparence de la commande de feuille de propriété. Appelez ensuite la [feuille CMFCProperty ::InitNavigationControl](#initnavigationcontrol) méthode pour initialiser l’objet de contrôle de l’onglet interne. Utilisez cette méthode pour récupérer l’objet de contrôle de l’onglet, puis utilisez cet objet pour travailler avec les onglets sur la feuille de propriété.

Cette méthode affirme en mode débogé si le contrôle de la feuille de propriété n’est pas configuré pour apparaître dans le style de Microsoft OneNote.

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>Feuille CMFCProperty::InitNavigationControl

Initialise l'apparence du contrôle de feuille de propriétés actuel.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre du contrôle de la feuille de propriété.

### <a name="remarks"></a>Notes

Un contrôle de la feuille de propriété peut apparaître sous plusieurs formes différentes, telles qu’un ensemble de pages tabbed, un contrôle d’arbre, ou une liste de boutons de navigation. Utilisez la [feuille CMFCProperty ::SetLook](#setlook) méthode pour spécifier l’apparence de la commande de la feuille de propriété.

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>Feuille CMFCProperty::OnActivatePage

Appelé par l'infrastructure quand une page de propriétés est activée.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
[dans] Pointeur vers un objet de page de propriété qui représente la page de propriété activée.

### <a name="remarks"></a>Notes

Par défaut, cette méthode garantit que la page de propriété activée est défichée en vue. Si le style de la feuille de propriété actuelle contient un volet Microsoft Outlook, cette méthode définit le bouton Outlook correspondant à l’état vérifié.

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CmFCPropertySheet::OnDrawPageHeader

Appelé par le cadre pour dessiner l’en-tête pour une page de propriété personnalisée.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil.

*nPage*<br/>
[dans] Le numéro de page de propriété à base nulle.

*rectHeader (en)*<br/>
[dans] Un rectangle de délimitation qui spécifie où dessiner la tête.

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Si vous remplacez cette méthode, appelez la [feuille CMFCProperty : : Méthode EnablePageHeader](#enablepageheader) avant que le cadre n’appelle cette méthode.

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CmFCPropertySheet::OnRemoveTreePage

Appelé par l'infrastructure pour supprimer une page de propriétés d'un contrôle d'arborescence.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
[dans] Pointeur vers un objet de page de propriété qui représente la page de propriété à supprimer.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>Feuille CMFCProperty::RemoveCategory

Supprime un nœud du contrôle d’arborescence.

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Paramètres

*pCatégory*<br/>
[dans] Pointeur vers une catégorie (nœud) à supprimer.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour enlever un nœud, qui est également appelé une catégorie, d’un contrôle des arbres. Utilisez la [feuille CMFCProperty ::AddTreeCategory](#addtreecategory) méthode pour ajouter un nœud à un contrôle des arbres.

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>Feuille DE CMFCProperty::SupprimerPage

Supprime une page de propriétés de la feuille de propriétés.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
[dans] Pointeur vers l’objet de page de propriété qui représente la page de propriété à supprimer. Ne peut pas avoir la valeur NULL.

*nPage*<br/>
[dans] Index zéro de la page à supprimer.

### <a name="remarks"></a>Notes

Cette méthode supprime la page de propriété spécifiée et détruit sa fenêtre associée. L’objet de la page de propriété que le paramètre *pPage* précise n’est pas détruit jusqu’à ce que la fenêtre [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) soit fermée.

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>Feuille CMFCProperty::SetIconsList

Spécifie la liste des images utilisées dans le contrôle de navigation du volet Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Paramètres

*uiImageListResID*<br/>
[dans] L’ID de ressource d’une liste d’images.

*Cx*<br/>
[dans] La largeur, en pixels, des icônes dans la liste d’images.

*clrTransparent*<br/>
[dans] La couleur transparente de l’image. Les parties de l’image qui sont cette couleur seront transparentes. La valeur par défaut est la couleur magenta, RGB(255,0,255).

*hIcons*<br/>
[dans] Une poignée à une liste d’images existante.

### <a name="return-value"></a>Valeur de retour

Dans la première syntaxe de surcharge de méthode, VRAI si cette méthode est réussie ; autrement, FALSE.

### <a name="remarks"></a>Notes

Si la feuille de propriété est dans le style de Microsoft Outlook, le cadre affiche une liste de boutons de navigation, appelé le contrôle de la vitre Outlook, à gauche de la feuille de propriété. Utilisez cette méthode pour définir la liste d’images à utiliser par le contrôle de la vitre Outlook.

Pour plus d’informations sur les méthodes qui prennent en charge cette méthode, voir [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) and [CImageList::Ajouter](../../mfc/reference/cimagelist-class.md#add). Pour plus d’informations sur la façon de définir le style d’une feuille de propriété, voir [CMFCPropertySheet:SetLook](#setlook).

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>Feuille CMFCProperty::SetLook

Spécifie l'apparence de la feuille de propriétés.

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Paramètres

*Regarder*<br/>
[dans] Une des valeurs de recensement qui spécifie l’apparence de la feuille de propriété. Le style par défaut `CMFCPropertySheet::PropSheetLook_Tabs`pour une feuille de propriété est . Pour plus d’informations, consultez le tableau dans la section Remarques de ce sujet.

*nNavControlWidth (en)*<br/>
[dans] La largeur du contrôle de navigation, en pixels. La valeur par défaut est 100.

### <a name="remarks"></a>Notes

Pour afficher une feuille de propriété dans un style autre que le défaut, appelez cette méthode avant de créer la fenêtre de feuille de propriété.

Le tableau suivant répertorie les valeurs d’énumération qui peuvent être spécifiées dans le *paramètre d’apparence.*

|Valeur|Description|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Par défaut) Affiche un onglet pour chaque page de propriété. Les onglets sont affichés en haut de la feuille de propriété et sont empilés s’il y a plus d’onglets que dans une seule rangée.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Affiche une liste de boutons de navigation, dans le style de la barre Microsoft Outlook, sur le côté gauche de la feuille de propriété. Chaque bouton de la liste correspond à une page de propriété. Le cadre affiche des flèches de défilement s’il y a plus de boutons que dans la zone visible de la liste.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Affiche un contrôle d’arbre sur le côté gauche de la feuille de propriété. Chaque parent ou nœud d’enfant du contrôle de l’arbre correspond à une page de propriété. Le cadre affiche des flèches de défilement s’il y a plus de nœuds que dans la zone visible du contrôle des arbres.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Affiche un onglet, dans le style de Microsoft OneNote, pour chaque page de propriété. Le cadre affiche des onglets en haut de la feuille de propriété et défilent des flèches s’il y a plus d’onglets que dans une seule rangée.|
|`CMFCPropertySheet::PropSheetLook_List`|Affiche une liste sur le côté gauche de la feuille de propriété. Chaque élément de liste correspond à une page de propriété. Le cadre affiche des flèches de défilement s’il y a plus d’éléments de liste que dans la zone visible de la liste.|

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage, classe](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[Classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
