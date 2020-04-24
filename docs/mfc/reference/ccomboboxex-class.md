---
title: Classe CComboBoxEx
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
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754827"
---
# <a name="ccomboboxex-class"></a>Classe CComboBoxEx

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
|[CComboBoxEx::Créer](#create)|Crée la boîte combo et `CComboBoxEx` la fixe à l’objet.|
|[CComboBoxEx::CreateEx](#createex)|Crée une boîte combo avec les styles Windows `ComboBoxEx` étendus spécifiés et l’attache à un objet.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Supprime un élément `ComboBoxEx` d’un contrôle.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Récupère un pointeur sur le contrôle de la boîte combo enfant.|
|[CComboBoxEx:GetEditCtrl](#geteditctrl)|Récupère la poignée à la partie `ComboBoxEx` de contrôle de modification d’un contrôle.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus qui `ComboBoxEx` sont utilisés pour un contrôle.|
|[CComboBoxEx::GetImageList](#getimagelist)|Récupère un pointeur sur la `ComboBoxEx` liste d’images attribuée à un contrôle.|
|[CComboBoxEx::GetItem](#getitem)|Récupère les informations de `ComboBoxEx` l’élément pour un élément donné.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Détermine si l’utilisateur a modifié `ComboBoxEx` le contenu du contrôle de modification en tapant.|
|[CComboBoxEx::InsertItem](#insertitem)|Insère un nouvel `ComboBoxEx` élément dans un contrôle.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Définit des styles `ComboBoxEx` étendus dans un contrôle.|
|[CComboBoxEx::SetImageList](#setimagelist)|Définit une liste `ComboBoxEx` d’images pour un contrôle.|
|[CComboBoxEx::SetItem](#setitem)|Définit les attributs d’un élément sous un `ComboBoxEx` contrôle.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Définit le style visuel du contrôle de la boîte combo étendue.|

## <a name="remarks"></a>Notes

En `CComboBoxEx` utilisant pour créer des commandes de boîte combo, vous n’avez plus besoin d’implémenter votre propre code de dessin d’image. Utilisez plutôt `CComboBoxEx` pour accéder aux images d’une liste d’images.

## <a name="image-list-support"></a>Support de liste d’images

Dans une boîte combo standard, le propriétaire de la boîte combo est responsable de dessiner une image en créant la boîte combo comme un contrôle propriétaire-tirage. Lorsque vous `CComboBoxEx`utilisez, vous n’avez pas besoin de définir les styles de dessin CBS_OWNERDRAWFIXED et CBS_HASSTRINGS parce qu’ils sont implicites. Sinon, vous devez écrire du code pour effectuer des opérations de dessin. Un `CComboBoxEx` contrôle prend en charge jusqu’à trois images par élément : une pour un état sélectionné, une pour un état non sélectionné et une pour une image superposée.

## <a name="styles"></a>Styles

`CComboBoxEx`soutient les styles CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST et WS_CHILD. Tous les autres styles passés lorsque vous créez la fenêtre sont ignorés par le contrôle. Après la création de la fenêtre, vous pouvez `CComboBoxEx` fournir d’autres styles de boîte combo en appelant la fonction [membre SetExtendedStyle](#setextendedstyle). Avec ces styles, vous pouvez:

- Définissez les recherches en chaîne dans la liste pour être sensibles aux cas.

- Créez un contrôle de boîte combo qui utilise les caractères slash ('/'), backslash ('),\\et période ('.') comme des limiteurs de mots. Cela permet aux utilisateurs de sauter de mot en mot, en utilisant le raccourci clavier CTRLMD ARROW.

- Réglez le contrôle de la boîte combo pour afficher ou non une image. Si aucune image n’est affichée, la boîte combo peut supprimer le texte en retrait qui s’adapte à une image.

- Créez un contrôle étroit de boîte de combo, y compris le dimensionnement ainsi il clips la boîte combo plus large qu’il contient.

Ces drapeaux de style sont décrits plus loin dans [l’utilisation de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Attributs de conservation et d’élément de rappel d’éléments

Les informations sur les éléments, telles que les index pour les éléments et les images, les valeurs d’indentation et les chaînes de texte, sont stockées dans la structure Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), telle que décrite dans le SDK Windows. La structure contient également des membres qui correspondent à des drapeaux de rappel.

Pour une discussion détaillée et conceptuelle, voir [à l’aide de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx

Appelez cette fonction de `CComboBoxEx` membre pour créer un objet.

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx::Créer

Crée la boîte combo et `CComboBoxEx` la fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie la combinaison de styles de boîte combo appliqués à la boîte combo. Voir **Remarques** ci-dessous pour plus d’informations sur les styles.

*Rect*<br/>
Une référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou une structure [RECT,](/windows/win32/api/windef/ns-windef-rect) qui est la position et la taille de la boîte combo.

*pParentWnd*<br/>
Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la `CDialog`fenêtre parente de la boîte combo (généralement un ). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la boîte combo.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Créez `CComboBoxEx` un objet en deux étapes :

1. Appelez [CComboBoxEx](#ccomboboxex) pour `CComboBoxEx` construire un objet.

1. Appelez cette fonction de membre, qui crée la boîte `CComboBoxEx` de combo Windows étendue et la fixe à l’objet.

Lorsque vous `Create`appelez, MFC initialise les contrôles communs.

Lorsque vous créez la boîte combo, vous pouvez spécifier l’un ou l’ensemble des styles combo-box suivants :

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Tous les autres styles passés lorsque vous créez la fenêtre sont ignorés. Le `ComboBoxEx` contrôle prend également en charge les styles étendus qui fournissent des fonctionnalités supplémentaires. Ces styles sont décrits dans [les styles étendus de contrôle De ComboBoxEx,](/windows/win32/Controls/comboboxex-control-extended-styles)dans le SDK Windows. Définissez ces styles en appelant [SetExtendedStyle](#setextendedstyle).

Si vous souhaitez utiliser des styles windows étendus `Create`avec votre contrôle, appelez [CreateEx](#createex) au lieu de .

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx::CreateEx

Appelez cette fonction pour créer un contrôle de boîte combo `CComboBoxEx` étendu (une fenêtre d’enfant) et l’associer à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Le style du contrôle de la boîte combo. Voir [Créer](#create) pour une liste de styles.

*Rect*<br/>
Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au `Create` lieu d’appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

`CreateEx`crée le contrôle avec les styles Windows étendus spécifiés par *dwExStyle*. Vous devez définir des styles étendus spécifiques à un contrôle de boîte combo étendu à l’aide [de SetExtendedStyle](#setextendedstyle). Par exemple, `CreateEx` utilisez-le pour définir des styles `SetExtendedStyle` tels que WS_EX_CONTEXTHELP, mais utilisez pour définir des styles tels que CBES_EX_CASESENSITIVE. Pour plus d’informations, voir les styles décrits dans le sujet [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) dans le Windows SDK.

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::DeleteItem

Supprime un élément `ComboBoxEx` d’un contrôle.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
Indice zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Le nombre d’articles restants dans le contrôle. Si *iIndex* est invalide, la fonction renvoie CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la fonctionnalité du message [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem), tel que décrit dans le SDK Windows. Lorsque vous appelez DeleteItem, un [message WM_NOTIFY](/windows/win32/controls/wm-notify) avec CBEN_DELETEITEM notification sera envoyé à la fenêtre parente.

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl

Appelez cette fonction de membre pour obtenir un `CComboBoxEx` pointeur à un contrôle de boîte de combo dans un objet.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CComboBox`.

### <a name="remarks"></a>Notes

Le `CComboBoxEx` contrôle se compose d’une fenêtre parente, qui encapsule un `CComboBox`.

L’objet `CComboBox` pointé par la valeur de retour est un objet temporaire et est détruit pendant le prochain temps de traitement au ralenti.

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx:GetEditCtrl

Appelez cette fonction de membre pour obtenir un pointeur au contrôle de modification pour une boîte de combo.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur un objet [CEdit.](../../mfc/reference/cedit-class.md)

### <a name="remarks"></a>Notes

Un `CComboBoxEx` contrôle utilise une boîte de modification lorsqu’elle est créée avec le style CBS_DROPDOWN.

L’objet `CEdit` pointé par la valeur de retour est un objet temporaire et est détruit pendant le prochain temps de traitement au ralenti.

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle

Appelez cette fonction de membre pour `CComboBoxEx` obtenir les styles étendus utilisés pour un contrôle.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur DWORD qui contient les styles étendus qui sont utilisés pour le contrôle de la boîte combo.

### <a name="remarks"></a>Notes

Voir [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) in the Windows SDK pour plus d’informations sur ces styles.

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx::GetImageList

Appelez cette fonction de membre pour obtenir un `CComboBoxEx` pointeur à la liste d’images utilisée par un contrôle.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList.](../../mfc/reference/cimagelist-class.md) Si elle échoue, cette fonction de membre renvoie NULL.

### <a name="remarks"></a>Notes

L’objet `CImageList` pointé par la valeur de retour est un objet temporaire et est détruit pendant le prochain temps de traitement au ralenti.

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx::GetItem

Récupère les informations de `ComboBoxEx` l’élément pour un élément donné.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem (en)*<br/>
Un pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la fonctionnalité du message [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem), tel que décrit dans le SDK Windows.

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::HasEditChanged

Détermine si l’utilisateur a modifié `ComboBoxEx` le contenu du contrôle de modification en tapant.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur a tapé dans la boîte de modification du contrôle; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la fonctionnalité du message [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged), tel que décrit dans le SDK Windows.

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx::InsertItem

Insère un nouvel `ComboBoxEx` élément dans un contrôle.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem (en)*<br/>
Un pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément. Cette structure contient des valeurs de drapeau de rappel pour l’élément.

### <a name="return-value"></a>Valeur de retour

L’indice auquel le nouvel élément a été inséré en cas de succès; sinon -1.

### <a name="remarks"></a>Notes

Lorsque vous `InsertItem`appelez, un [message WM_NOTIFY](/windows/win32/controls/wm-notify) avec [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) notification sera envoyé à la fenêtre parente.

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle

Appelez cette fonction de membre pour définir les styles étendus utilisés pour un contrôle étendu de boîte de combo.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Paramètres

*dwExMask (en anglais)*<br/>
Une valeur DWORD qui indique quels styles dans *dwExStyles* doivent être affectés. Seuls les styles étendus dans *dwExMask* seront changés. Tous les autres styles seront maintenus tels qu’ils sont. Si ce paramètre est nul, alors tous les styles dans *dwExStyles* seront affectés.

*dwExStyles (en anglais)*<br/>
Une valeur DWORD qui contient les styles de contrôle de la boîte combo étendus à définir pour le contrôle.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient les styles étendus précédemment utilisés pour le contrôle.

### <a name="remarks"></a>Notes

Voir [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) in the Windows SDK pour plus d’informations sur ces styles.

Pour créer un combo box contrôle étendu avec des styles de fenêtres étendues, utilisez [CreateEx](#createex).

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::SetImageList

Définit une liste `ComboBoxEx` d’images pour un contrôle.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList (en)*<br/>
Un pointeur `CImageList` à un objet contenant `CComboBoxEx` les images à utiliser avec le contrôle.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) `CComboBoxEx` contenant les images précédemment utilisées par le contrôle. NULL si aucune liste d’images n’a été précédemment définie.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la fonctionnalité du message [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist), tel que décrit dans le SDK Windows. Si vous modifiez la hauteur du contrôle de modification par défaut, appelez la fonction Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) pour resize votre contrôle après votre appel, `SetImageList`ou il ne s’affichera pas correctement.

L’objet `CImageList` pointé par la valeur de retour est un objet temporaire et est détruit pendant le prochain temps de traitement au ralenti.

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx::SetItem

Définit les attributs d’un élément sous un `ComboBoxEx` contrôle.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Paramètres

*pCBItem (en)*<br/>
Un pointeur vers une structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) qui recevra les informations de l’élément.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la fonctionnalité du message [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem), tel que décrit dans le SDK Windows.

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme

Définit le style visuel du contrôle de la boîte combo étendue.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Un pointeur à une chaîne Unicode qui contient le style visuel de boîte combo étendue à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message [CBEM_SETWINDOWTHEME,](/windows/win32/Controls/cbem-setwindowtheme) tel que décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC, exemple MFCIE](../../overview/visual-cpp-samples.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)
