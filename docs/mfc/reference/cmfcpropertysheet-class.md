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
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505049"
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
|[CMFCPropertySheet:: CMFCPropertySheet](#cmfcpropertysheet)|Construit un objet `CMFCPropertySheet`.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPropertySheet:: AddPage](#addpage)|Ajoute une page à la feuille de propriétés.|
|[CMFCPropertySheet:: AddPageToTree](#addpagetotree)|Ajoute une nouvelle page de propriétés au contrôle d'arborescence.|
|[CMFCPropertySheet:: AddTreeCategory](#addtreecategory)|Ajoute un nouveau nœud au contrôle d'arborescence.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Réserve de l'espace en haut de chaque page pour dessiner un en-tête personnalisé.|
|[CMFCPropertySheet:: GetHeaderHeight](#getheaderheight)|Récupère la hauteur de l'en-tête actuel.|
|[CMFCPropertySheet:: GetLook](#getlook)|Récupère une valeur d'énumération qui spécifie l'apparence de la feuille de propriétés actuelle.|
|[CMFCPropertySheet:: GetNavBarWidth](#getnavbarwidth)|Réessaie la largeur de la barre de navigation en pixels.|
|[CMFCPropertySheet:: GetTab](#gettab)|Récupère l'objet de contrôle d'onglet interne qui prend en charge le contrôle de feuille de propriétés actuel.|
|`CMFCPropertySheet::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol)|Initialise l'apparence du contrôle de feuille de propriétés actuel.|
|[CMFCPropertySheet:: OnActivatePage](#onactivatepage)|Appelé par l'infrastructure quand une page de propriétés est activée.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Appelé par l'infrastructure pour dessiner un en-tête de page de propriétés personnalisé.|
|`CMFCPropertySheet::OnInitDialog`|Gère le message [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Substitue [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Appelé par l'infrastructure pour supprimer une page de propriétés d'un contrôle d'arborescence.|
|`CMFCPropertySheet::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Substitue `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet:: RemoveCategory](#removecategory)|Supprime un nœud du contrôle d’arborescence.|
|[CMFCPropertySheet:: RemovePage](#removepage)|Supprime une page de propriétés de la feuille de propriétés.|
|[CMFCPropertySheet:: SetIconsList](#seticonslist)|Spécifie la liste des images utilisées dans le contrôle de navigation du volet Outlook.|
|[CMFCPropertySheet:: SetLook](#setlook)|Spécifie l'apparence de la feuille de propriétés.|

## <a name="remarks"></a>Notes

La classe `CMFCPropertySheet` représente les feuilles de propriétés, aussi appelées boîtes de dialogue à onglets. La classe `CMFCPropertySheet` peut afficher une page de propriétés de diverses manières.

Pour utiliser la classe `CMFCPropertySheet` dans votre application, procédez comme suit :

1. Faites dériver une classe de la classe `CMFCPropertySheet` et nommez-la, par exemple, CMyPropertySheet.

1. Construisez un objet [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) pour chaque page de propriétés.

1. Appelez la méthode [CMFCPropertySheet:: SetLook](#setlook) dans le constructeur CMyPropertySheet. Un paramètre de cette méthode permet de spécifier sous quelle forme les pages de propriétés seront affichées : onglets le long de la bordure supérieure ou gauche de la feuille de propriétés ; onglets dans le style d'une feuille de propriétés Microsoft OneNote ; boutons sur un contrôle de barre d'outils Microsoft Outlook ; nœuds sur un contrôle d'arborescence ; ou liste d'éléments sur le côté gauche de la feuille de propriétés.

1. Si vous créez une feuille de propriétés dans le style d’une barre d’outils Microsoft Outlook, appelez la méthode [CMFCPropertySheet:: SetIconsList](#seticonslist) pour associer une liste d’images aux pages de propriétés.

1. Appelez la méthode [CMFCPropertySheet:: AddPage](#addpage) pour chaque page de propriétés.

1. Créez un contrôle `CMFCPropertySheet` et appelez sa méthode `DoModal`.

## <a name="illustrations"></a>Illustrations

L'illustration suivante représente une feuille de propriétés dont le style est celui d'une barre d'outils Microsoft Outlook incorporée. La barre d'outils Outlook s'affiche sur le côté gauche de la feuille de propriétés.

![Contrôles de couleur CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Contrôles de couleur CMFCPropertySheet")

L’illustration suivante représente une feuille de propriétés qui contient un objet de [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) . Cet objet est une feuille de propriétés dont le style est celui d'une feuille de propriétés de contrôles communs standard.

![Contrôles de liste et de propriété CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "Contrôles de liste et de propriété CMFCPropertySheet")

L’illustration suivante représente une feuille de propriétés dont le style est celui d’un contrôle d’arborescence.

![Arborescence des propriétés](../../mfc/reference/media/proptree.png "Arborescence des propriétés")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxpropertysheet. h

##  <a name="addpage"></a>  CMFCPropertySheet::AddPage

Ajoute une page à la feuille de propriétés.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
dans Pointeur vers un objet page. Ce paramètre ne peut pas être NULL.

### <a name="remarks"></a>Notes

Cette méthode ajoute la page de propriétés spécifiée comme onglet le plus à droite dans la feuille de propriétés. Par conséquent, utilisez cette méthode pour ajouter des pages dans l’ordre de gauche à droite.

Si la feuille de propriétés est dans le style de Microsoft Outlook, l’infrastructure affiche une liste de boutons de navigation à gauche de la feuille de propriétés. Une fois que cette méthode a ajouté une page de propriétés, elle ajoute un bouton correspondant à la liste. Pour afficher une page de propriétés, cliquez sur le bouton correspondant. Pour plus d’informations sur les styles des feuilles de propriétés, consultez [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="addpagetotree"></a>CMFCPropertySheet:: AddPageToTree

Ajoute une nouvelle page de propriétés au contrôle d'arborescence.

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Paramètres

*pCategory*<br/>
dans Pointeur vers un nœud d’arborescence parent, ou NULL pour associer la page spécifiée au nœud de niveau supérieur. Appelez la méthode [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) pour obtenir ce pointeur.

*pPage*<br/>
dans Pointeur vers un objet de page de propriétés.

*nIconNum*<br/>
dans Index de base zéro d’une icône, ou-1 si aucune icône n’est utilisée. L’icône s’affiche en regard de la page de propriétés du contrôle d’arborescence lorsque la page n’est pas sélectionnée. La valeur par défaut est -1.

*nSelIconNum*<br/>
dans Index de base zéro d’une icône, ou-1 si aucune icône n’est utilisée. L’icône s’affiche en regard de la page de propriétés du contrôle d’arborescence lorsque la page est sélectionnée. La valeur par défaut est -1.

### <a name="remarks"></a>Notes

Cette méthode ajoute une page de propriétés en tant que feuille d’un contrôle d’arborescence. Pour ajouter une page de propriétés, créez `CMFCPropertySheet` un objet, appelez la méthode [CMFCPropertySheet:: SetLook](#setlook) avec le paramètre *look* défini `CMFCPropertySheet::PropSheetLook_Tree`sur, puis utilisez cette méthode pour ajouter la page de propriétés.

##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory

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
dans Nom du nœud.

*nIconNum*<br/>
dans Index de base zéro d’une icône, ou-1 si aucune icône n’est utilisée. L’icône s’affiche en regard de la page de propriétés du contrôle d’arborescence lorsque la page n’est pas sélectionnée. La valeur par défaut est -1.

*nSelectedIconNum*<br/>
dans Index de base zéro d’une icône, ou-1 si aucune icône n’est utilisée. L’icône s’affiche en regard de la page de propriétés du contrôle d’arborescence lorsque la page est sélectionnée. La valeur par défaut est -1.

*pParentCategory*<br/>
dans Pointeur vers un nœud d’arborescence parent, ou NULL pour associer la page spécifiée au nœud de niveau supérieur. Définissez ce paramètre avec la méthode [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

### <a name="return-value"></a>Valeur de retour

Pointeur vers le nouveau nœud dans le contrôle d’arborescence.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour ajouter un nouveau nœud, également appelé catégorie, au contrôle d’arborescence. Pour ajouter un nœud, créez un `CMFCPropertySheet` objet, appelez la méthode [CMFCPropertySheet:: SetLook](#setlook) avec le paramètre *look* défini sur `CMFCPropertySheet::PropSheetLook_Tree`, puis utilisez cette méthode pour ajouter le nœud.

Utilisez la valeur de retour de cette méthode dans les appels suivants à [CMFCPropertySheet:: AddPageToTree](#addpagetotree) et [CMFCPropertySheet:: AddTreeCategory](#addtreecategory).

##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet

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
dans Chaîne qui contient la légende de la feuille de propriétés. Ne peut pas être Null.

*nIDCaption*<br/>
dans ID de ressource qui contient la légende de la feuille de propriétés.

*pParentWnd*<br/>
dans Pointeur vers la fenêtre parente de la feuille de propriétés, ou NULL si la fenêtre parente est la fenêtre principale de l’application. La valeur par défaut est NULL.

*iSelectPage*<br/>
dans Index de base zéro de la page de propriétés supérieure. La valeur par défaut est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez les paramètres du constructeur [CPropertySheet:: CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) .

##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader

Réserve de l'espace en haut de chaque page pour dessiner un en-tête personnalisé.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Paramètres

*nHeaderHeight*<br/>
dans Hauteur de l’en-tête, en pixels.

### <a name="remarks"></a>Notes

Pour utiliser la valeur du paramètre *nHeaderHeight* pour dessiner un en-tête personnalisé, substituez la méthode [CMFCPropertySheet:: OnDrawPageHeader](#ondrawpageheader) .

##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight

Récupère la hauteur de l'en-tête actuel.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Valeur de retour

Hauteur de l’en-tête, en pixels.

### <a name="remarks"></a>Notes

Appelez la méthode [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) avant d’appeler cette méthode.

##  <a name="getlook"></a>CMFCPropertySheet:: GetLook

Récupère une valeur d'énumération qui spécifie l'apparence de la feuille de propriétés actuelle.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Valeur de retour

L’une des valeurs d’énumération qui spécifie l’apparence de la feuille de propriétés. Pour obtenir la liste des valeurs possibles, consultez le tableau d’énumération dans la section Notes de [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth

Obtient la largeur de la barre de navigation.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la barre de navigation en pixels.

##  <a name="gettab"></a>CMFCPropertySheet:: GetTab

Récupère l'objet de contrôle d'onglet interne qui prend en charge le contrôle de feuille de propriétés actuel.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Valeur de retour

Objet de contrôle d’onglet interne.

### <a name="remarks"></a>Notes

Vous pouvez définir une feuille de propriétés afin qu’elle apparaisse dans différents styles, par exemple un contrôle d’arborescence, une liste de boutons de navigation ou un ensemble de pages à onglets.

Avant d’appeler cette méthode, appelez la méthode [CMFCPropertySheet:: SetLook](#setlook) pour définir l’apparence du contrôle de feuille de propriétés. Appelez ensuite la méthode [CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol) pour initialiser l’objet de contrôle d’onglet interne. Utilisez cette méthode pour récupérer l’objet de contrôle Tab, puis utilisez cet objet pour utiliser les onglets de la feuille de propriétés.

Cette méthode déclare en mode débogage si le contrôle de feuille de propriétés n’est pas défini pour apparaître dans le style de Microsoft OneNote.

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet:: InitNavigationControl

Initialise l'apparence du contrôle de feuille de propriétés actuel.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre du contrôle de feuille de propriétés.

### <a name="remarks"></a>Notes

Un contrôle de feuille de propriétés peut apparaître sous différentes formes, comme un ensemble de pages à onglets, un contrôle d’arborescence ou une liste de boutons de navigation. Utilisez la méthode [CMFCPropertySheet:: SetLook](#setlook) pour spécifier l’apparence du contrôle de feuille de propriétés.

##  <a name="onactivatepage"></a>CMFCPropertySheet:: OnActivatePage

Appelé par l'infrastructure quand une page de propriétés est activée.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
dans Pointeur vers un objet de page de propriétés qui représente la page de propriétés activée.

### <a name="remarks"></a>Notes

Par défaut, cette méthode permet de faire défiler la page de propriétés activé vers l’affichage. Si le style de la feuille de propriétés actuelle contient un volet Microsoft Outlook, cette méthode définit le bouton Outlook correspondant à l’état activé.

##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader

Appelé par l’infrastructure pour dessiner l’en-tête d’une page de propriétés personnalisée.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*nPage*<br/>
dans Numéro de la page de propriétés de base zéro.

*rectHeader*<br/>
dans Rectangle englobant qui spécifie où dessiner l’en-tête.

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Si vous substituez cette méthode, appelez la méthode [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) avant que le Framework appelle cette méthode.

##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage

Appelé par l'infrastructure pour supprimer une page de propriétés d'un contrôle d'arborescence.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
dans Pointeur vers un objet de page de propriétés qui représente la page de propriétés à supprimer.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit; Sinon, FALSe.

##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory

Supprime un nœud du contrôle d’arborescence.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Paramètres

*pCategory*<br/>
dans Pointeur désignant une catégorie (nœud) à supprimer.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour supprimer un nœud, également appelé catégorie, d’un contrôle d’arborescence. Utilisez la méthode [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) pour ajouter un nœud à un contrôle d’arborescence.

##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage

Supprime une page de propriétés de la feuille de propriétés.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
dans Pointeur vers un objet de page de propriétés qui représente la page de propriétés à supprimer. Ne peut pas être Null.

*nPage*<br/>
dans Index de base zéro de la page à supprimer.

### <a name="remarks"></a>Notes

Cette méthode supprime la page de propriétés spécifiée et détruit la fenêtre qui lui est associée. L’objet page de propriétés que le paramètre *pPage* spécifie n’est pas détruit tant que la fenêtre [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) n’est pas fermée.

##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList

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
dans ID de ressource d’une liste d’images.

*cx*<br/>
dans Largeur, en pixels, des icônes dans la liste d’images.

*clrTransparent*<br/>
dans Couleur transparente de l’image. Les parties de l’image qui sont de cette couleur sont transparentes. La valeur par défaut est la couleur magenta, RGB (255, 0255).

*hIcons*<br/>
dans Handle d’une liste d’images existante.

### <a name="return-value"></a>Valeur de retour

Dans la première syntaxe de surcharge de méthode, TRUE si cette méthode réussit; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si la feuille de propriétés est dans le style de Microsoft Outlook, l’infrastructure affiche une liste de boutons de navigation, appelée contrôle de volet Outlook, à gauche de la feuille de propriétés. Utilisez cette méthode pour définir la liste d’images à utiliser par le contrôle de volet Outlook.

Pour plus d’informations sur les méthodes qui prennent en charge cette méthode, consultez [CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) et [CImageList:: Add](../../mfc/reference/cimagelist-class.md#add). Pour plus d’informations sur la façon de définir le style d’une feuille de propriétés, consultez [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="setlook"></a>CMFCPropertySheet:: SetLook

Spécifie l'apparence de la feuille de propriétés.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Paramètres

*look*<br/>
dans L’une des valeurs d’énumération qui spécifie l’apparence de la feuille de propriétés. Le style par défaut d’une feuille de `CMFCPropertySheet::PropSheetLook_Tabs`propriétés est. Pour plus d’informations, consultez le tableau de la section Remarques de cette rubrique.

*nNavControlWidth*<br/>
dans Largeur du contrôle de navigation, en pixels. La valeur par défaut est 100.

### <a name="remarks"></a>Notes

Pour afficher une feuille de propriétés dans un style autre que celui par défaut, appelez cette méthode avant de créer la fenêtre de la feuille de propriétés.

Le tableau suivant répertorie les valeurs d’énumération qui peuvent être spécifiées dans le paramètre *look* .

|Valeur|Description|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|Valeurs Affiche un onglet pour chaque page de propriétés. Les onglets sont affichés en haut de la feuille de propriétés et sont empilés s’il y a plus d’onglets que dans une seule ligne.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Affiche une liste de boutons de navigation, dans le style de la barre Microsoft Outlook, sur le côté gauche de la feuille de propriétés. Chaque bouton de la liste correspond à une page de propriétés. L’infrastructure affiche des flèches de défilement si le nombre de boutons est supérieur à la taille de la zone visible de la liste.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Affiche un contrôle d’arborescence sur le côté gauche de la feuille de propriétés. Chaque nœud parent ou enfant du contrôle d’arborescence correspond à une page de propriétés. L’infrastructure affiche des flèches de défilement si le nombre de nœuds est supérieur au nombre de nœuds visibles dans la zone visible du contrôle d’arborescence.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Affiche un onglet, dans le style de Microsoft OneNote, pour chaque page de propriétés. L’infrastructure affiche des onglets en haut de la feuille de propriétés et des flèches de défilement si le nombre d’onglets est supérieur à la taille d’une seule ligne.|
|`CMFCPropertySheet::PropSheetLook_List`|Affiche une liste sur le côté gauche de la feuille de propriétés. Chaque élément de liste correspond à une page de propriétés. L’infrastructure affiche des flèches de défilement s’il y a plus d’éléments de liste que ce qui peut être contenu dans la zone visible de la liste.|

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage, classe](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)
