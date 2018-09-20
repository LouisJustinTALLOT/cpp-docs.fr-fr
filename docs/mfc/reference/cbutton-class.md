---
title: CButton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2f0f0ce6a893406fca73f25e040cbc3dbd29d08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429940"
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
|[CButton::CButton](#cbutton)|Construit un objet `CButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CButton::Create](#create)|Crée le contrôle de bouton Windows et l’attache à la `CButton` objet.|
|[CButton::DrawItem](#drawitem)|Remplacement pour dessiner un owner-drawn `CButton` objet.|
|[CButton::GetBitmap](#getbitmap)|Récupère le handle de l’image bitmap précédemment défini avec [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Récupère des informations sur le style du contrôle bouton.|
|[CButton::GetCheck](#getcheck)|Récupère l’état d’activation d’un contrôle bouton.|
|[CButton::GetCursor](#getcursor)|Récupère le handle de l’image curseur défini précédemment avec [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Récupère le handle de l’icône précédemment défini avec [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Récupère la taille idéale du contrôle bouton.|
|[CButton::GetImageList](#getimagelist)|Récupère la liste d’images du contrôle bouton.|
|[CButton::GetNote](#getnote)|Récupère le composant Remarque du contrôle de lien de commande actuelle.|
|[CButton::GetNoteLength](#getnotelength)|Récupère la longueur du texte de note pour le contrôle de lien de commande actuelle.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Récupère le glyphe associé au contrôle de bouton Fractionner en cours.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Récupère la liste d’images pour le contrôle de bouton partagé actuel.|
|[CButton::GetSplitInfo](#getsplitinfo)|Récupère les informations qui définissent le contrôle de bouton partagé actuel.|
|[CButton::GetSplitSize](#getsplitsize)|Récupère le rectangle englobant du composant de liste déroulante du contrôle de bouton de fractionnement actuel.|
|[CButton::GetSplitStyle](#getsplitstyle)|Récupère les styles de bouton de fractionnement qui définissent le contrôle de bouton partagé actuel.|
|[CButton::GetState](#getstate)|Récupère la vérification de l’état, état de mise en surbrillance et l’état de focus d’un contrôle bouton.|
|[CButton::GetTextMargin](#gettextmargin)|Récupère la marge de texte du contrôle bouton.|
|[CButton::SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher sur le bouton.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Modifie le style d’un bouton.|
|[CButton::SetCheck](#setcheck)|Définit l’état d’activation d’un contrôle bouton.|
|[CButton::SetCursor](#setcursor)|Spécifie une image de curseur doit être affiché sur le bouton.|
|[CButton::SetDropDownState](#setdropdownstate)|Définit l’état de la liste déroulante du contrôle de bouton de fractionnement actuel.|
|[CButton::SetIcon](#seticon)|Spécifie l’icône à afficher sur le bouton.|
|[CButton::SetImageList](#setimagelist)|Définit la liste d’images du contrôle bouton.|
|[CButton::SetNote](#setnote)|Définit la Remarque sur le contrôle de lien de commande actuelle.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Associe un glyphe spécifié avec le contrôle de bouton partagé actuel.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Associe une liste d’images avec le contrôle de bouton partagé actuel.|
|[CButton::SetSplitInfo](#setsplitinfo)|Spécifie les informations qui définissent le contrôle de bouton partagé actuel.|
|[CButton::SetSplitSize](#setsplitsize)|Définit le rectangle englobant du composant de liste déroulante du contrôle de bouton de fractionnement actuel.|
|[CButton::SetSplitStyle](#setsplitstyle)|Définit le style du contrôle de bouton de fractionnement actuel.|
|[CButton::SetState](#setstate)|Définit l’état de mise en surbrillance d’un contrôle bouton.|
|[CButton::SetTextMargin](#settextmargin)|Définit la marge de texte du contrôle bouton.|

## <a name="remarks"></a>Notes

Un contrôle de bouton est une fenêtre enfant petit et rectangulaire qui peut être activée et désactiver. Boutons peuvent être utilisés seul ou en groupes et peuvent soit être étiquetés ou apparaissent sans texte. Un apparence du bouton généralement change lorsque l’utilisateur clique dessus.

Boutons classiques sont le case à cocher, case d’option et le bouton de commande. A `CButton` objet peut devenir un de ces éléments, en fonction de la [bouton style](../../mfc/reference/styles-used-by-mfc.md#button-styles) spécifié lors de son initialisation par le [créer](#create) fonction membre.

En outre, le [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) dérivé de la classe `CButton` prend en charge la création de contrôles bouton étiquetés avec des images bitmap plutôt que du texte. Un `CBitmapButton` peut avoir des bitmaps distinctes pour un bouton du vers le bas, concentré et désactivé des États.

Vous pouvez créer un contrôle de bouton à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, tout d’abord appeler le constructeur `CButton` pour construire le `CButton` de l’objet, puis appelez le `Create` fonction membre pour créer le Windows contrôle de bouton et l’attacher à la `CButton` objet.

Construction peut être un processus en une étape dans une classe dérivée de `CButton`. Écrire un constructeur pour la classe dérivée et appelez `Create` à partir de dans le constructeur.

Si vous souhaitez gérer les messages de notification Windows envoyés par un contrôle de bouton à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajouter une fonction de membre entrée et le Gestionnaire de messages-table des messages à la classe parente pour chaque message.

Chaque entrée de table des messages prend la forme suivante :

**ON_** Notification **(**`id`, `memberFxn` **)**

où `id` Spécifie l’ID de fenêtre enfant du contrôle qui envoie la notification et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer les notifications.

Prototype de fonction du parent est la suivante :

**afx_msg** `void` `memberFxn` **() ;**

Les entrées de table des messages potentielles sont les suivantes :

|Entrée de mappage|Envoyé vers le parent lorsque...|
|---------------|----------------------------|
|ON_BN_CLICKED|L’utilisateur clique sur un bouton.|
|ON_BN_DOUBLECLICKED|L’utilisateur double-clique sur un bouton.|

Si vous créez un `CButton` objet à partir d’une ressource de la boîte de dialogue, le `CButton` automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CButton` de l’objet dans une fenêtre, vous devrez peut-être à détruire. Si vous créez le `CButton` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet à détruire lorsque l’utilisateur ferme le Windows le contrôle de bouton. Si vous créez le `CButton` sur la pile, ou il est incorporé dans l’objet de la boîte de dialogue parent, il est supprimé automatiquement.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cbutton"></a>  CButton::CButton

Construit un objet `CButton`.

```
CButton();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>  CButton::Create

Crée le contrôle de bouton Windows et l’attache à la `CButton` objet.

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
Spécifie le texte du contrôle de bouton.

*dwStyle*<br/>
Spécifie le style du contrôle bouton. Appliquer n’importe quelle combinaison de [styles des boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles) au bouton.

*Rect*<br/>
Spécifie la taille et la position du contrôle bouton. Il peut s’agir un `CRect` objet ou un `RECT` structure.

*pParentWnd*<br/>
Spécifie les fenêtre du parent du contrôle de bouton, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de bouton

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CButton` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle de bouton Windows et l’attache à la `CButton` objet.

Si le style WS_VISIBLE est indiqué, Windows envoie le contrôle de bouton à tous les messages qui sont requises pour activer et afficher le bouton.

Appliquer les éléments suivants [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle de bouton :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_GROUP aux contrôles de groupe

- WS_TABSTOP pour inclure le bouton dans l’ordre de tabulation

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>  CButton::DrawItem

Appelé par le framework lorsqu’un aspect visuel d’un bouton owner-drawn a été modifiée.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur long désignant un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure. La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Un bouton owner-drawn a le style BS_OWNERDRAW définie. Remplacez cette fonction membre pour implémenter le dessin pour un owner-drawn `CButton` objet. L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant le membre de fonction se termine.

Consultez également le [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) valeurs de style.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>  CButton::GetBitmap

Appelez cette fonction membre pour obtenir le handle d’une image bitmap, précédemment défini avec [SetBitmap](#setbitmap), qui est associé à un bouton.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers une image bitmap. NULL si aucune bitmap n’est déjà spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle

Récupère des informations sur le style du contrôle bouton.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne les styles de bouton pour ce `CButton` objet. Cette fonction retourne uniquement le [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) style des valeurs, pas les autres styles de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>  CButton::GetCheck

Récupère l’état d’activation d’une case d’option ou une case à cocher.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour d’un contrôle bouton créé avec le BS_AUTOCHECKBOX BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON ou BS_3STATE style est une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|BST_UNCHECKED|État du bouton est désactivé.|
|BST_CHECKED|État du bouton est vérifiée.|
|BST_INDETERMINATE|État du bouton est indéterminé (s’applique uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE).|

Si le bouton présente sous n’importe quel autre style, la valeur de retour est BST_UNCHECKED.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>  CButton::GetCursor

Appelez cette fonction membre pour obtenir le handle d’un curseur défini précédemment avec [SetCursor](#setcursor), qui est associé à un bouton.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Handle vers une image de curseur. NULL si aucun curseur n’est spécifié précédemment.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>  CButton::GetIcon

Appelez cette fonction membre pour obtenir le handle d’un jeu d’icônes, précédemment avec [SetIcon](#seticon), qui est associé à un bouton.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Un handle d’une icône. NULL si aucune icône n’est spécifiée précédemment.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>  CButton::GetIdealSize

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

Cette fonction membre émule la fonctionnalité du message BCM_GETIDEALSIZE, comme décrit dans la [boutons](https://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.

##  <a name="getimagelist"></a>  CButton::GetImageList

Appelez cette méthode pour obtenir la liste d’images à partir du contrôle de bouton.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Un pointeur vers la liste d’images de la `CButton` objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité du message BCM_GETIMAGELIST, comme décrit dans la [boutons](https://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.

##  <a name="getnote"></a>  CButton::GetNote

Récupère le texte de note associé au contrôle de lien de commande actuelle.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|[out] Pointeur vers une mémoire tampon, ce qui l’appelant est responsable de l’allocation et désallocation. Si la valeur de retour est TRUE, la mémoire tampon contient le texte de la Remarque qui est associé au contrôle de lien de commande en cours ; Sinon, la mémoire tampon est inchangée.|
|*cchNote*|[in, out] Pointeur vers une variable d’entier non signé.<br /><br /> Lorsque cette méthode est appelée, la variable contient la taille de la mémoire tampon spécifiée par le *lpszNote* paramètre.<br /><br /> Lorsque cette méthode est retournée, si la valeur renvoyée est TRUE, la variable contient la taille de la note associée au contrôle de lien de commande actuelle. Si la valeur de retour est FALSE, la variable contient la taille de mémoire tampon requise pour contenir la note.|

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, un [CString](../../atl-mfc-shared/using-cstring.md) objet qui contient le texte de note associé au contrôle de lien de commande actuelle.

- ou -

Dans la seconde surcharge, TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [BCM_GETNOTE](/windows/desktop/Controls/bcm-getnote) message, qui est décrite dans le SDK Windows.

##  <a name="getnotelength"></a>  CButton::GetNoteLength

Récupère la longueur du texte de note pour le contrôle de lien de commande actuelle.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du texte de note, en caractères Unicode 16 bits, pour le contrôle de lien de commande actuelle.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [BCM_GETNOTELENGTH](/windows/desktop/Controls/bcm-getnotelength) message, qui est décrite dans le SDK Windows.

##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph

Récupère le glyphe associé au contrôle de bouton Fractionner en cours.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valeur de retour

Le caractère de glyphe associé au contrôle de bouton Fractionner en cours.

### <a name="remarks"></a>Notes

Un glyphe est la représentation physique d’un caractère dans une police particulière. Par exemple, un contrôle bouton partagé peut être décoré avec le glyphe du caractère de case à cocher Unicode (U + 2713).

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_GLYPH et l’envoie que la structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le Windows SDK. Lorsque la fonction de message est retournée, cette méthode récupère le glyphe à partir de la `himlGlyph` membre de la structure.

##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList

Récupère le [liste d’images](../../mfc/reference/cimagelist-class.md) pour le contrôle de bouton partagé actuel.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_IMAGE et l’envoie que la structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le Windows SDK. Lorsque la fonction de message est retournée, cette méthode récupère la liste d’images à partir de la `himlGlyph` membre de la structure.

##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo

Récupère les paramètres qui déterminent la manière dont Windows crée le contrôle de bouton partagé actuel.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo*|[out] Pointeur vers un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure qui reçoit des informations sur le contrôle de bouton partagé actuel. L’appelant est responsable de l’allocation de la structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message, qui est décrite dans le SDK Windows.

##  <a name="getsplitsize"></a>  CButton::GetSplitSize

Récupère le rectangle englobant du composant de liste déroulante du contrôle de bouton de fractionnement actuel.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSize*|[out] Pointeur vers un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure qui reçoit la description d’un rectangle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Lorsque le contrôle bouton partagé est développé, il peut afficher un composant de liste déroulante tel qu’un contrôle de liste ou d’un contrôle de pagineur. Cette méthode récupère le rectangle englobant qui contient le composant de liste déroulante.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_SIZE et l’envoie que la structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le Windows SDK. Lorsque la fonction de message est retournée, cette méthode récupère le rectangle englobant de le `size` membre de la structure.

##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle

Récupère les styles de bouton de fractionnement qui définissent le contrôle de bouton partagé actuel.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Combinaison au niveau du bit de styles de boutons de fractionnement. Pour plus d’informations, consultez le `uSplitStyle` membre de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles de bouton Fractionner spécifient l’alignement, le rapport hauteur / largeur et le format graphique avec laquelle Windows Dessine une icône de bouton de fractionnement.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_STYLE et l’envoie que la structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le Windows SDK. Lorsque la fonction de message est retournée, cette méthode récupère les styles de bouton de fractionnement à partir de la `uSplitStyle` membre de la structure.

##  <a name="getstate"></a>  CButton::GetState

Récupère l’état d’un contrôle bouton.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valeur de retour

Un champ de bits qui contient la combinaison de valeurs qui indiquent l’état actuel d’un contrôle bouton. Le tableau suivant répertorie les valeurs possibles.

|État du bouton|Value|Description|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|L’état initial.|
|BST_CHECKED|0 x 0001|Le contrôle bouton est activé.|
|BST_INDETERMINATE|0 x 0002|L’état est indéterminé (possible uniquement lorsque le contrôle de bouton a trois états).|
|BST_PUSHED|0 x 0004|Le contrôle bouton est enfoncé.|
|BST_FOCUS|0x0008|Le contrôle de bouton a le focus.|

### <a name="remarks"></a>Notes

Un contrôle de bouton avec le style de bouton BS_3STATE ou BS_AUTO3STATE crée une case à cocher qui a un troisième état nommé un état indéterminé. Un état indéterminé indique que la case à cocher n’est ni activé ni désactivé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>  CButton::GetTextMargin

Appelez cette méthode pour obtenir la marge de texte de la `CButton` objet.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin*<br/>
Un pointeur de la marge de texte de la `CButton` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la marge de texte.

### <a name="remarks"></a>Notes

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité du message BCM_GETTEXTMARGIN, comme décrit dans la [boutons](https://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.

##  <a name="setbitmap"></a>  CButton::SetBitmap

Appelez cette fonction membre pour associer une nouvelle image bitmap avec le bouton.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Le handle d’une image bitmap.

### <a name="return-value"></a>Valeur de retour

Le handle d’une image bitmap précédemment associé au bouton.

### <a name="remarks"></a>Notes

L’image bitmap sera automatiquement placée sur le bouton centré par défaut. Si la bitmap est trop grande pour le bouton, il apparaît découpé chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par un bouton, `SetBitmap` n'utilise qu’une seule bitmap par le bouton. Lorsque le bouton est enfoncé, l’image bitmap s’affiche pour décaler vers le bas et vers la droite.

Vous êtes chargé de libérer la bitmap lorsque vous avez terminé avec lui.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>  CButton::SetButtonStyle

Modifie le style d’un bouton.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Spécifie le [bouton style](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Spécifie si le bouton doit être redessiné. Une valeur différente de zéro redessine le bouton. Une valeur 0 n’a pas ne redessine le bouton. Par défaut, le bouton est redessiné.

### <a name="remarks"></a>Notes

Utilisez le `GetButtonStyle` fonction membre pour récupérer le style de bouton. Le mot de poids faible du style de bouton terminé correspond au style de bouton spécifiques.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>  CButton::SetCheck

Définit ou réinitialise l’état d’activation d’une case d’option ou une case à cocher.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nVérifiez*<br/>
Spécifie l’état d’activation. Ce paramètre peut être une des opérations suivantes :

|Value|Signification|
|-----------|-------------|
|BST_UNCHECKED|Définir l’état du bouton de la case à cocher.|
|BST_CHECKED|Définir l’état du bouton vérifié.|
|BST_INDETERMINATE|La valeur est l’état indéterminé. Cette valeur peut être utilisée uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE.|

### <a name="remarks"></a>Notes

Cette fonction membre n’a aucun effet sur un bouton de commande.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>  CButton::SetCursor

Appelez cette fonction membre pour associer un nouveau curseur avec le bouton.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
Le handle d’un curseur.

### <a name="return-value"></a>Valeur de retour

Le handle d’un curseur précédemment associé au bouton.

### <a name="remarks"></a>Notes

Le curseur est automatiquement placé sur le bouton centré par défaut. Si le curseur est trop grand pour le bouton, il apparaît découpé chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par un bouton, `SetCursor` n'utilise qu’un seul curseur par le bouton. Lorsque le bouton est enfoncé, le curseur s’affiche pour décaler vers le bas et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>  CButton::SetDropDownState

Définit l’état de la liste déroulante du contrôle de bouton de fractionnement actuel.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fDropDown*|[in] TRUE pour définir l’état BST_DROPDOWNPUSHED ; Sinon, FALSE.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Un contrôle de bouton partagé a un style de BS_SPLITBUTTON ou BS_DEFSPLITBUTTON et se compose d’un bouton et une flèche de déroulement à sa droite. Pour plus d’informations, consultez [Styles de boutons](/windows/desktop/Controls/button-styles). En règle générale, l’état de la liste déroulante est défini lorsque l’utilisateur clique sur la flèche déroulante. Utilisez cette méthode pour définir par programme l’état de la liste déroulante du contrôle. La flèche est dessinée grisée pour indiquer l’état.

Cette méthode envoie le [BCM_SETDROPDOWNSTATE](/windows/desktop/Controls/bcm-setdropdownstate) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_splitButton*, qui est utilisé pour accéder par programmation le contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit l’état du contrôle de bouton de fractionnement pour indiquer que la flèche de déroulement est envoyée.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired

Définit l’état du contrôle de bouton actuel à `elevation required`, ce qui est nécessaire pour le contrôle afficher une icône avec élévation de privilèges de sécurité.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fElevationRequired*|[in] True pour définir `elevation required` état ; sinon, FALSE.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Si un contrôle de lien de bouton ou la commande nécessite une autorisation de sécurité avec élévation de privilèges pour exécuter une action, la valeur est le contrôle `elevation required` état. Par la suite, Windows affiche l’icône de bouclier du contrôle de compte utilisateur (UAC) sur le contrôle. Pour plus d’informations, consultez « Contrôle de compte d’utilisateur » à l’adresse [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).

Cette méthode envoie le [BCM_SETSHIELD](/windows/desktop/Controls/bcm-setshield) message, qui est décrite dans le SDK Windows.

##  <a name="seticon"></a>  CButton::SetIcon

Appelez cette fonction membre pour associer une icône de nouveau avec le bouton.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
Le handle d’une icône.

### <a name="return-value"></a>Valeur de retour

Le handle d’une icône précédemment associé au bouton.

### <a name="remarks"></a>Notes

L’icône sera automatiquement placée sur le bouton centré par défaut. Si l’icône est trop grande pour le bouton, il apparaît découpé chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre bitmaps par un bouton, `SetIcon` utilise uniquement une icône par le bouton. Lorsque le bouton est enfoncé, l’icône s’affiche pour décaler vers le bas et vers la droite.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>  CButton::SetImageList

Appelez cette méthode pour définir la liste d’images de la `CButton` objet.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Paramètres

*pbuttonImagelist*<br/>
Pointeur vers la nouvelle liste d’images.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité du message BCM_SETIMAGELIST, comme décrit dans la [boutons](https://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.

##  <a name="setnote"></a>  CButton::SetNote

Définit le texte de note pour le contrôle de lien de commande actuelle.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszNote*|[in] Pointeur vers une chaîne Unicode qui est définie en tant que texte de la note pour le contrôle de lien de commande.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_COMMANDLINK ou BS_DEFCOMMANDLINK.

Cette méthode envoie le [BCM_SETNOTE détermine](/windows/desktop/Controls/bcm-setnote) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_cmdLink*, qui est utilisé pour accéder par programmation le contrôle de lien de commande. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le texte de note pour le contrôle de lien de commande.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>  CButton::SetSplitGlyph

Associe un glyphe spécifié avec le contrôle de bouton partagé actuel.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*chGlyph*|[in] Un caractère qui spécifie le glyphe à utiliser comme la fractionnement bouton flèche de déroulement.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles qui ont le style de bouton BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Un glyphe est la représentation physique d’un caractère dans une police particulière. Le *chGlyph* paramètre n’est pas utilisé en tant que le glyphe, mais il est utilisé à la place pour sélectionner un glyphe à partir d’un jeu de glyphes définie par le système. Le glyphe de flèche de déroulement par défaut est spécifié par un caractère « 6 » et ressemble à caractère Unicode TRIANGLE pointant noir vers le bas (U + 25BC).

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_GLYPH et le `himlGlyph` membre avec le *chGlyph* paramètre et qui envoie ensuite structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le SDK Windows.

##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList

Associe un [liste d’images](../../mfc/reference/cimagelist-class.md) avec le contrôle de bouton partagé actuel.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSplitImageList*|[in] Pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet à affecter pour le contrôle de bouton partagé actuel.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode initialise le `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_IMAGE et le `himlGlyph` membre avec le *pSplitImageList* paramètre et l’envoie Cette structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le SDK Windows.

##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo

Spécifie les paramètres qui déterminent la manière dont Windows crée le contrôle de bouton partagé actuel.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pInfo*|[in] Pointeur vers un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure qui définit le contrôle de bouton partagé actuel.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Cette méthode envoie le [BCM_SETSPLITINFO](/windows/desktop/Controls/bcm-setsplitinfo) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programmation le contrôle bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie le glyphe est utilisé pour la fractionnement bouton flèche de déroulement. L’exemple remplace un glyphe de triangle pointant vers le haut pour le glyphe de triangle pointant vers le bas par défaut. Le glyphe affiché varie selon le caractère que vous spécifiez dans le `himlGlyph` membre de la `BUTTON_SPLITINFO` structure. Le glyphe de triangle pointant vers le bas est spécifié par un caractère « 6 » et le glyphe de triangle pointant vers le haut est spécifié par un caractère ' 5'. Pour la comparaison, consultez la méthode pratique, [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>  CButton::SetSplitSize

Définit le rectangle englobant du composant de liste déroulante du contrôle de bouton de fractionnement actuel.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pSize*|[in] Pointeur vers un [taille](https://msdn.microsoft.com/library/windows/desktop/dd145106) structure qui décrit un rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Lorsque le contrôle bouton partagé est développé, il peut afficher un composant de liste déroulante tel qu’un contrôle de liste ou d’un contrôle de pagineur. Cette méthode spécifie la taille du rectangle englobant qui contient le composant de liste déroulante.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_SIZE et `size` membre avec le *pSize* paramètre et l’envoie de structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programmation le contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple suivant double la taille de la flèche déroulante du bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle

Définit le style du contrôle de bouton de fractionnement actuel.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*uSplitStyle*|[in] Combinaison au niveau du bit de styles de boutons de fractionnement. Pour plus d’informations, consultez le `uSplitStyle` membre de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est BS_SPLITBUTTON ou BS_DEFSPLITBUTTON.

Les styles de bouton Fractionner spécifient l’alignement, le rapport hauteur / largeur et le format graphique avec laquelle Windows Dessine une icône de bouton de fractionnement. Pour plus d’informations, consultez le `uSplitStyle` membre de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure.

Cette méthode initialise la `mask` membre d’un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) structure avec l’indicateur BCSIF_STYLE et le `uSplitStyle` membre avec le *uSplitStyle* paramètre et qui envoie ensuite structure dans le [adaptées à vos](/windows/desktop/Controls/bcm-getsplitinfo) message qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programmation le contrôle bouton partagé.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le style de la flèche déroulante du bouton partagé. Le style BCSS_ALIGNLEFT affiche la flèche sur le côté gauche du bouton et le style BCSS_STRETCH conserve les proportions de la flèche déroulante quand vous redimensionnez le bouton.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>  CButton::SetState

Définit si un contrôle bouton est mis en surbrillance ou non.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight*<br/>
Spécifie si le bouton est à mettre en surbrillance. Une valeur différente de zéro met en évidence le bouton ; une valeur 0 supprime toute mise en surbrillance.

### <a name="remarks"></a>Notes

Mise en surbrillance affecte à l’extérieur d’un contrôle bouton. Il n’a aucun effet sur l’état d’activation d’une case d’option ou une case à cocher.

Un contrôle bouton est automatiquement mis en surbrillance lorsque l’utilisateur clique et maintient le bouton gauche de la souris. La mise en surbrillance est supprimé lorsque l’utilisateur relâche le bouton de la souris.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>  CButton::SetTextMargin

Appelez cette méthode pour définir la marge de texte de la `CButton` objet.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Paramètres

*pmargin*<br/>
Pointeur vers les nouvelles marges de texte.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité du message BCM_SETTEXTMARGIN, comme décrit dans la [boutons](https://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton, classe](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
