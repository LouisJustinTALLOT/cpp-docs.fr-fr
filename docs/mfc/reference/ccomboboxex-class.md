---
title: CComboBoxEx (classe)
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: c3fd57510a38d597b827f80ab98a0be280ad31e3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767767"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx (classe)

Étend le contrôle de zone de liste déroulante en fournissant la prise en charge des listes d'images.

## <a name="syntax"></a>Syntaxe

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Construit un objet `CComboBoxEx`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|Crée la zone de liste modifiable et l’attache à la `CComboBoxEx` objet.|
|[CComboBoxEx::CreateEx](#createex)|Crée une zone de liste déroulante avec les styles étendus Windows spécifiés et l’attache à un `ComboBoxEx` objet.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Supprime un élément d’un `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Récupère un pointeur vers le contrôle de zone de liste modifiable enfant.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Récupère le handle vers la partie de contrôle d’édition une `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus qui sont en cours d’utilisation pour un `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetImageList](#getimagelist)|Récupère un pointeur vers la liste d’images assignée à un `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetItem](#getitem)|Récupère d’élément d’informations pour une donnée `ComboBoxEx` élément.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Détermine si l’utilisateur a modifié le contenu de la `ComboBoxEx` contrôle d’édition en tapant.|
|[CComboBoxEx::InsertItem](#insertitem)|Insère un nouvel élément dans un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Définit les styles étendus au sein d’un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetImageList](#setimagelist)|Définit une liste d’images pour un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetItem](#setitem)|Définit les attributs d’un élément dans un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Définit le style visuel de la liste déroulante étendue de contrôle de zone.|

## <a name="remarks"></a>Notes

À l’aide de `CComboBoxEx` pour créer des contrôles de zone de liste déroulante, vous n’avez plus besoin d’implémenter votre propre code de dessin de l’image. Au lieu de cela, utilisez `CComboBoxEx` aux images de l’accès à partir d’une liste d’images.

## <a name="image-list-support"></a>Prise en charge de la liste des images

Dans une zone de liste modifiable, le propriétaire de la zone de liste déroulante est responsable du dessin d’une image en créant la zone de liste modifiable en tant qu’un contrôle owner-draw. Lorsque vous utilisez `CComboBoxEx`, vous n’avez pas besoin de définir les styles de dessin CBS_OWNERDRAWFIXED et CBS_HASSTRINGS, car elles sont implicites. Sinon, vous devez écrire du code pour effectuer des opérations de dessin. Un `CComboBoxEx` contrôle prend en charge jusqu'à trois images par élément : un pour un état sélectionné, un pour un état désélectionné et l’autre pour une image de superposition.

## <a name="styles"></a>Styles

`CComboBoxEx` prend en charge les styles CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST et WS_CHILD. Tous les autres styles passées lors de la création de la fenêtre sont ignorés par le contrôle. Une fois que la fenêtre est créée, vous pouvez fournir autre liste déroulante styles de zone en appelant le `CComboBoxEx` fonction membre [SetExtendedStyle](#setextendedstyle). Avec ces styles, vous pouvez :

- Ensemble des recherches de chaîne dans la liste pour respecter la casse.

- Créer un contrôle combo box qui utilise une barre oblique (« / »), barre oblique inverse ('\\') et la période ('. ') caractères en tant que délimiteurs de word. Cela permettre aux utilisateurs d’accéder à partir d’un mot à un autre, en utilisant le raccourci clavier CTRL + flèche.

- Définissez la liste déroulante contrôle de zone pour afficher ou non afficher une image. Si aucune image n’est affichée, la zone de liste modifiable peut supprimer le retrait du texte qui prend en charge une image.

- Créer un contrôle de zone de liste déroulante étroit, notamment le dimensionnement d’afin qu’elle découpe la zone de liste déroulante plus large qu’elle contient.

Ces indicateurs de style sont décrites dans [à l’aide de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Rétention des éléments et attributs d’élément de rappel

Informations sur les éléments, tels que des index pour les éléments et les images, les valeurs de mise en retrait et les chaînes de texte, sont stockées dans la structure Win32 [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema), comme décrit dans le SDK Windows. La structure contient également les membres qui correspondent aux indicateurs de rappel.

Pour une explication détaillée, conceptuelle, consultez [à l’aide de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

Appelez cette fonction membre pour créer un `CComboBoxEx` objet.

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

Crée la zone de liste modifiable et l’attache à la `CComboBoxEx` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie la combinaison de styles de zone de liste déroulante appliqué à la zone de liste déroulante. Consultez **notes** ci-dessous pour plus d’informations sur les styles.

*rect*<br/>
Une référence à un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou [RECT](/previous-versions/dd162897\(v=vs.85\)) structure, qui est la position et la taille de la zone de liste déroulante.

*pParentWnd*<br/>
Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente de la zone de liste déroulante (généralement un `CDialog`). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle. de zone de liste déroulante

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet a été créé avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Créer un `CComboBoxEx` objet en deux étapes :

1. Appelez [CComboBoxEx](#ccomboboxex) pour construire un `CComboBoxEx` objet.

1. Appelez cette fonction membre, ce qui crée la zone de liste déroulante étendue Windows et l’attache à la `CComboBoxEx` objet.

Lorsque vous appelez `Create`, MFC initialise les contrôles communs.

Lorsque vous créez la zone de liste déroulante, vous pouvez spécifier tout ou partie des styles de zone de liste déroulante suivantes :

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Tous les autres styles passées lors de la création de la fenêtre sont ignorés. Le `ComboBoxEx` contrôle prend également en charge les styles étendus qui fournissent des fonctionnalités supplémentaires. Ces styles sont décrites dans [ComboBoxEx contrôler des styles étendus](/windows/desktop/Controls/comboboxex-control-extended-styles), dans le SDK Windows. Définir ces styles en appelant [SetExtendedStyle](#setextendedstyle).

Si vous souhaitez utiliser des styles étendus windows avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create`.

##  <a name="createex"></a>  CComboBoxEx::CreateEx

Appelez cette fonction pour créer un contrôle de zone de liste déroulante étendue (une fenêtre enfant) et l’associer avec le `CComboBoxEx` objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
Style du contrôle de zone de liste déroulante. Consultez [créer](#create) pour obtenir la liste des styles.

*rect*<br/>
Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de `Create` pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

`CreateEx` crée le contrôle avec les styles étendus de Windows spécifiés par *dwExStyle*. Vous devez définir des styles étendus propres à un contrôle de zone de liste déroulante étendue à l’aide [SetExtendedStyle](#setextendedstyle). Par exemple, utilisez `CreateEx` pour définir des styles de ce type en tant que WS_EX_CONTEXTHELP, mais utiliser `SetExtendedStyle` pour définir des styles de ce type comme CBES_EX_CASESENSITIVE. Pour plus d’informations, consultez les styles décrites dans la rubrique [ComboBoxEx contrôle étendu Styles](/windows/desktop/Controls/comboboxex-control-extended-styles) dans le SDK Windows.

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

Supprime un élément d’un `ComboBoxEx` contrôle.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
Index de base zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments restants dans le contrôle. Si *iIndex* est non valide, la fonction retourne CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem), comme décrit dans le SDK Windows. Lorsque vous appelez DeleteItem, un [WM_NOTIFY](/windows/desktop/controls/wm-notify) message avec notification de CBEN_DELETEITEM sera envoyé à la fenêtre parente.

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

Appelez cette fonction membre pour obtenir un pointeur vers un contrôle combo box dans un `CComboBoxEx` objet.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CComboBox` .

### <a name="remarks"></a>Notes

Le `CComboBoxEx` contrôle se compose d’une fenêtre parente, qui encapsule un `CComboBox`.

Le `CComboBox` objet désigné par la valeur de retour est un objet temporaire et est détruit pendant la durée de traitement d’inactivité suivante.

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

Appelez cette fonction membre pour obtenir un pointeur vers le contrôle d’édition pour une zone de liste déroulante.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CEdit](../../mfc/reference/cedit-class.md) objet.

### <a name="remarks"></a>Notes

Un `CComboBoxEx` contrôle utilise une zone d’édition lorsqu’il est créé avec le style CBS_DROPDOWN.

Le `CEdit` objet désigné par la valeur de retour est un objet temporaire et est détruit pendant la durée de traitement d’inactivité suivante.

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

Appelez cette fonction membre pour obtenir les styles étendus utilisés pour un `CComboBoxEx` contrôle.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur DWORD qui contient les styles étendus qui sont utilisés pour le contrôle de zone de liste déroulante.

### <a name="remarks"></a>Notes

Consultez [ComboBoxEx contrôle étendu Styles](/windows/desktop/Controls/comboboxex-control-extended-styles) dans le SDK Windows pour plus d’informations sur ces styles.

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

Appelez cette fonction membre pour obtenir un pointeur vers la liste d’images utilisée par un `CComboBoxEx` contrôle.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet. En cas d’échec, cette fonction membre retourne NULL.

### <a name="remarks"></a>Notes

Le `CImageList` objet désigné par la valeur de retour est un objet temporaire et est détruit pendant la durée de traitement d’inactivité suivante.

##  <a name="getitem"></a>  CComboBoxEx::GetItem

Récupère d’élément d’informations pour une donnée `ComboBoxEx` élément.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Un pointeur vers un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) structure qui recevra les informations d’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem), comme décrit dans le SDK Windows.

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

Détermine si l’utilisateur a modifié le contenu de la `ComboBoxEx` contrôle d’édition en tapant.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a tapé dans la zone d’édition du contrôle ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged), comme décrit dans le SDK Windows.

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

Insère un nouvel élément dans un `ComboBoxEx` contrôle.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Un pointeur vers un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) structure qui recevra les informations d’élément. Cette structure contient des valeurs d’indicateur de rappel pour l’élément.

### <a name="return-value"></a>Valeur de retour

L’index au niveau duquel le nouvel élément a été inséré en cas de réussite ; sinon -1.

### <a name="remarks"></a>Notes

Lorsque vous appelez `InsertItem`, un [WM_NOTIFY](/windows/desktop/controls/wm-notify) message avec [CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem) notification sera envoyée à la fenêtre parente.

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

Appelez cette fonction membre pour définir les styles étendus utilisés pour une zone de liste déroulante étendue du contrôle.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Paramètres

*dwExMask*<br/>
Une valeur DWORD qui indique les styles dans *dwExStyles* sont affectées. Uniquement les styles étendus dans *dwExMask* sera modifié. Tous les autres styles seront conservées en l’état. Si ce paramètre est zéro, tous les styles dans *dwExStyles* seront affectées.

*dwExStyles*<br/>
Une valeur DWORD qui contient le contrôle de zone de liste déroulante étendue des styles à définir pour le contrôle.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient les styles étendus précédemment utilisés pour le contrôle.

### <a name="remarks"></a>Notes

Consultez [ComboBoxEx contrôle étendu Styles](/windows/desktop/Controls/comboboxex-control-extended-styles) dans le SDK Windows pour plus d’informations sur ces styles.

Pour créer une zone de liste déroulante étendue de contrôle avec des styles d’étendues de windows, utilisez [CreateEx](#createex).

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

Définit une liste d’images pour un `ComboBoxEx` contrôle.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Un pointeur vers un `CImageList` objet contenant les images à utiliser avec le `CComboBoxEx` contrôle.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet contenant les images précédemment utilisées par le `CComboBoxEx` contrôle. NULL si aucune liste d’images a été défini précédemment.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist), comme décrit dans le SDK Windows. Si vous modifiez la hauteur du contrôle d’édition par défaut, appelez la fonction Win32 [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) pour redimensionner votre contrôle après avoir appelé `SetImageList`, ou il ne s’affiche correctement.

Le `CImageList` objet désigné par la valeur de retour est un objet temporaire et est détruit pendant la durée de traitement d’inactivité suivante.

##  <a name="setitem"></a>  CComboBoxEx::SetItem

Définit les attributs d’un élément dans un `ComboBoxEx` contrôle.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Un pointeur vers un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) structure qui recevra les informations d’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem), comme décrit dans le SDK Windows.

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

Définit le style visuel de la liste déroulante étendue de contrôle de zone.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Pointeur vers une chaîne Unicode qui contient le style visuel de zone de liste déroulante étendue à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité de la [CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme) du message, comme décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC, exemple MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)
