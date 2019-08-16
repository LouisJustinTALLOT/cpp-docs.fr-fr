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
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507182"
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
|[CComboBoxEx::Create](#create)|Crée la zone de liste déroulante et l' `CComboBoxEx` attache à l’objet.|
|[CComboBoxEx::CreateEx](#createex)|Crée une zone de liste déroulante avec les styles étendus Windows spécifiés `ComboBoxEx` et l’attache à un objet.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Supprime un élément d’un `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Récupère un pointeur désignant le contrôle de zone de liste déroulante enfant.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Récupère le handle de la partie du contrôle d’édition d' `ComboBoxEx` un contrôle.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus qui sont utilisés pour un `ComboBoxEx` contrôle.|
|[CComboBoxEx::GetImageList](#getimagelist)|Récupère un pointeur vers la liste d’images assignée `ComboBoxEx` à un contrôle.|
|[CComboBoxEx::GetItem](#getitem)|Récupère des informations d’élément pour un `ComboBoxEx` élément donné.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Détermine si l’utilisateur a modifié le contenu du contrôle `ComboBoxEx` d’édition en tapant.|
|[CComboBoxEx::InsertItem](#insertitem)|Insère un nouvel élément dans un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Définit des styles étendus `ComboBoxEx` dans un contrôle.|
|[CComboBoxEx::SetImageList](#setimagelist)|Définit une liste d’images pour `ComboBoxEx` un contrôle.|
|[CComboBoxEx::SetItem](#setitem)|Définit les attributs d’un élément dans un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Définit le style visuel du contrôle de zone de liste déroulante étendue.|

## <a name="remarks"></a>Notes

En utilisant `CComboBoxEx` pour créer des contrôles de zone de liste déroulante, vous n’avez plus besoin d’implémenter votre propre code de dessin d’image. Utilisez `CComboBoxEx` plutôt pour accéder aux images à partir d’une liste d’images.

## <a name="image-list-support"></a>Prise en charge de la liste d’images

Dans une zone de liste modifiable standard, le propriétaire de la zone de liste déroulante est chargé de dessiner une image en créant la zone de liste déroulante comme contrôle owner-draw. Lorsque vous utilisez `CComboBoxEx`, vous n’avez pas besoin de définir les styles de dessin CBS_OWNERDRAWFIXED et CBS_HASSTRINGS, car ils sont implicites. Dans le cas contraire, vous devez écrire du code pour effectuer des opérations de dessin. Un `CComboBoxEx` contrôle prend en charge jusqu’à trois images par élément: une pour un état sélectionné, une pour un État non sélectionné et une pour une image de superposition.

## <a name="styles"></a>Styles

`CComboBoxEx`prend en charge les styles CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST et WS_CHILD. Tous les autres styles passés lorsque vous créez la fenêtre sont ignorés par le contrôle. Une fois la fenêtre créée, vous pouvez fournir d’autres styles de zone de liste `CComboBoxEx` déroulante en appelant la fonction membre [SetExtendedStyle](#setextendedstyle). Avec ces styles, vous pouvez:

- Définissez les recherches de chaînes dans la liste pour respecter la casse.

- Créez un contrôle de zone de liste déroulante qui utilise la barre oblique («/\\»), la barre oblique inverse («») et le point ('. ') caractères comme délimiteurs de mots. Cela permet aux utilisateurs de passer de Word à Word, en utilisant le raccourci clavier CTRL + Flèche.

- Définissez le contrôle de zone de liste déroulante pour afficher ou ne pas afficher une image. Si aucune image n’est affichée, la zone de liste modifiable peut supprimer le retrait du texte qui prend en charge une image.

- Créez un contrôle de zone de liste modifiable étroite, y compris pour le dimensionner afin qu’il découpe la zone de liste déroulante plus large qu’il contient.

Ces indicateurs de style sont décrits plus en détail dans [utilisation de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Attributs de rétention d’élément et d’élément de rappel

Les informations d’élément, telles que les index pour les éléments et les images, les valeurs de mise en retrait et les chaînes de texte, sont stockées dans la [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)de la structure Win32, comme décrit dans la SDK Windows. La structure contient également des membres qui correspondent aux indicateurs de rappel.

Pour une discussion conceptuelle détaillée, consultez [utilisation de CComboBoxEx](../../mfc/using-ccomboboxex.md).

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

Crée la zone de liste déroulante et l' `CComboBoxEx` attache à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie la combinaison de styles de zone de liste déroulante appliquée à la zone de liste déroulante. Pour plus d’informations sur les styles, consultez les **Remarques** ci-dessous.

*rect*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) , qui est la position et la taille de la zone de liste déroulante.

*pParentWnd*<br/>
Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente de la zone de liste déroulante (généralement `CDialog`). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet a été créé avec succès; Sinon, 0.

### <a name="remarks"></a>Notes

Créez un `CComboBoxEx` objet en deux étapes:

1. Appelez [CComboBoxEx](#ccomboboxex) pour construire un `CComboBoxEx` objet.

1. Appelez cette fonction membre, qui crée la zone de liste déroulante Windows étendue et l' `CComboBoxEx` attache à l’objet.

Lorsque vous appelez `Create`, MFC initialise les contrôles communs.

Lorsque vous créez la zone de liste déroulante, vous pouvez spécifier tout ou partie des styles de zone de liste déroulante suivants:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Tous les autres styles passés lorsque vous créez la fenêtre sont ignorés. Le `ComboBoxEx` contrôle prend également en charge des styles étendus qui fournissent des fonctionnalités supplémentaires. Ces styles sont décrits dans la SDK Windows les [styles étendus de contrôle ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles). Définissez ces styles en appelant [SetExtendedStyle](#setextendedstyle).

Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle, appelez [CreateEx](#createex) au `Create`lieu de.

##  <a name="createex"></a>  CComboBoxEx::CreateEx

Appelez cette fonction pour créer un contrôle de zone de liste déroulante étendue (une fenêtre enfant) `CComboBoxEx` et l’associer à l’objet.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Style du contrôle de zone de liste déroulante. Pour obtenir la liste des styles, consultez [créer](#create) .

*rect*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu `Create` de pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_** .

`CreateEx`crée le contrôle avec les styles Windows étendus spécifiés par *dwExStyle*. Vous devez définir des styles étendus spécifiques à un contrôle de zone de liste déroulante étendue à l’aide de [SetExtendedStyle](#setextendedstyle). Par exemple, utilisez `CreateEx` pour définir des styles tels que WS_EX_CONTEXTHELP, mais `SetExtendedStyle` utilisez pour définir des styles tels que CBES_EX_CASESENSITIVE. Pour plus d’informations, consultez les styles décrits dans la rubrique [ComboBoxEx contrôler les styles étendus](/windows/win32/Controls/comboboxex-control-extended-styles) dans le SDK Windows.

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

Supprime un élément d’un `ComboBoxEx` contrôle.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
Index de base zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments restants dans le contrôle. Si *iIndex* n’est pas valide, la fonction retourne CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem), comme décrit dans la SDK Windows. Quand vous appelez DeleteItem, un message [WM_NOTIFY](/windows/win32/controls/wm-notify) avec notification CBEN_DELETEITEM est envoyé à la fenêtre parente.

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

Appelez cette fonction membre pour obtenir un pointeur vers un contrôle de zone de liste `CComboBoxEx` déroulante dans un objet.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CComboBox` .

### <a name="remarks"></a>Notes

Le `CComboBoxEx` contrôle se compose d’une fenêtre parente, qui encapsule un `CComboBox`.

L' `CComboBox` objet vers lequel pointe la valeur de retour est un objet temporaire et il est détruit pendant le temps de traitement inactif suivant.

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

Appelez cette fonction membre pour obtenir un pointeur vers le contrôle d’édition pour une zone de liste déroulante.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CEdit](../../mfc/reference/cedit-class.md) .

### <a name="remarks"></a>Notes

Un `CComboBoxEx` contrôle utilise une zone d’édition lorsqu’il est créé avec le style CBS_DROPDOWN.

L' `CEdit` objet vers lequel pointe la valeur de retour est un objet temporaire et il est détruit pendant le temps de traitement inactif suivant.

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

Appelez cette fonction membre pour obtenir les styles étendus utilisés pour `CComboBoxEx` un contrôle.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur DWORD qui contient les styles étendus utilisés pour le contrôle de zone de liste déroulante.

### <a name="remarks"></a>Notes

Pour plus d’informations sur ces styles, consultez [ComboBoxEx, contrôle des styles étendus](/windows/win32/Controls/comboboxex-control-extended-styles) dans le SDK Windows.

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

Appelez cette fonction membre pour obtenir un pointeur vers la liste d’images utilisée par `CComboBoxEx` un contrôle.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) . En cas d’échec, cette fonction membre retourne la valeur NULL.

### <a name="remarks"></a>Notes

L' `CImageList` objet vers lequel pointe la valeur de retour est un objet temporaire et il est détruit pendant le temps de traitement inactif suivant.

##  <a name="getitem"></a>  CComboBoxEx::GetItem

Récupère des informations d’élément pour un `ComboBoxEx` élément donné.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem), comme décrit dans la SDK Windows.

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

Détermine si l’utilisateur a modifié le contenu du contrôle `ComboBoxEx` d’édition en tapant.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a tapé la zone d’édition du contrôle; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged), comme décrit dans la SDK Windows.

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

Insère un nouvel élément dans un `ComboBoxEx` contrôle.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément. Cette structure contient des valeurs d’indicateur de rappel pour l’élément.

### <a name="return-value"></a>Valeur de retour

Index auquel le nouvel élément a été inséré en cas de réussite; sinon-1.

### <a name="remarks"></a>Notes

Quand vous appelez `InsertItem`, un message [WM_NOTIFY](/windows/win32/controls/wm-notify) avec notification [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) est envoyé à la fenêtre parente.

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

Appelez cette fonction membre pour définir les styles étendus utilisés pour un contrôle étendu de zone de liste déroulante.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Paramètres

*dwExMask*<br/>
Valeur DWORD qui indique les styles de *dwExStyles* à affecter. Seuls les styles étendus dans *dwExMask* seront modifiés. Tous les autres styles seront conservés tels quels. Si ce paramètre est égal à zéro, tous les styles dans *dwExStyles* seront affectés.

*dwExStyles*<br/>
Valeur DWORD qui contient la zone de liste déroulante styles étendus à définir pour le contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur DWORD qui contient les styles étendus utilisés précédemment pour le contrôle.

### <a name="remarks"></a>Notes

Pour plus d’informations sur ces styles, consultez [ComboBoxEx, contrôle des styles étendus](/windows/win32/Controls/comboboxex-control-extended-styles) dans le SDK Windows.

Pour créer un contrôle étendu de zone de liste déroulante avec des styles Windows étendus, utilisez [CreateEx](#createex).

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

Définit une liste d’images pour `ComboBoxEx` un contrôle.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Pointeur vers un `CImageList` objet contenant les images à utiliser avec le `CComboBoxEx` contrôle.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) contenant les images précédemment utilisées par le `CComboBoxEx` contrôle. NULL si aucune liste d’images n’a été définie précédemment.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist), comme décrit dans la SDK Windows. Si vous modifiez la hauteur du contrôle d’édition par défaut, appelez la fonction Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) pour redimensionner votre contrôle après `SetImageList`l’appel de, ou il ne s’affichera pas correctement.

L' `CImageList` objet vers lequel pointe la valeur de retour est un objet temporaire et il est détruit pendant le temps de traitement inactif suivant.

##  <a name="setitem"></a>  CComboBoxEx::SetItem

Définit les attributs d’un élément dans un `ComboBoxEx` contrôle.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem*<br/>
Pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente les fonctionnalités du message [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem), comme décrit dans la SDK Windows.

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

Définit le style visuel du contrôle de zone de liste déroulante étendue.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Pointeur vers une chaîne Unicode qui contient le style visuel de zone de liste déroulante étendue à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme) , comme décrit dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple de MFCIE MFC](../../overview/visual-cpp-samples.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)
