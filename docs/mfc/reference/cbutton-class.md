---
title: Classe de CButton | Documents Microsoft
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
ms.openlocfilehash: 5e232c363da4c9bbaf7e049551f9e2915671098c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957440"
---
# <a name="cbutton-class"></a>Classe de CButton
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
|[CButton::Create](#create)|Crée le contrôle de bouton Windows et l’attache à le `CButton` objet.|  
|[CButton::DrawItem](#drawitem)|Remplacement pour dessiner un owner-drawn `CButton` objet.|  
|[CButton::GetBitmap](#getbitmap)|Récupère le handle de l’image bitmap précédemment défini avec [SetBitmap](#setbitmap).|  
|[CButton::GetButtonStyle](#getbuttonstyle)|Récupère des informations sur le style du contrôle bouton.|  
|[CButton::GetCheck](#getcheck)|Récupère l’état d’activation d’un contrôle bouton.|  
|[CButton::GetCursor](#getcursor)|Récupère le handle de l’image de curseur défini précédemment avec [SetCursor](#setcursor).|  
|[CButton::GetIcon](#geticon)|Récupère le handle de l’icône précédemment défini avec [SetIcon](#seticon).|  
|[CButton::GetIdealSize](#getidealsize)|Récupère la taille idéale du contrôle button.|  
|[CButton::GetImageList](#getimagelist)|Récupère la liste d’images du contrôle button.|  
|[CButton::GetNote](#getnote)|Récupère le composant Remarque du contrôle de lien de commande en cours.|  
|[CButton::GetNoteLength](#getnotelength)|Récupère la longueur du texte de la note pour le contrôle de lien de commande en cours.|  
|[CButton::GetSplitGlyph](#getsplitglyph)|Récupère le glyphe associé avec le contrôle de bouton partagé actuel.|  
|[CButton::GetSplitImageList](#getsplitimagelist)|Récupère la liste d’images pour le contrôle de bouton partagé actuel.|  
|[CButton::GetSplitInfo](#getsplitinfo)|Récupère les informations qui définissent le contrôle de bouton partagé actuel.|  
|[CButton::GetSplitSize](#getsplitsize)|Récupère le rectangle englobant du composant de liste déroulante du contrôle de bouton Fractionner en cours.|  
|[CButton::GetSplitStyle](#getsplitstyle)|Récupère les styles de bouton de fractionnement qui définissent le contrôle de bouton partagé actuel.|  
|[CButton::GetState](#getstate)|Récupère la vérification de l’état, état de mise en surbrillance et l’état de focus d’un contrôle bouton.|  
|[CButton::GetTextMargin](#gettextmargin)|Récupère la marge de texte du contrôle button.|  
|[CButton::SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher sur le bouton.|  
|[CButton::SetButtonStyle](#setbuttonstyle)|Modifie le style d’un bouton.|  
|[CButton::SetCheck](#setcheck)|Définit l’état d’activation d’un contrôle bouton.|  
|[CButton::SetCursor](#setcursor)|Spécifie une image de curseur à afficher sur le bouton.|  
|[CButton::SetDropDownState](#setdropdownstate)|Définit l’état de la liste déroulante du contrôle de bouton Fractionner en cours.|  
|[CButton::SetIcon](#seticon)|Spécifie l’icône à afficher sur le bouton.|  
|[CButton::SetImageList](#setimagelist)|Définit la liste d’images du contrôle button.|  
|[CButton::SetNote](#setnote)|Définit la Remarque sur le contrôle de lien de commande en cours.|  
|[CButton::SetSplitGlyph](#setsplitglyph)|Associe un glyphe spécifié avec le contrôle de bouton partagé actuel.|  
|[CButton::SetSplitImageList](#setsplitimagelist)|Associe une liste d’images avec le contrôle de bouton partagé actuel.|  
|[CButton::SetSplitInfo](#setsplitinfo)|Spécifie les informations qui définissent le contrôle de bouton partagé actuel.|  
|[CButton::SetSplitSize](#setsplitsize)|Définit le rectangle englobant du composant de liste déroulante du contrôle de bouton Fractionner en cours.|  
|[CButton::SetSplitStyle](#setsplitstyle)|Définit le style du contrôle de bouton Fractionner en cours.|  
|[CButton::SetState](#setstate)|Définit l’état de mise en surbrillance d’un contrôle bouton.|  
|[CButton::SetTextMargin](#settextmargin)|Définit la marge de texte du contrôle button.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle bouton est une fenêtre enfant de petite taille, rectangulaire que vous pouvez cliquer sur et hors tension. Boutons peuvent être utilisés seul ou en groupes et peuvent soit être étiquetés ou sans texte. Un bouton change généralement apparence lorsque l’utilisateur clique dessus.  
  
 Les boutons par défaut sont la case à cocher, case d’option et bouton de commande. A `CButton` objet peut devenir un de ces éléments, conformément à la [bouton style](../../mfc/reference/styles-used-by-mfc.md#button-styles) spécifié lors de son initialisation par le [créer](#create) fonction membre.  
  
 En outre, le [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) dérivé de la classe `CButton` prend en charge la création de contrôles bouton étiquetés avec des images bitmap au lieu de texte. Un `CBitmapButton` peut avoir des bitmaps distinctes pour un bouton du, vers le bas, le focus et désactivé des États.  
  
 Vous pouvez créer un contrôle de bouton à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, tout d’abord appeler le constructeur `CButton` pour construire le `CButton` de l’objet, puis appelez le `Create` fonction membre pour créer les fenêtres de contrôle de bouton et en l’attachant à la `CButton` objet.  
  
 Construction peut être un processus en une étape dans une classe dérivée de `CButton`. Écrire un constructeur pour la classe dérivée et appelez `Create` à partir de dans le constructeur.  
  
 Si vous souhaitez traiter les messages de notification Windows envoyés par un contrôle de bouton à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajouter une fonction table des messages de membre des entrée et le Gestionnaire de messages à la classe parente pour chaque message.  
  
 Chaque entrée de table des messages prend la forme suivante :  
  
 **ON_** Notification **(**`id`, `memberFxn` **)**  
  
 où `id` Spécifie l’ID de fenêtre enfant du contrôle qui envoie la notification et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.  
  
 Prototype de fonction du parent est la suivante :  
  
 **afx_msg** `void` `memberFxn` **() ;**  
  
 Les entrées de table des messages potentielles sont les suivantes :  
  
|Entrée de mappage|Envoyés vers le parent lorsque...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|L’utilisateur clique sur un bouton.|  
|**ON_BN_DOUBLECLICKED**|L’utilisateur double-clique sur un bouton.|  
  
 Si vous créez un `CButton` objet à partir d’une ressource de boîte de dialogue, la `CButton` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CButton` de l’objet dans une fenêtre, vous devrez peut-être à détruire. Si vous créez le `CButton` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet pour détruire lorsque l’utilisateur ferme les fenêtres de contrôle de bouton. Si vous créez le `CButton` objet sur la pile, ou il est incorporé dans l’objet de la boîte de dialogue parent, il est supprimé automatiquement.  
  
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
 Crée le contrôle de bouton Windows et l’attache à le `CButton` objet.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszCaption*  
 Spécifie le texte du contrôle de bouton.  
  
 *dwStyle*  
 Spécifie le style du contrôle bouton. Appliquer n’importe quelle combinaison de [styles des boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles) au bouton.  
  
 *Rect*  
 Spécifie la taille et la position du contrôle bouton. Il peut être soit un `CRect` objet ou un `RECT` structure.  
  
 *pParentWnd*  
 Spécifie les fenêtre du parent du contrôle de bouton, généralement un `CDialog`. Il ne doit pas être **NULL**.  
  
 *nID*  
 Spécifie l’ID. du contrôle de bouton  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CButton` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle de bouton Windows et l’attache à le `CButton` objet.  
  
 Si le **WS_VISIBLE** style est fourni, Windows envoie le contrôle de tous les messages qui sont requises pour activer et afficher le bouton.  
  
 Appliquez ce qui suit [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle bouton :  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
- **WS_GROUP** aux contrôles de groupe  
  
- **WS_TABSTOP** d’inclure le bouton dans l’ordre de tabulation  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CButton::DrawItem  
 Appelé par l’infrastructure quand un aspect visuel d’un bouton owner-drawn a changé.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpDrawItemStruct*  
 Un pointeur long désignant un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure. La structure contient des informations sur l’élément doit être dessiné et le type de dessin nécessaire.  
  
### <a name="remarks"></a>Notes  
 Un bouton owner-drawn a la **BS_OWNERDRAW** set de style. Remplacez cette fonction membre pour implémenter le dessin pour un owner-drawn `CButton` objet. L’application doit restaurer tous les objets interface GDI périphérique graphique sélectionnés pour le contexte d’affichage fournie dans *lpDrawItemStruct* avant le membre de la fonction s’arrête.  
  
 Consultez également le [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) valeurs de style.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>  CButton::GetBitmap  
 Appelez cette fonction membre pour obtenir le handle d’une image bitmap, précédemment défini avec [SetBitmap](#setbitmap), qui est associé à un bouton.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers une image bitmap. **NULL** si aucune bitmap n’est déjà spécifié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle  
 Récupère des informations sur le style du contrôle bouton.  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne les styles de bouton pour ce `CButton` objet. Cette fonction retourne uniquement le [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) valeurs style, pas les autres styles de fenêtre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>  CButton::GetCheck  
 Récupère l’état d’activation d’une case d’option ou une case à cocher.  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour à partir d’un contrôle bouton créé avec le **BS_AUTOCHECKBOX**, **BS_AUTORADIOBUTTON**, **BS_AUTO3STATE**, **BS_CHECKBOX**, **BS_RADIOBUTTON**, ou **BS_3STATE** style est une des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|**BST_UNCHECKED**|État du bouton est désactivé.|  
|**BST_CHECKED**|État du bouton est activé.|  
|**BST_INDETERMINATE**|État du bouton est indéterminé (s’applique uniquement si le bouton a la **BS_3STATE** ou **BS_AUTO3STATE** style).|  
  
 Si le bouton a tout autre style, la valeur de retour est **BST_UNCHECKED**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>  CButton::GetCursor  
 Appelez cette fonction membre pour obtenir le handle d’un curseur défini précédemment avec [SetCursor](#setcursor), qui est associé à un bouton.  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers une image de curseur. **NULL** si aucun curseur n’est déjà spécifié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>  CButton::GetIcon  
 Appelez cette fonction membre pour obtenir le descripteur d’une icône définie précédemment avec [SetIcon](#seticon), qui est associé à un bouton.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle d’une icône. **NULL** si aucune icône n’est déjà spécifié.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>  CButton::GetIdealSize  
 Récupère la taille idéale pour le contrôle bouton.  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>Paramètres  
 *psize*  
 Pointeur vers la taille actuelle du bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la **BCM_GETIDEALSIZE** d’un message, comme décrit dans la [boutons](http://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.  
  
##  <a name="getimagelist"></a>  CButton::GetImageList  
 Appelez cette méthode pour obtenir la liste d’images à partir du contrôle de bouton.  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbuttonImagelist*  
 Un pointeur vers la liste d’images de la `CButton` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la **BCM_GETIMAGELIST** d’un message, comme décrit dans la [boutons](http://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.  
  
##  <a name="getnote"></a>  CButton::GetNote  
 Récupère le texte de note associé au contrôle de lien de commande en cours.  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[out] *lpszNote*|Pointeur vers une mémoire tampon, l’appelant est responsable de l’allocation et désallocation. Si la valeur de retour est `true`, la mémoire tampon contient le texte de la note qui est associé au contrôle de lien de commande en cours ; sinon, la mémoire tampon reste inchangée.|  
|[dans, out] *cchNote*|Pointeur vers une variable d’entier non signé.<br /><br /> Lorsque cette méthode est appelée, la variable contient la taille de la mémoire tampon spécifiée par le *lpszNote* paramètre.<br /><br /> Lorsque cette méthode est retournée, si la valeur de retour est `true` la variable contient la taille de la note associée au contrôle de lien de commande en cours. Si la valeur de retour est `false`, la variable contient la taille de mémoire tampon requise pour contenir la note.|  
  
### <a name="return-value"></a>Valeur de retour  
 Dans la première surcharge, une [CString](../../atl-mfc-shared/using-cstring.md) objet qui contient le texte de la note associé au contrôle de lien de commande en cours.  
  
 - ou -  
  
 Dans la seconde surcharge, `true` si cette méthode réussit ; sinon, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_COMMANDLINK` ou `BS_DEFCOMMANDLINK`.  
  
 Cette méthode envoie le [BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getnotelength"></a>  CButton::GetNoteLength  
 Récupère la longueur du texte de la note pour le contrôle de lien de commande en cours.  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur du texte de note, en caractères Unicode 16 bits, pour le contrôle de lien de commande en cours.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_COMMANDLINK` ou `BS_DEFCOMMANDLINK`.  
  
 Cette méthode envoie le [BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph  
 Récupère le glyphe associé avec le contrôle de bouton partagé actuel.  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le caractère de glyphe associé avec le contrôle de bouton partagé actuel.  
  
### <a name="remarks"></a>Notes  
 Un glyphe est la représentation physique d’un caractère dans une police particulière. Par exemple, un contrôle bouton partagé peut être décoré avec le glyphe de la case à cocher caractère Unicode (U + 2713).  
  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_GLYPH` indicateur, puis envoie la structure dans le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message décrit dans le SDK Windows. Retour de la fonction de message, cette méthode récupère le glyphe à partir de la `himlGlyph` membre de la structure.  
  
##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList  
 Récupère le [liste d’images](../../mfc/reference/cimagelist-class.md) pour le contrôle de bouton partagé actuel.  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_IMAGE` indicateur, puis envoie la structure dans le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message décrit dans le SDK Windows. Retour de la fonction de message, cette méthode récupère la liste d’images à partir de la `himlGlyph` membre de la structure.  
  
##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo  
 Récupère les paramètres qui déterminent la manière dont Windows crée le contrôle de bouton partagé actuel.  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[out] *pInfo*|Pointeur vers un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure qui reçoit des informations sur le contrôle de bouton partagé actuel. L’appelant est responsable de l’allocation de la structure.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Cette méthode envoie le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getsplitsize"></a>  CButton::GetSplitSize  
 Récupère le rectangle englobant du composant de liste déroulante du contrôle de bouton Fractionner en cours.  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[out] *pSize*|Pointeur vers un [taille](http://msdn.microsoft.com/library/windows/desktop/dd145106) structure qui reçoit la description d’un rectangle.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Lorsque le contrôle bouton partagé est développé, il peut afficher un composant de liste déroulante par exemple un contrôle de liste ou un contrôle pager. Cette méthode récupère le rectangle englobant qui contient le composant de liste déroulante.  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_SIZE` indicateur, puis envoie la structure dans le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message décrit dans le SDK Windows. Retour de la fonction de message, cette méthode récupère le rectangle englobant de le `size` membre de la structure.  
  
##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle  
 Récupère les styles de bouton de fractionnement qui définissent le contrôle de bouton partagé actuel.  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Combinaison de bits de styles de bouton de fractionnement. Pour plus d’informations, consultez la `uSplitStyle` membre de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Les styles de bouton Fractionner spécifient l’alignement, proportions et format graphique avec laquelle Windows Dessine une icône de bouton de fractionnement.  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_STYLE` indicateur, puis envoie la structure dans le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message décrit dans le SDK Windows. Retour de la fonction de message, cette méthode récupère les styles de bouton de fractionnement à partir de la `uSplitStyle` membre de la structure.  
  
##  <a name="getstate"></a>  CButton::GetState  
 Récupère l’état d’un contrôle bouton.  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un champ de bits qui contient la combinaison de valeurs qui indiquent l’état actuel d’un contrôle bouton. Le tableau suivant répertorie les valeurs possibles.  
  
|État du bouton|Value|Description|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|L’état initial.|  
|`BST_CHECKED`|0 x 0001|Le contrôle de bouton est activé.|  
|`BST_INDETERMINATE`|0 x 0002|L’état est indéterminé (possible uniquement lorsque le contrôle de bouton a trois états).|  
|`BST_PUSHED`|0 x 0004|Le contrôle bouton est enfoncé.|  
|`BST_FOCUS`|0x0008|Le contrôle a le focus.|  
  
### <a name="remarks"></a>Notes  
 Un contrôle de bouton avec le `BS_3STATE` ou `BS_AUTO3STATE` style de bouton crée une case à cocher qui a un État tiers qui porte l’état indéterminé. L’état indéterminé indique que la case à cocher n’est ni activé ni désactivé.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>  CButton::GetTextMargin  
 Appelez cette méthode pour obtenir la marge de texte de la `CButton` objet.  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Paramètres  
 *pmargin*  
 Un pointeur de la marge de texte de la `CButton` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la marge de texte.  
  
### <a name="remarks"></a>Notes  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la **BCM_GETTEXTMARGIN** d’un message, comme décrit dans la [boutons](http://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.  
  
##  <a name="setbitmap"></a>  CButton::SetBitmap  
 Appelez cette fonction membre pour associer une nouvelle image bitmap avec le bouton.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 *hBitmap*  
 Le handle d’une image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle d’une image bitmap précédemment associé au bouton.  
  
### <a name="remarks"></a>Notes  
 L’image bitmap est automatiquement placé sur le bouton centré par défaut. Si la bitmap est trop grande pour le bouton, il apparaît découpé sur chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre images bitmap par un bouton, `SetBitmap` utilise uniquement une image bitmap par le bouton. Lorsque le bouton est activé, l’image bitmap s’affiche à déplacer vers le bas et à droite.  
  
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
 *nStyle*  
 Spécifie le [bouton style](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 *bRedraw*  
 Spécifie si le bouton doit être redessiné. Une valeur différente de zéro redessine le bouton. Une valeur 0 ne redessine pas le bouton. Par défaut, le bouton est redessiné.  
  
### <a name="remarks"></a>Notes  
 Utilisez le `GetButtonStyle` fonction membre pour récupérer le style de bouton. Le mot de poids faible du style de bouton terminé est le style de bouton spécifiques.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>  CButton::SetCheck  
 Active ou désactive la vérification de l’état d’une case d’option ou une case à cocher.  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVérifiez*  
 Spécifie l’état d’activation. Ce paramètre peut être une des opérations suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|**BST_UNCHECKED**|Définir l’état du bouton de la case à cocher.|  
|**BST_CHECKED**|Définir l’état activé.|  
|**BST_INDETERMINATE**|La valeur l’état indéterminé. Cette valeur peut être utilisée uniquement si le bouton a la **BS_3STATE** ou **BS_AUTO3STATE** style.|  
  
### <a name="remarks"></a>Notes  
 Il n’y a aucun effet sur un bouton de commande pour cette fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>  CButton::SetCursor  
 Appelez cette fonction membre pour associer un nouveau curseur avec le bouton.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Paramètres  
 *hCursor*  
 Le handle d’un curseur.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle d’un curseur précédemment associé au bouton.  
  
### <a name="remarks"></a>Notes  
 Le curseur est automatiquement placé sur le bouton centré par défaut. Si le curseur est trop grand pour le bouton, il apparaît découpé sur chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre images bitmap par un bouton, `SetCursor` utilise uniquement un curseur par le bouton. Lorsque le bouton est activé, le curseur s’affiche à déplacer vers le bas et à droite.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>  CButton::SetDropDownState  
 Définit l’état de la liste déroulante du contrôle de bouton Fractionner en cours.  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *fDropDown*|`true` Pour définir `BST_DROPDOWNPUSHED` état ; sinon, `false`.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Un contrôle bouton partagé a un style de `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON` et se compose d’un bouton et une flèche de déroulement située à sa droite. Pour plus d’informations, consultez [les Styles de bouton](http://msdn.microsoft.com/library/windows/desktop/bb775951). En règle générale, l’état de la liste déroulante est définie lorsque l’utilisateur clique sur la flèche déroulante. Utilisez cette méthode pour définir par programme l’état de la liste déroulante du contrôle. La flèche de déroulement est dessinée grisée pour indiquer l’état.  
  
 Cette méthode envoie le [BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, *m_splitButton*, qui est utilisé pour accéder par programme le contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit l’état du contrôle de bouton de fractionnement pour indiquer que la flèche de déroulement est envoyée.  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired  
 Définit l’état du contrôle bouton actuel pour `elevation required`, ce qui est nécessaire pour le contrôle afficher une icône avec élévation de privilèges de sécurité.  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `fElevationRequired`|`true` Pour définir `elevation required` état ; sinon, `false`.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Si un contrôle de lien de bouton ou la commande requiert l’autorisation de sécurité avec élévation de privilèges pour exécuter une action, la valeur du contrôle `elevation required` état. Par la suite, Windows affiche l’icône de bouclier du contrôle de compte d’utilisateur (UAC) sur le contrôle. Pour plus d’informations, consultez « Contrôle de compte d’utilisateur » à [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).  
  
 Cette méthode envoie le [BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="seticon"></a>  CButton::SetIcon  
 Appelez cette fonction membre pour associer une icône de nouveau avec le bouton.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 *hIcon*  
 Le handle d’une icône.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle d’une icône précédemment associé au bouton.  
  
### <a name="remarks"></a>Notes  
 L’icône sera automatiquement placé sur le bouton centré par défaut. Si l’icône est trop grande pour le bouton, il apparaît découpé sur chaque côté. Vous pouvez choisir d’autres options d’alignement, notamment les suivantes :  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 Contrairement aux [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), qui utilise quatre images bitmap par un bouton, `SetIcon` utilise uniquement une icône par le bouton. Lorsque le bouton est activé, l’icône s’affiche à déplacer vers le bas et à droite.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>  CButton::SetImageList  
 Appelez cette méthode pour définir la liste d’images de la `CButton` objet.  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbuttonImagelist*  
 Pointeur vers la nouvelle liste d’images.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la **BCM_SETIMAGELIST** d’un message, comme décrit dans la [boutons](http://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.  
  
##  <a name="setnote"></a>  CButton::SetNote  
 Définit le texte de note pour le contrôle de lien de commande en cours.  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *lpszNote*|Pointeur vers une chaîne Unicode qui est définie en tant que texte de la note pour le contrôle de lien de commande.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_COMMANDLINK` ou `BS_DEFCOMMANDLINK`.  
  
 Cette méthode envoie le [BCM_SETNOTE détermine](http://msdn.microsoft.com/library/windows/desktop/bb775977) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, *m_cmdLink*, qui est utilisé pour accéder par programme le contrôle de lien de commande. Cette variable est utilisée dans l’exemple suivant.  
  
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
|[in] *chGlyph*|Un caractère qui spécifie le glyphe à utiliser en tant que la fractionnement bouton flèche de déroulement.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles qui ont le style de bouton `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Un glyphe est la représentation physique d’un caractère dans une police particulière. Le *chGlyph* paramètre n’est pas utilisé en tant que le glyphe, mais au lieu de cela permet de sélectionner un glyphe à partir d’un jeu de glyphes de définies par le système. Le glyphe de flèche de déroulement située par défaut est spécifié par un caractère '6' et ressemble à caractère Unicode TRIANGLE pointant noir vers le bas (U + 25BC).  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_GLYPH` indicateur et le `himlGlyph` membre avec le `chGlyph` paramètre, puis envoie la structure dans le [ Adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList  
 Associe un [liste d’images](../../mfc/reference/cimagelist-class.md) avec le contrôle de bouton partagé actuel.  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pSplitImageList*|Pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet à affecter pour le contrôle de bouton partagé actuel.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Cette méthode initialise la `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_IMAGE` indicateur et la `himlGlyph` membre avec le *pSplitImageList* paramètre, puis envoie cette structure le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo  
 Spécifie les paramètres qui déterminent la manière dont Windows crée le contrôle de bouton partagé actuel.  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pInfo*|Pointeur vers un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure qui définit le contrôle de bouton partagé actuel.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Cette méthode envoie le [BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programme le contrôle bouton partagé.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant modifie le glyphe est utilisé pour la fractionnement bouton flèche de déroulement. L’exemple substitue un glyphe triangle pointant vers le haut pour le glyphe de triangle pointant vers le bas par défaut. Le glyphe est affiché varie selon le caractère que vous spécifiez dans le `himlGlyph` membre de la `BUTTON_SPLITINFO` structure. Le glyphe de triangle pointant vers le bas est spécifié par un caractère ' 6 'et le glyphe de triangle pointant vers le haut est spécifié par un caractère ' 5'. Pour la comparaison, consultez la méthode pratique, [CButton::SetSplitGlyph](#setsplitglyph).  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>  CButton::SetSplitSize  
 Définit le rectangle englobant du composant de liste déroulante du contrôle de bouton Fractionner en cours.  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pSize*|Pointeur vers un [taille](http://msdn.microsoft.com/library/windows/desktop/dd145106) structure qui décrit un rectangle englobant.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Lorsque le contrôle bouton partagé est développé, il peut afficher un composant de liste déroulante par exemple un contrôle de liste ou un contrôle pager. Cette méthode spécifie la taille du rectangle englobant qui contient le composant de liste déroulante.  
  
 Cette méthode initialise la `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_SIZE` indicateur et la `size` membre avec le *pSize* paramètre et qui envoie ensuite dans la structure du [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programme le contrôle bouton partagé. Cette variable est utilisée dans l’exemple suivant.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant double la taille de la flèche déroulante de fractionnement.  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle  
 Définit le style du contrôle de bouton Fractionner en cours.  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *uSplitStyle*|Combinaison de bits de styles de bouton de fractionnement. Pour plus d’informations, consultez la `uSplitStyle` membre de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement avec les contrôles dont le style de bouton est `BS_SPLITBUTTON` ou `BS_DEFSPLITBUTTON`.  
  
 Les styles de bouton Fractionner spécifient l’alignement, proportions et format graphique avec laquelle Windows Dessine une icône de bouton de fractionnement. Pour plus d’informations, consultez la `uSplitStyle` membre de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure.  
  
 Cette méthode initialise le `mask` membre un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) structure avec le `BCSIF_STYLE` indicateur et le `uSplitStyle` membre avec le *uSplitStyle* paramètre, puis envoie Cette structure dans le [adaptées à vos](http://msdn.microsoft.com/library/windows/desktop/bb775969) message qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_splitButton`, qui est utilisé pour accéder par programme le contrôle bouton partagé.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit le style de la flèche déroulante de fractionnement. Le `BCSS_ALIGNLEFT` style affiche la flèche sur le côté gauche du bouton et le `BCSS_STRETCH` style conserve les proportions de la flèche déroulante quand vous redimensionnez le bouton.  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>  CButton::SetState  
 Définit si un contrôle bouton est mis en surbrillance ou non.  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Paramètres  
 *bHighlight*  
 Spécifie si le bouton doit être mis en surbrillance. Une valeur différente de zéro met en surbrillance le bouton ; la valeur 0 supprime toute la mise en surbrillance.  
  
### <a name="remarks"></a>Notes  
 Mise en surbrillance affecte à l’extérieur d’un contrôle bouton. Il n’a aucun effet sur la vérification de l’état d’une case d’option ou une case à cocher.  
  
 Un contrôle bouton est automatiquement mis en surbrillance lorsque l’utilisateur clique et maintient le bouton gauche de la souris. La mise en surbrillance est supprimé lorsque l’utilisateur relâche le bouton de la souris.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>  CButton::SetTextMargin  
 Appelez cette méthode pour définir les marges du texte de la `CButton` objet.  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Paramètres  
 *pmargin*  
 Pointeur vers la nouvelle marge de texte.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la **BCM_SETTEXTMARGIN** d’un message, comme décrit dans la [boutons](http://msdn.microsoft.com/library/windows/desktop/bb775943) section du Kit de développement Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [Classe de CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Classe de CStatic](../../mfc/reference/cstatic-class.md)   
 [Classe de CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog, classe](../../mfc/reference/cdialog-class.md)
