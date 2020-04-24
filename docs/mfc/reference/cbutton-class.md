---
title: Classe CButton
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
ms.openlocfilehash: 74b07dc8144e853714ea73c8235f1259538a0c12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752755"
---
# <a name="cbutton-class"></a>Classe CButton

Fournit les fonctionnalités des contrôles bouton Windows.

## <a name="syntax"></a>Syntaxe

```
class CButton : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Construit un objet `CButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CButton::Créer](#create)|Crée le contrôle du bouton Windows `CButton` et le fixe à l’objet.|
|[CButton::DrawItem](#drawitem)|Remplacer pour dessiner un `CButton` objet dessiné par le propriétaire.|
|[CButton::GetBitmap](#getbitmap)|Récupère la poignée de la bitmap précédemment réglée avec [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Récupère des informations sur le style de contrôle des boutons.|
|[CButton::GetCheck](#getcheck)|Récupère l’état de contrôle d’un contrôle de bouton.|
|[CButton::GetCursor](#getcursor)|Récupère la poignée de l’image curseur précédemment réglée avec [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Récupère la poignée de l’icône précédemment définie avec [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Récupère la taille idéale du contrôle du bouton.|
|[CButton::GetImageList](#getimagelist)|Récupère la liste d’images du contrôle du bouton.|
|[CButton::GetNote](#getnote)|Récupère le composant de note du contrôle actuel du lien de commande.|
|[CButton::GetNoteLength](#getnotelength)|Récupère la longueur du texte de note pour le contrôle actuel du lien de commande.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Récupère le glyphe associé au contrôle actuel du bouton fractionné.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Récupère la liste d’images pour le contrôle actuel du bouton fractionné.|
|[CButton::GetSplitInfo](#getsplitinfo)|Récupère les informations qui définissent le contrôle actuel du bouton fractionné.|
|[CButton::GetSplitSize](#getsplitsize)|Récupère le rectangle de délimitation du composant de chute du contrôle actuel du bouton fractionné.|
|[CButton::GetSplitStyle](#getsplitstyle)|Récupère les styles de boutons fendus qui définissent le contrôle actuel du bouton fendu.|
|[CButton::GetState](#getstate)|Récupère l’état de contrôle, met en évidence l’état, et l’état de mise au point d’un contrôle de bouton.|
|[CButton::GetTextMargin](#gettextmargin)|Récupère la marge de texte du contrôle du bouton.|
|[CButton::SetBitmap](#setbitmap)|Spécifie un bitmap à afficher sur le bouton.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Change le style d’un bouton.|
|[CButton::SetCheck](#setcheck)|Définit l’état de contrôle d’un contrôle de bouton.|
|[CButton::SetCursor](#setcursor)|Spécifie une image de curseur à afficher sur le bouton.|
|[CButton::SetDropDownState](#setdropdownstate)|Définit l’état de chute du contrôle actuel du bouton fractionné.|
|[CButton::SetIcon](#seticon)|Spécifie une icône à afficher sur le bouton.|
|[CButton::SetImageList](#setimagelist)|Définit la liste d’images du contrôle du bouton.|
|[CButton::SetNote](#setnote)|Définit la note sur le contrôle actuel du lien de commande.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Associe un glyphe spécifié au contrôle actuel du bouton fractionné.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Associe une liste d’images au contrôle actuel du bouton fractionné.|
|[CButton::SetSplitInfo](#setsplitinfo)|Spécifie les informations qui définissent le contrôle actuel du bouton fractionné.|
|[CButton::SetSplitSize](#setsplitsize)|Définit le rectangle de délimitation du composant de chute du contrôle actuel du bouton fractionné.|
|[CButton::SetSplitStyle](#setsplitstyle)|Définit le style du contrôle actuel du bouton fendu.|
|[CButton::SetState](#setstate)|Définit l’état de mise en évidence d’un contrôle de bouton.|
|[CButton::SetTextMargin](#settextmargin)|Définit la marge de texte du contrôle du bouton.|

## <a name="remarks"></a>Notes

Un bouton de contrôle est une petite fenêtre d’enfant rectangulaire qui peut être cliqué sur et en dehors. Les boutons peuvent être utilisés seuls ou en groupe et peuvent être étiquetés ou apparaître sans texte. Un bouton change généralement d’apparence lorsque l’utilisateur clique dessus.

Les boutons typiques sont la case à cocher, le bouton radio et le bouton de pression. Un `CButton` objet peut devenir l’un de ces, selon le [style de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles) spécifié lors de son initialisation par la fonction membre [Create.](#create)

En outre, la classe [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) dérivée de la création de `CButton` supports de contrôles de bouton étiquetés avec des images de bitmap au lieu du texte. A `CBitmapButton` peut avoir des bitmaps séparés pour un bouton est haut, vers le bas, concentré, et les états handicapés.

Vous pouvez créer un bouton de contrôle à partir d’un modèle de dialogue ou directement dans votre code. Dans les deux cas, `CButton` appelez d’abord le constructeur pour construire l’objet; `CButton` ensuite appelez `Create` la fonction membre pour créer le `CButton` contrôle du bouton Windows et l’attacher à l’objet.

La construction peut être un processus en `CButton`une seule étape dans une classe dérivée de . Écrivez un constructeur pour la `Create` classe dérivée et appelez à l’intérieur du constructeur.

Si vous souhaitez traiter les messages de notification Windows envoyés par un bouton de contrôle à son parent (généralement une classe dérivée de [CDialog),](../../mfc/reference/cdialog-class.md)ajoutez une entrée de carte de message et une fonction de membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de carte de message prend la forme suivante :

**ON\_**_Notification_ **(** _id_, _memberFxn_ **)**

lorsque *l’id* spécifie l’ID fenêtre de l’enfant du contrôle envoyant la notification et *membreFxn* est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.

Le prototype de fonction du parent est le suivant :

`afx_msg void memberFxn();`

Les entrées potentielles de carte de message sont les suivantes :

|Entrée de la carte|Envoyé au parent quand...|
|---------------|----------------------------|
|ON_BN_CLICKED|L’utilisateur clique sur un bouton.|
|ON_BN_DOUBLECLICKED|L’utilisateur double-clics d’un bouton.|

Si vous `CButton` créez un objet à `CButton` partir d’une ressource de dialogue, l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CButton` créez un objet à l’intérieur d’une fenêtre, vous devrez peut-être le détruire. Si vous `CButton` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque l’utilisateur ferme le contrôle du bouton Windows. Si vous `CButton` créez l’objet sur la pile, ou s’il est intégré dans l’objet de dialogue parent, il est détruit automatiquement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton::CButton

Construit un objet `CButton`.

```
CButton();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton::Créer

Crée le contrôle du bouton Windows `CButton` et le fixe à l’objet.

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
Spécifie le texte du contrôle du bouton.

*dwStyle (en)*<br/>
Spécifie le style du contrôle du bouton. Appliquez n’importe quelle combinaison de styles de [bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles) sur le bouton.

*Rect*<br/>
Spécifie la taille et la position du contrôle du bouton. Il peut s’agir `CRect` `RECT` d’un objet ou d’une structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`du contrôle du bouton, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle du bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CButton` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CButton` qui crée le contrôle du bouton Windows et le fixe à l’objet.

Si le style WS_VISIBLE est donné, Windows envoie le bouton de contrôle tous les messages nécessaires pour activer et afficher le bouton.

Appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de bouton :

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_GROUP Pour les contrôles de groupe

- WS_TABSTOP Inclure le bouton dans l’ordre de tabbing

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::DrawItem

Appelé par le cadre quand un aspect visuel d’un bouton tiré par le propriétaire a changé.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un long pointeur vers une structure [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Un bouton dessiné par le propriétaire a l’ensemble de style BS_OWNERDRAW. Remplacer cette fonction de membre pour implémenter le dessin d’un objet dessiné par le `CButton` propriétaire. L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de la fonction membre.

Voir aussi les valeurs de style [BS_.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton::GetBitmap

Appelez cette fonction de membre pour obtenir la poignée d’un bitmap, précédemment réglé avec [SetBitmap](#setbitmap), qui est associé à un bouton.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée à un bitmap. NULL si aucun bitmap n’est préalablement spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton::GetButtonStyle

Récupère des informations sur le style de contrôle des boutons.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne les styles `CButton` de bouton pour cet objet. Cette fonction ne renvoie que les valeurs de style [BS_,](../../mfc/reference/styles-used-by-mfc.md#button-styles) pas l’un des autres styles de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton::GetCheck

Récupère l’état de cocher d’un bouton radio ou d’une case à cocher.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour d’un bouton de contrôle créé avec le BS_AUTOCHECKBOX, la BS_AUTORADIOBUTTON, la BS_AUTO3STATE, la BS_CHECKBOX, la BS_RADIOBUTTON ou le style BS_3STATE est l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|BST_UNCHECKED|L’état de bouton n’est pas contrôlé.|
|BST_CHECKED|L’état du bouton est vérifié.|
|BST_INDETERMINATE|L’état du bouton est indéterminé (s’applique uniquement si le bouton a le BS_3STATE ou BS_AUTO3STATE style).|

Si le bouton a un autre style, la valeur de retour est BST_UNCHECKED.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton::GetCursor

Appelez cette fonction de membre pour obtenir la poignée d’un curseur, précédemment réglé avec [SetCursor](#setcursor), qui est associé à un bouton.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Une poignée à une image de curseur. NULL si aucun curseur n’est préalablement spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton::GetIcon

Appelez cette fonction de membre pour obtenir la poignée d’une icône, précédemment définie avec [SetIcon](#seticon), qui est associée à un bouton.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Handle d'une icône. NULL si aucune icône n’est préalablement spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton::GetIdealSize

Récupère la taille idéale pour le contrôle du bouton.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Paramètres

*Psize*<br/>
Un pointeur sur la taille actuelle du bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message BCM_GETIDEALSIZE, tel que décrit dans la section [Boutons](/windows/win32/controls/buttons) du SDK Windows.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton::GetImageList

Appelez cette méthode pour obtenir la liste d’images à partir du contrôle du bouton.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Un pointeur sur la `CButton` liste d’images de l’objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message BCM_GETIMAGELIST, tel que décrit dans la section [Boutons](/windows/win32/controls/buttons) du SDK Windows.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton::GetNote

Récupère le texte de note associé au contrôle actuel du lien de commande.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|[out] Pointeur vers un tampon, que l’appelant est responsable de l’attribution et de la transaction. Si la valeur de retour est VRAI, le tampon contient le texte de note qui est associé au contrôle actuel du lien de commande; autrement, le tampon est inchangé.|
|*cchNote*|[dans, dehors] Un pointeur à une variable insignable.<br /><br /> Lorsque cette méthode est appelée, la variable contient la taille du tampon spécifié par le paramètre *lpszNote.*<br /><br /> Lorsque cette méthode revient, si la valeur de retour est VRAI, la variable contient la taille de la note associée au contrôle actuel du lien de commande. Si la valeur de retour est FALSE, la variable contient la taille du tampon nécessaire pour contenir la note.|

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, un objet [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de note associé au contrôle actuel du lien de commande.

-ou-

Dans la deuxième surcharge, VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [message BCM_GETNOTE,](/windows/win32/Controls/bcm-getnote) qui est décrit dans le SDK Windows.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton::GetNoteLength

Récupère la longueur du texte de note pour le contrôle actuel du lien de commande.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du texte de la note, en caractères Unicode 16 bits, pour le contrôle actuel du lien de commande.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [message BCM_GETNOTELENGTH,](/windows/win32/Controls/bcm-getnotelength) qui est décrit dans le SDK Windows.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton::GetSplitGlyph

Récupère le glyphe associé au contrôle actuel du bouton fractionné.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valeur de retour

Le caractère glyphe associé au contrôle actuel du bouton fendu.

### <a name="remarks"></a>Notes

Un glyphe est la représentation physique d’un personnage dans une police particulière. Par exemple, un contrôle de bouton fendu peut être décoré avec le glyph du caractère de la marque de contrôle Unicode (U-2713).

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le drapeau BCSIF_GLYPH, puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows. Lorsque la fonction de message revient, cette `himlGlyph` méthode récupère le glyphe du membre de la structure.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton::GetSplitImageList

Récupère la [liste d’images](../../mfc/reference/cimagelist-class.md) pour le contrôle actuel du bouton fractionné.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le drapeau BCSIF_IMAGE, puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows. Lorsque la fonction de message revient, cette `himlGlyph` méthode récupère la liste d’images du membre de la structure.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton::GetSplitInfo

Récupère les paramètres qui déterminent la façon dont Windows tire le contrôle actuel du bouton fractionné.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo (en anglais)*|[out] Pointeur vers une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) qui reçoit des informations sur le contrôle actuel du bouton fractionné. L’appelant est responsable de l’attribution de la structure.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le [message BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton::GetSplitSize

Récupère le rectangle de délimitation du composant de chute du contrôle actuel du bouton fractionné.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Psize*|[out] Pointeur vers une structure [SIZE](/windows/win32/api/windef/ns-windef-size) qui reçoit la description d’un rectangle.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Lorsque le contrôle du bouton fractionné est élargi, il peut afficher un composant d’abandon tel qu’un contrôle de liste ou un contrôle de téléavertisseur. Cette méthode récupère le rectangle de délimitation qui contient le composant de dépôt.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le drapeau BCSIF_SIZE, puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows. Lorsque la fonction de message revient, cette `size` méthode récupère le rectangle de délimitation du membre de la structure.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton::GetSplitStyle

Récupère les styles de boutons fendus qui définissent le contrôle actuel du bouton fendu.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Une combinaison peu sage de styles de boutons fendus. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles de boutons partagés spécifient l’alignement, le rapport d’aspect et le format graphique avec lequel Windows dessine une icône de bouton fendu.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le drapeau BCSIF_STYLE, puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows. Lorsque la fonction de message revient, cette `uSplitStyle` méthode récupère les styles de bouton fractionné du membre de la structure.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton::GetState

Récupère l’état d’un contrôle de bouton.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valeur de retour

Un champ bit qui contient la combinaison de valeurs qui indiquent l’état actuel d’un contrôle de bouton. Le tableau suivant énumère les valeurs possibles.

|État de bouton|Valeur|Description|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|L’état initial.|
|BST_CHECKED|0x0001|Le contrôle du bouton est vérifié.|
|BST_INDETERMINATE|0x0002|L’état est indéterminé (seulement possible lorsque le contrôle du bouton a trois états).|
|BST_PUSHED|0x0004|Le contrôle du bouton est appuyé.|
|BST_FOCUS|0x0008|Le contrôle du bouton a la mise au point.|

### <a name="remarks"></a>Notes

Un contrôle de bouton avec le style BS_3STATE ou BS_AUTO3STATE bouton crée une case à cocher qui a un troisième état qui est nommé l’état d’une durée indéterminée. L’état d’une durée indéterminée indique que la case à cocher n’est ni cochée ni non contrôlée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton::GetTextMargin

Appelez cette méthode pour obtenir `CButton` la marge de texte de l’objet.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin pmargin*<br/>
Un pointeur sur la `CButton` marge de texte de l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la marge de texte.

### <a name="remarks"></a>Notes

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message BCM_GETTEXTMARGIN, tel que décrit dans la section [Boutons](/windows/win32/controls/buttons) du SDK Windows.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton::SetBitmap

Appelez cette fonction de membre pour associer une nouvelle bitmap avec le bouton.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap (en)*<br/>
Le manche d’un bitmap.

### <a name="return-value"></a>Valeur de retour

La poignée d’un bitmap précédemment associé au bouton.

### <a name="remarks"></a>Notes

Le bitmap sera automatiquement placé sur la face du bouton, centré par défaut. Si la bitmap est trop grande pour le bouton, elle sera coupée de chaque côté. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise `SetBitmap` quatre bitmaps par bouton, utilise seulement un bitmap par bouton. Lorsque le bouton est appuyé, le bitmap semble se déplacer vers le bas et vers la droite.

Vous êtes responsable de la libération de la bitmap quand vous en avez fini avec elle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton::SetButtonStyle

Change le style d’un bouton.

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Spécifie le [style bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw (en)*<br/>
Précise si le bouton doit être redessiné. Une valeur non zéro redessiner le bouton. Une valeur 0 ne redessinera pas le bouton. Le bouton est redessiné par défaut.

### <a name="remarks"></a>Notes

Utilisez `GetButtonStyle` la fonction membre pour récupérer le style bouton. Le mot de faible ordre du style bouton complet est le style bouton-spécifique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton::SetCheck

Définit ou réinitialise l’état de cocher d’un bouton radio ou d’une case à cocher.

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nCheck (en)*<br/>
Spécifie l’état de contrôle. Ce paramètre peut avoir l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|BST_UNCHECKED|Réglez l’état du bouton à décoché.|
|BST_CHECKED|Réglez l’état du bouton pour vérifier.|
|BST_INDETERMINATE|Réglez l’état du bouton pour une durée indéterminée. Cette valeur ne peut être utilisée que si le bouton a le BS_3STATE ou BS_AUTO3STATE style.|

### <a name="remarks"></a>Notes

Cette fonction de membre n’a aucun effet sur un pushbutton.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::SetCursor

Appelez cette fonction de membre pour associer un nouveau curseur avec le bouton.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
La poignée d’un curseur.

### <a name="return-value"></a>Valeur de retour

La poignée d’un curseur précédemment associée au bouton.

### <a name="remarks"></a>Notes

Le curseur sera automatiquement placé sur la face du bouton, centré par défaut. Si le curseur est trop grand pour le bouton, il sera coupé de chaque côté. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise `SetCursor` quatre bitmaps par bouton, utilise un seul curseur par bouton. Lorsque le bouton est appuyé, le curseur semble se déplacer vers le bas et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton::SetDropDownState

Définit l’état de chute du contrôle actuel du bouton fractionné.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fDropDown*|[dans] VRAI pour fixer BST_DROPDOWNPUSHED état; autrement, FALSE.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Un contrôle de bouton fendu a un style de BS_SPLITBUTTON ou BS_DEFSPLITBUTTON et se compose d’un bouton et d’une flèche de chute vers le bas à sa droite. Pour plus d’informations, voir [Button Styles](/windows/win32/Controls/button-styles). Habituellement, l’état de décrochage est défini lorsque l’utilisateur clique sur la flèche de chute. Utilisez cette méthode pour définir de façon programmatique l’état d’abandon du contrôle. La flèche de chute est dessinée à l’ombre pour indiquer l’état.

Cette méthode envoie le [message BCM_SETDROPDOWNSTATE,](/windows/win32/Controls/bcm-setdropdownstate) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_splitButton*, qui est utilisée pour accéder programmatiquement au contrôle du bouton fractionné. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit l’état du contrôle du bouton fractionné pour indiquer que la flèche de chute est poussée.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton::SetElevationRequired

Définit l’état du contrôle `elevation required`du bouton actuel à , ce qui est nécessaire pour le contrôle d’afficher une icône de sécurité élevée.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fElevationRequired*|[dans] VRAI pour `elevation required` définir l’état; autrement, FALSE.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Si un bouton ou un contrôle de lien de commande `elevation required` nécessite une autorisation de sécurité élevée pour effectuer une action, définissez le contrôle à l’état. Par la suite, Windows affiche l’icône de bouclier de contrôle de compte utilisateur (UAC) sur le contrôle. Pour plus d’informations, voir "User Account Control" chez [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Cette méthode envoie le [message BCM_SETSHIELD,](/windows/win32/Controls/bcm-setshield) qui est décrit dans le SDK Windows.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton::SetIcon

Appelez cette fonction de membre pour associer une nouvelle icône avec le bouton.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
Le manche d’une icône.

### <a name="return-value"></a>Valeur de retour

La poignée d’une icône précédemment associée au bouton.

### <a name="remarks"></a>Notes

L’icône sera automatiquement placée sur la face du bouton, centrée par défaut. Si l’icône est trop grande pour le bouton, elle sera coupée de chaque côté. Vous pouvez choisir d’autres options d’alignement, y compris les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement à [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise `SetIcon` quatre bitmaps par bouton, utilise une seule icône par bouton. Lorsque le bouton est appuyé, l’icône semble se déplacer vers le bas et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton::SetImageList

Appelez cette méthode pour définir `CButton` la liste d’images de l’objet.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Un pointeur vers la nouvelle liste d’images.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message BCM_SETIMAGELIST, tel que décrit dans la section [Boutons](/windows/win32/controls/buttons) du SDK Windows.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton::SetNote

Définit le texte de note pour le contrôle actuel du lien de commande.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|[dans] Pointeur vers une chaîne Unicode qui est définie comme texte de note pour le contrôle du lien de commande.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [message BCM_SETNOTE,](/windows/win32/Controls/bcm-setnote) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_cmdLink*, qui est utilisée pour accéder programmatiquement au contrôle du lien de commande. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le texte de note pour le contrôle du lien de commande.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton::SetSplitGlyph

Associe un glyphe spécifié au contrôle actuel du bouton fractionné.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*chGlyph*|[dans] Un personnage qui spécifie le glyphe à utiliser comme la flèche de chute du bouton fendu.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes qui ont le style bouton BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Un glyphe est la représentation physique d’un personnage dans une police particulière. Le paramètre *chGlyph* n’est pas utilisé comme le glyphe, mais est plutôt utilisé pour sélectionner un glyphe à partir d’un ensemble de glyphes définis par le système. Le glyph de flèche d’abandon par défaut est spécifié par un personnage '6', et ressemble au personnage d’Unicode BLACK DOWN-POINTING TRIANGLE (U-25BC).

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le `himlGlyph` drapeau BCSIF_GLYPH et le membre avec le paramètre *chGlyph,* puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::SetSplitImageList

Associe une [liste d’images](../../mfc/reference/cimagelist-class.md) au contrôle actuel du bouton fractionné.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSplitImageList*|[dans] Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) à attribuer au contrôle actuel du bouton fractionné.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le `himlGlyph` drapeau BCSIF_IMAGE et le membre avec le paramètre *pSplitImageList,* puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::SetSplitInfo

Specifie les paramètres qui déterminent la façon dont Windows tire le contrôle actuel du bouton fractionné.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo (en anglais)*|[dans] Pointeur vers une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) qui définit le contrôle actuel du bouton fendu.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le [message BCM_SETSPLITINFO,](/windows/win32/Controls/bcm-setsplitinfo) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_splitButton`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du bouton fractionné.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie le glyphe qui est utilisé pour la flèche de chute du bouton fendu. L’exemple remplace un glyphe triangle pointant vers le haut pour le glyphe triangle de pointage vers le bas par défaut. Le glyphe affiché dépend du caractère que `himlGlyph` vous spécifiez dans le membre de la `BUTTON_SPLITINFO` structure. Le glyphe triangle pointant vers le bas est spécifié par un caractère '6' et le glyphe triangle pointant vers le haut est spécifié par un caractère '5'. À titre de comparaison, voir la méthode de commodité, [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton::SetSplitSize

Définit le rectangle de délimitation du composant de chute du contrôle actuel du bouton fractionné.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Psize*|[dans] Pointeur vers une structure [SIZE](/windows/win32/api/windef/ns-windef-size) qui décrit un rectangle de délimitation.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Lorsque le contrôle du bouton fractionné est élargi, il peut afficher un composant d’abandon tel qu’un contrôle de liste ou un contrôle de téléavertisseur. Cette méthode spécifie la taille du rectangle de délimitation qui contient le composant de dépôt.

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le `size` drapeau BCSIF_SIZE et le membre avec le paramètre *pSize,* puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_splitButton`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du bouton fractionné. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant double la taille de la flèche de chute du bouton fendu.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton::SetSplitStyle

Définit le style du contrôle actuel du bouton fendu.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*uSplitStyle (en)*|[dans] Une combinaison peu sage de styles de boutons fendus. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec des commandes dont le style bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles de boutons partagés spécifient l’alignement, le rapport d’aspect et le format graphique avec lequel Windows dessine une icône de bouton fendu. Pour plus d’informations, consultez le `uSplitStyle` membre de la structure [BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

Cette méthode initialise `mask` le membre d’une structure [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) avec le `uSplitStyle` drapeau BCSIF_STYLE et le membre avec le paramètre *uSplitStyle,* puis envoie cette structure dans le [message BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_splitButton`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du bouton fractionné.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le style de la flèche de chute du bouton fendu. Le style BCSS_ALIGNLEFT affiche la flèche sur le côté gauche du bouton, et le style BCSS_STRETCH conserve les proportions de la flèche de chute lorsque vous redimensionnez le bouton.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton::SetState

Définit si un contrôle de bouton est mis en surbrillance ou non.

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight (en)*<br/>
Précise si le bouton doit être mis en surbrillance. Une valeur non zéro met en évidence le bouton; une valeur 0 supprime toute mise en surbrillance.

### <a name="remarks"></a>Notes

La mise en surbrillance affecte l’extérieur d’un bouton de contrôle. Il n’a aucun effet sur l’état de cocher d’un bouton radio ou d’une case à cocher.

Un contrôle de bouton est automatiquement mis en évidence lorsque l’utilisateur clique et tient le bouton de la souris gauche. La mise en surbrillance est supprimée lorsque l’utilisateur relâche le bouton de la souris.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton::SetTextMargin

Appelez cette méthode pour définir `CButton` la marge de texte de l’objet.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin pmargin*<br/>
Un pointeur sur la nouvelle marge de texte.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message BCM_SETTEXTMARGIN, tel que décrit dans la section [Boutons](/windows/win32/controls/buttons) du SDK Windows.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[Classe CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Classe CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
