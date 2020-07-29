---
title: CButton, classe
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 108bbbbb7fcb491ecc9ed278c5f7d5002ad02ef3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231856"
---
# <a name="cbutton-class"></a>CButton, classe

Fournit les fonctionnalités des contrôles bouton Windows.

## <a name="syntax"></a>Syntaxe

```
class CButton : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CButton :: CButton](#cbutton)|Construit un objet `CButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CButton :: Create](#create)|Crée le contrôle bouton Windows et l’attache à l' `CButton` objet.|
|[CButton ::D rawItem](#drawitem)|Substituez pour dessiner un objet owner-drawn `CButton` .|
|[CButton :: GetBitmap](#getbitmap)|Récupère le handle de la bitmap précédemment définie avec [SetBitmap](#setbitmap).|
|[CButton :: GetButtonStyle](#getbuttonstyle)|Récupère des informations sur le style du contrôle bouton.|
|[CButton :: GetCheck](#getcheck)|Récupère l’état d’activation d’un contrôle bouton.|
|[CButton :: GetCursor](#getcursor)|Récupère le handle de l’image de curseur précédemment définie avec [SetCursor](#setcursor).|
|[CButton :: GetIcon](#geticon)|Récupère le handle de l’icône précédemment définie avec [seticon](#seticon).|
|[CButton :: GetIdealSize](#getidealsize)|Récupère la taille idéale du contrôle bouton.|
|[CButton :: GetImageList](#getimagelist)|Récupère la liste d’images du contrôle bouton.|
|[CButton :: GetNote](#getnote)|Récupère le composant de note du contrôle de lien de commande actuel.|
|[CButton :: GetNoteLength](#getnotelength)|Récupère la longueur du texte de la note pour le contrôle de lien de commande actuel.|
|[CButton :: GetSplitGlyph](#getsplitglyph)|Récupère le glyphe associé au contrôle de bouton partagé actuel.|
|[CButton :: GetSplitImageList](#getsplitimagelist)|Récupère la liste d’images pour le contrôle bouton partagé actuel.|
|[CButton :: GetSplitInfo](#getsplitinfo)|Récupère des informations qui définissent le contrôle du bouton partagé actuel.|
|[CButton :: GetSplitSize](#getsplitsize)|Récupère le rectangle englobant du composant de liste déroulante du contrôle bouton partagé actuel.|
|[CButton :: GetSplitStyle](#getsplitstyle)|Récupère les styles de bouton partagé qui définissent le contrôle bouton partagé actuel.|
|[CButton :: GetState](#getstate)|Récupère l’état d’activation, de mise en surbrillance et de focus d’un contrôle bouton.|
|[CButton :: GetTextMargin](#gettextmargin)|Récupère la marge de texte du contrôle bouton.|
|[CButton :: SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher sur le bouton.|
|[CButton :: SetButtonStyle](#setbuttonstyle)|Modifie le style d’un bouton.|
|[CButton :: SetCheck](#setcheck)|Définit l’état d’activation d’un contrôle bouton.|
|[CButton :: SetCursor](#setcursor)|Spécifie une image de curseur à afficher sur le bouton.|
|[CButton :: SetDropDownState](#setdropdownstate)|Définit l’État déroulant du contrôle bouton partagé actuel.|
|[CButton :: SetIcon](#seticon)|Spécifie une icône à afficher sur le bouton.|
|[CButton :: SetImageList](#setimagelist)|Définit la liste d’images du contrôle bouton.|
|[CButton :: SetNote](#setnote)|Définit la note sur le contrôle de lien de commande actuel.|
|[CButton :: SetSplitGlyph](#setsplitglyph)|Associe un glyphe spécifié au contrôle de bouton partagé actuel.|
|[CButton :: SetSplitImageList](#setsplitimagelist)|Associe une liste d’images au contrôle de bouton partagé actuel.|
|[CButton :: SetSplitInfo](#setsplitinfo)|Spécifie des informations qui définissent le contrôle du bouton partagé actuel.|
|[CButton :: SetSplitSize](#setsplitsize)|Définit le rectangle englobant du composant de liste déroulante du contrôle bouton partagé actuel.|
|[CButton :: SetSplitStyle](#setsplitstyle)|Définit le style du contrôle bouton partagé actuel.|
|[CButton :: SetState](#setstate)|Définit l’état de mise en surbrillance d’un contrôle bouton.|
|[CButton :: SetTextMargin](#settextmargin)|Définit la marge de texte du contrôle bouton.|

## <a name="remarks"></a>Notes

Un contrôle Button est une petite fenêtre enfant rectangulaire qui peut être activée ou désactivée. Les boutons peuvent être utilisés seuls ou dans des groupes et peuvent être étiquetés ou affichés sans texte. Un bouton change généralement d’apparence lorsque l’utilisateur clique dessus.

Les boutons standard sont la case à cocher, la case d’option et le bouton de contrôle. Un `CButton` objet peut devenir l’un de ces objets, en fonction du [style de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles) spécifié lors de son initialisation par la fonction membre [Create](#create) .

En outre, la classe [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) dérivée de `CButton` prend en charge la création de contrôles Button étiquetés avec des images bitmap au lieu de texte. Un `CBitmapButton` peut avoir des bitmaps séparées pour les États haut, vers le haut, focus et désactivé d’un bouton.

Vous pouvez créer un contrôle Button à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, appelez d’abord le constructeur `CButton` pour construire l' `CButton` objet, puis appelez la `Create` fonction membre pour créer le contrôle bouton Windows et l’attacher à l' `CButton` objet.

La construction peut être un processus en une étape dans une classe dérivée de `CButton` . Écrivez un constructeur pour la classe dérivée et appelez `Create` à partir du constructeur.

Si vous voulez gérer les messages de notification Windows envoyés par un contrôle bouton à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajoutez une entrée de table des messages et une fonction membre du gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de la table des messages prend la forme suivante :

**Sur \_ ** _Notification_ **(** _ID_, _memberFxn_ **)**

où *ID* spécifie l’ID de fenêtre enfant du contrôle qui envoie la notification et *memberFxn* est le nom de la fonction membre parente que vous avez écrite pour gérer la notification.

Le prototype de fonction du parent est le suivant :

`afx_msg void memberFxn();`

Les entrées de table des messages potentielles sont les suivantes :

|Entrée de mappage|Envoyé au parent quand...|
|---------------|----------------------------|
|ON_BN_CLICKED|L’utilisateur clique sur un bouton.|
|ON_BN_DOUBLECLICKED|L’utilisateur double-clique sur un bouton.|

Si vous créez un `CButton` objet à partir d’une ressource de boîte de dialogue, l' `CButton` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CButton` objet dans une fenêtre, vous devrez peut-être le détruire. Si vous créez l' `CButton` objet sur le tas à l’aide de la **`new`** fonction, vous devez appeler **`delete`** sur l’objet pour le détruire lorsque l’utilisateur ferme le contrôle bouton Windows. Si vous créez l' `CButton` objet sur la pile, ou qu’il est incorporé dans l’objet de boîte de dialogue parent, il est détruit automatiquement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton :: CButton

Construit un objet `CButton`.

```
CButton();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton :: Create

Crée le contrôle bouton Windows et l’attache à l' `CButton` objet.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszCaption*<br/>
Spécifie le texte du contrôle bouton.

*dwStyle*<br/>
Spécifie le style du contrôle bouton. Appliquez n’importe quelle combinaison de [styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles) au bouton.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle bouton. Il peut s’agir d’un `CRect` objet ou d’une `RECT` structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle Button, généralement `CDialog` . Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CButton` objet en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create` , qui crée le contrôle bouton Windows et l’attache à l' `CButton` objet.

Si le style de WS_VISIBLE est donné, Windows envoie le contrôle Button à tous les messages requis pour activer et afficher le bouton.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle Button :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_GROUP des contrôles de groupe

- WS_TABSTOP d’inclure le bouton dans l’ordre de tabulation

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton ::D rawItem

Appelé par le Framework quand un aspect visuel d’un bouton owner-drawn a changé.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur long vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Le style de BS_OWNERDRAW est défini pour un bouton owner-drawn. Substituez cette fonction membre pour implémenter le dessin pour un objet owner-drawn `CButton` . L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant que la fonction membre ne se termine.

Consultez également les valeurs de style de [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton :: GetBitmap

Appelez cette fonction membre pour obtenir le handle d’une image bitmap, précédemment définie avec [SetBitmap](#setbitmap), qui est associée à un bouton.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Handle d’une bitmap. NULL si aucune bitmap n’est précédemment spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton :: GetButtonStyle

Récupère des informations sur le style du contrôle bouton.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne les styles de bouton pour cet `CButton` objet. Cette fonction retourne uniquement les valeurs de style [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) , pas les autres styles de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton :: GetCheck

Récupère l’état d’activation d’une case d’option ou d’une case à cocher.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour d’un contrôle bouton créé avec le style BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON ou BS_3STATE est l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|BST_UNCHECKED|L’état du bouton est désactivé.|
|BST_CHECKED|L’état du bouton est activé.|
|BST_INDETERMINATE|L’état du bouton est indéterminé (s’applique uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE).|

Si le bouton a un autre style, la valeur de retour est BST_UNCHECKED.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton :: GetCursor

Appelez cette fonction membre pour obtenir le handle d’un curseur, précédemment défini avec [SetCursor](#setcursor), associé à un bouton.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Handle d’une image de curseur. NULL si aucun curseur n’est spécifié précédemment.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton :: GetIcon

Appelez cette fonction membre pour obtenir le handle d’une icône, précédemment définie avec [seticon](#seticon), qui est associée à un bouton.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Handle d'une icône. NULL si aucune icône n’est précédemment spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton :: GetIdealSize

Récupère la taille idéale pour le contrôle bouton.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Paramètres

*psize*<br/>
Pointeur vers la taille actuelle du bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la BCM_GETIDEALSIZE message, comme décrit dans la section [boutons](/windows/win32/controls/buttons) de l’SDK Windows.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton :: GetImageList

Appelez cette méthode pour récupérer la liste d’images à partir du contrôle bouton.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Pointeur vers la liste d’images de l' `CButton` objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la BCM_GETIMAGELIST message, comme décrit dans la section [boutons](/windows/win32/controls/buttons) de l’SDK Windows.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton :: GetNote

Récupère le texte de note associé au contrôle de lien de commande actuel.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|à Pointeur vers une mémoire tampon, que l’appelant est chargé d’allouer et de libérer. Si la valeur de retour est TRUE, la mémoire tampon contient le texte de note associé au contrôle de lien de commande actuel ; dans le cas contraire, la mémoire tampon est inchangée.|
|*cchNote*|[in, out] Pointeur vers une variable de type entier non signé.<br /><br /> Lorsque cette méthode est appelée, la variable contient la taille de la mémoire tampon spécifiée par le paramètre *lpszNote* .<br /><br /> Lorsque cette méthode est retournée, si la valeur de retour est TRUE, la variable contient la taille de la note associée au contrôle de lien de commande actuel. Si la valeur de retour est FALSe, la variable contient la taille de mémoire tampon requise pour contenir la note.|

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, objet [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de note associé au contrôle de lien de commande actuel.

-ou-

Dans la deuxième surcharge, TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le message [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) , qui est décrit dans le SDK Windows.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton :: GetNoteLength

Récupère la longueur du texte de la note pour le contrôle de lien de commande actuel.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du texte de la note, en caractères Unicode 16 bits, pour le contrôle de lien de commande actuel.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le message [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) , qui est décrit dans le SDK Windows.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton :: GetSplitGlyph

Récupère le glyphe associé au contrôle de bouton partagé actuel.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valeur de retour

Caractère de glyphe associé au contrôle de bouton partagé actuel.

### <a name="remarks"></a>Notes

Un glyphe est la représentation physique d’un caractère dans une police particulière. Par exemple, un contrôle de bouton partagé peut être décoré avec le glyphe du caractère de coche Unicode (U + 2713).

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_GLYPH, puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows. Lorsque la fonction de message retourne, cette méthode récupère le glyphe à partir du `himlGlyph` membre de la structure.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton :: GetSplitImageList

Récupère la [liste d’images](../../mfc/reference/cimagelist-class.md) pour le contrôle bouton partagé actuel.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_IMAGE, puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows. Lorsque la fonction de message retourne, cette méthode récupère la liste d’images à partir du `himlGlyph` membre de la structure.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton :: GetSplitInfo

Récupère les paramètres qui déterminent la façon dont Windows dessine le contrôle bouton partagé actuel.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo*|à Pointeur vers une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) qui reçoit des informations sur le contrôle bouton partagé actuel. L’appelant est chargé d’allouer la structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le message [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , qui est décrit dans le SDK Windows.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton :: GetSplitSize

Récupère le rectangle englobant du composant de liste déroulante du contrôle bouton partagé actuel.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSize*|à Pointeur vers une structure de [taille](/windows/win32/api/windef/ns-windef-size) qui reçoit la description d’un rectangle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Quand le contrôle de bouton partagé est développé, il peut afficher un composant déroulant, tel qu’un contrôle de liste ou un contrôle de pagineur. Cette méthode récupère le rectangle englobant qui contient le composant de liste déroulante.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_SIZE, puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows. Lorsque la fonction de message retourne, cette méthode récupère le rectangle englobant du `size` membre de la structure.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton :: GetSplitStyle

Récupère les styles de bouton partagé qui définissent le contrôle bouton partagé actuel.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Combinaison d’opérations de bits de styles de bouton partagé. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles du bouton partagé spécifient l’alignement, le proportions et le format graphique avec lequel Windows dessine une icône de bouton partagé.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_STYLE, puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows. Lorsque la fonction de message retourne, cette méthode récupère les styles de bouton partagé à partir du `uSplitStyle` membre de la structure.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton :: GetState

Récupère l’état d’un contrôle bouton.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valeur de retour

Champ de bits qui contient la combinaison de valeurs qui indiquent l’état actuel d’un contrôle bouton. Le tableau suivant répertorie les valeurs possibles.

|État du bouton|Value|Description|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|État initial.|
|BST_CHECKED|0x0001|Le contrôle bouton est activé.|
|BST_INDETERMINATE|0x0002|L’État est indéterminé (uniquement possible lorsque le contrôle Button a trois États).|
|BST_PUSHED|0x0004|Le contrôle bouton est enfoncé.|
|BST_FOCUS|0x0008|Le contrôle bouton a le focus.|

### <a name="remarks"></a>Notes

Un contrôle bouton avec le style de bouton BS_3STATE ou BS_AUTO3STATE crée une case à cocher dont l’État est défini sur indéterminé. L’état indéterminé indique que la case à cocher n’est ni activée ni désactivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton :: GetTextMargin

Appelez cette méthode pour récupérer la marge de texte de l' `CButton` objet.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin*<br/>
Pointeur vers la marge de texte de l' `CButton` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la marge de texte.

### <a name="remarks"></a>Notes

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la BCM_GETTEXTMARGIN message, comme décrit dans la section [boutons](/windows/win32/controls/buttons) de l’SDK Windows.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton :: SetBitmap

Appelez cette fonction membre pour associer une nouvelle image bitmap au bouton.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Handle d’une bitmap.

### <a name="return-value"></a>Valeur de retour

Handle d’une bitmap précédemment associée au bouton.

### <a name="remarks"></a>Notes

Le bitmap est automatiquement placé sur la face du bouton, centré par défaut. Si la bitmap est trop grande pour le bouton, elle est découpée de part et d’autre. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par bouton, `SetBitmap` n’utilise qu’une seule bitmap par bouton. Lorsque le bouton est enfoncé, le bitmap semble décaler vers le dessous et vers la droite.

Vous êtes chargé de libérer l’image bitmap lorsque vous en avez terminé avec celle-ci.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton :: SetButtonStyle

Modifie le style d’un bouton.

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Spécifie le [style du bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Spécifie si le bouton doit être redessiné. Une valeur différente de zéro redessine le bouton. Une valeur 0 ne redessine pas le bouton. Le bouton est redessiné par défaut.

### <a name="remarks"></a>Notes

Utilisez la `GetButtonStyle` fonction membre pour récupérer le style de bouton. Le mot de poids faible du style de bouton complet est le style spécifique au bouton.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton :: SetCheck

Définit ou réinitialise l’état d’activation d’une case d’option ou d’une case à cocher.

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nConsultez*<br/>
Spécifie l’état d’activation. Ce paramètre peut avoir l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|BST_UNCHECKED|Affectez la valeur non cochée à l’état du bouton.|
|BST_CHECKED|Définissez l’état du bouton sur activé.|
|BST_INDETERMINATE|Affectez à l’état du bouton la valeur Indeterminate. Cette valeur peut être utilisée uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE.|

### <a name="remarks"></a>Notes

Cette fonction membre n’a aucun effet sur un PushButton.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton :: SetCursor

Appelez cette fonction membre pour associer un nouveau curseur au bouton.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
Handle d’un curseur.

### <a name="return-value"></a>Valeur de retour

Handle d’un curseur précédemment associé au bouton.

### <a name="remarks"></a>Notes

Le curseur est automatiquement placé sur la face du bouton, centré par défaut. Si le curseur est trop grand pour le bouton, il est coupé de chaque côté. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par bouton, `SetCursor` n’utilise qu’un seul curseur par bouton. Lorsque le bouton est enfoncé, le curseur apparaît pour décaler vers le dessous et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton :: SetDropDownState

Définit l’État déroulant du contrôle bouton partagé actuel.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fDropDown*|dans TRUE pour définir BST_DROPDOWNPUSHED État ; Sinon, FALSe.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Un contrôle de bouton partagé a un style BS_SPLITBUTTON ou BS_DEFSPLITBUTTON et se compose d’un bouton et d’une flèche de déroulement vers la droite. Pour plus d’informations, consultez [styles de bouton](/windows/win32/Controls/button-styles). En règle générale, l’État déroulant est défini lorsque l’utilisateur clique sur la flèche déroulante. Utilisez cette méthode pour définir par programmation l’état de liste déroulante du contrôle. La flèche de déroulement est dessinée en grisé pour indiquer l’État.

Cette méthode envoie le message [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_splitButton*, qui est utilisée pour accéder par programmation au contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit l’état du contrôle bouton partagé pour indiquer que la flèche déroulante fait l’objet d’un push.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton :: SetElevationRequired

Affecte à l’état du contrôle bouton actuel la valeur `elevation required` , ce qui est nécessaire pour que le contrôle affiche une icône de sécurité élevée.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fElevationRequired*|dans TRUE pour définir l' `elevation required` État ; sinon, false.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si un contrôle de lien de commande ou de bouton requiert une autorisation de sécurité élevée pour effectuer une action, définissez le contrôle sur `elevation required` État. Par la suite, Windows affiche l’icône de bouclier du contrôle de compte d’utilisateur (UAC) sur le contrôle. Pour plus d’informations, consultez [Contrôle de compte d’utilisateur](/windows/win32/uxguide/winenv-uac).

Cette méthode envoie le message [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) , qui est décrit dans le SDK Windows.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton :: SetIcon

Appelez cette fonction membre pour associer une nouvelle icône au bouton.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
Handle d’une icône.

### <a name="return-value"></a>Valeur de retour

Handle d’une icône précédemment associée au bouton.

### <a name="remarks"></a>Notes

L’icône est automatiquement placée sur la face du bouton, centrée par défaut. Si l’icône est trop grande pour le bouton, elle est découpée de part et d’autre. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par bouton, `SetIcon` n’utilise qu’une seule icône par bouton. Lorsque le bouton est enfoncé, l’icône s’affiche pour décaler vers le dessous et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton :: SetImageList

Appelez cette méthode pour définir la liste d’images de l' `CButton` objet.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Pointeur vers la nouvelle liste d’images.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la BCM_SETIMAGELIST message, comme décrit dans la section [boutons](/windows/win32/controls/buttons) de l’SDK Windows.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton :: SetNote

Définit le texte de la note pour le contrôle de lien de commande actuel.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|dans Pointeur vers une chaîne Unicode qui est définie comme texte de note pour le contrôle de lien de commande.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le message [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_cmdLink*, qui est utilisée pour accéder par programmation au contrôle de lien de commande. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le texte de la note pour le contrôle de lien de commande.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton :: SetSplitGlyph

Associe un glyphe spécifié au contrôle de bouton partagé actuel.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*chGlyph*|dans Caractère qui spécifie le glyphe à utiliser comme flèche de déroulement du bouton partagé.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles qui ont le style de bouton BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Un glyphe est la représentation physique d’un caractère dans une police particulière. Le paramètre *chGlyph* n’est pas utilisé comme glyphe, mais il est utilisé pour sélectionner un glyphe à partir d’un ensemble de glyphes définis par le système. Le glyphe de la flèche déroulante par défaut est spécifié par un caractère « 6 » et ressemble au TRIANGLE noir POINTant vers le bas en caractères Unicode (U + 25BC).

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_GLYPH et le `himlGlyph` membre avec le paramètre *chGlyph* , puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton :: SetSplitImageList

Associe une [liste d’images](../../mfc/reference/cimagelist-class.md) au contrôle de bouton partagé actuel.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSplitImageList*|dans Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) à assigner au contrôle bouton partagé actuel.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_IMAGE et le `himlGlyph` membre avec le paramètre *pSplitImageList* , puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton :: SetSplitInfo

Spécifie les paramètres qui déterminent la façon dont Windows dessine le contrôle bouton partagé actuel.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo*|dans Pointeur vers une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) qui définit le contrôle bouton partagé actuel.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le message [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton` , qui est utilisée pour accéder par programmation au contrôle bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie le glyphe utilisé pour la flèche de déroulement du bouton partagé. L’exemple substitue un glyphe de triangle pointant vers le haut pour le glyphe de triangle pointant vers le haut par défaut. Le glyphe affiché dépend du caractère que vous spécifiez dans le `himlGlyph` membre de la `BUTTON_SPLITINFO` structure. Le glyphe de triangle pointant vers le haut est spécifié par un caractère « 6 » et le glyphe de triangle pointant vers le haut est spécifié par un caractère « 5 ». Pour comparaison, consultez la méthode pratique, [CButton :: SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton :: SetSplitSize

Définit le rectangle englobant du composant de liste déroulante du contrôle bouton partagé actuel.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSize*|dans Pointeur vers une structure de [taille](/windows/win32/api/windef/ns-windef-size) qui décrit un rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Quand le contrôle de bouton partagé est développé, il peut afficher un composant déroulant, tel qu’un contrôle de liste ou un contrôle de pagineur. Cette méthode spécifie la taille du rectangle englobant qui contient le composant de liste déroulante.

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_SIZE et le `size` membre avec le paramètre *psize* , puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton` , qui est utilisée pour accéder par programmation au contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant double la taille de la flèche de déroulement du bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton :: SetSplitStyle

Définit le style du contrôle bouton partagé actuel.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*uSplitStyle*|dans Combinaison d’opérations de bits de styles de bouton partagé. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles du bouton partagé spécifient l’alignement, le proportions et le format graphique avec lequel Windows dessine une icône de bouton partagé. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

Cette méthode initialise le `mask` membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec l’indicateur BCSIF_STYLE et le `uSplitStyle` membre avec le paramètre *uSplitStyle* , puis envoie cette structure dans le [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) message décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton` , qui est utilisée pour accéder par programmation au contrôle bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le style de la flèche déroulante du bouton partagé. Le style de BCSS_ALIGNLEFT affiche la flèche sur le côté gauche du bouton et le style de BCSS_STRETCH conserve les proportions de la flèche déroulante lorsque vous redimensionnez le bouton.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton :: SetState

Définit si un contrôle bouton est mis en surbrillance ou non.

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight*<br/>
Spécifie si le bouton doit être mis en surbrillance. Une valeur différente de zéro met en surbrillance le bouton. une valeur 0 supprime toute mise en surbrillance.

### <a name="remarks"></a>Notes

La mise en surbrillance affecte l’extérieur d’un contrôle Button. Elle n’a aucun effet sur l’état d’activation d’une case d’option ou d’une case à cocher.

Un contrôle bouton est automatiquement mis en surbrillance lorsque l’utilisateur clique sur le bouton gauche de la souris et le maintient enfoncé. La mise en surbrillance est supprimée lorsque l’utilisateur relâche le bouton de la souris.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton :: SetTextMargin

Appelez cette méthode pour définir la marge de texte de l' `CButton` objet.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin*<br/>
Pointeur vers la nouvelle marge de texte.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la BCM_SETTEXTMARGIN message, comme décrit dans la section [boutons](/windows/win32/controls/buttons) de l’SDK Windows.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox (classe)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton, classe](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog (classe)](../../mfc/reference/cdialog-class.md)
