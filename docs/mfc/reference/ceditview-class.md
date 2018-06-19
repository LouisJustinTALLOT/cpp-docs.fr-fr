---
title: Classe CEditView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs:
- C++
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b15d604670ec1c458c6ca8db5b3b4eab51fb8f65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371541"
---
# <a name="ceditview-class"></a>Classe de CEditView
Type de classe d'affichage qui fournit les fonctionnalités d'un contrôle d'édition Windows et peut être utilisé pour implémenter des fonctionnalités d'éditeur de texte simples.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|Construit un objet de type `CEditView`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|Recherche une chaîne dans le texte.|  
|[CEditView::GetBufferLength](#getbufferlength)|Obtient la longueur de la mémoire tampon de caractères.|  
|[CEditView::GetEditCtrl](#geteditctrl)|Fournit l’accès à la `CEdit` partie d’un `CEditView` objet (contrôle d’édition Windows).|  
|[CEditView::GetPrinterFont](#getprinterfont)|Récupère la police d’imprimante en cours.|  
|[CEditView::GetSelectedText](#getselectedtext)|Récupère le texte sélectionné.|  
|[CEditView::LockBuffer](#lockbuffer)|Verrouille la mémoire tampon.|  
|[CEditView::PrintInsideRect](#printinsiderect)|Restitue le texte à l’intérieur d’un rectangle.|  
|[CEditView::SerializeRaw](#serializeraw)|Sérialise un `CEditView` objet sur le disque sous forme de texte brut.|  
|[CEditView::SetPrinterFont](#setprinterfont)|Définit une police d’imprimante.|  
|[CEditView::SetTabStops](#settabstops)|Jeux de tabulations pour l’affichage à l’écran et l’impression.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|Déverrouille la mémoire tampon.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|Recherche l’occurrence suivante d’une chaîne de texte.|  
|[CEditView::OnReplaceAll](#onreplaceall)|Remplace toutes les occurrences d’une chaîne donnée par une nouvelle chaîne.|  
|[CEditView::OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|Appelée lorsqu’une opération de recherche échoue correspondre à n’importe quel autre texte.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|Style par défaut pour les objets de type **CEditView.**|  
  
## <a name="remarks"></a>Notes  
 La `CEditView` classe fournit les fonctions supplémentaires suivantes :  
  
-   Imprimer.  
  
-   Rechercher et remplacer.  
  
 Étant donné que classe `CEditView` dérive de la classe `CView`, objets de la classe `CEditView` peut être utilisé avec des documents et des modèles de document.  
  
 Chaque `CEditView` texte du contrôle est conservé dans son propre objet de la mémoire globale. Votre application peut avoir un nombre quelconque de `CEditView` objets.  
  
 Créer des objets de type `CEditView` si vous voulez une fenêtre d’édition avec les fonctionnalités répertoriées ci-dessus, ou si vous souhaitez que les fonctionnalités de l’éditeur de texte simple. A `CEditView` objet peut occuper de la zone cliente d’une fenêtre. Dériver vos propres classes de `CEditView` pour ajouter ou modifier les fonctionnalités de base, ou pour déclarer des classes qui peuvent être ajoutés à un modèle de document.  
  
 L’implémentation par défaut de la classe `CEditView` gère les commandes suivantes : **ID_EDIT_SELECT_ALL**, **ID_EDIT_FIND**, **ID_EDIT_REPLACE**, **ID_EDIT_REPEAT**, et **ID_FILE_PRINT**.  
  
 La limite de caractères par défaut pour `CEditView` est (1024 \* 1024-1 = 1048575). Cela peut être modifiée en appelant le **EM_LIMITTEXT** contrôle d’édition de fonction de l’objet sous-jacent. Toutefois, les limites sont différentes selon le système d’exploitation et le type de modifier le contrôle (unique ou multiligne). Pour plus d’informations sur ces limites, consultez [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Pour modifier cette limite dans votre contrôle, substituez le `OnCreate()` fonctionner pour votre `CEditView` de classe et d’insérer la ligne de code suivante :  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 Objets de type `CEditView` (ou des types dérivés de `CEditView`) présentent les limitations suivantes :  
  
- `CEditView` n’implémente pas la valeur true ce que vous voyez est ce que vous obtenez (WYSIWYG) modification. S’il existe un choix entre la lisibilité à l’écran et imprimé correspondant, `CEditView` opte pour une meilleure lisibilité de l’écran.  
  
- `CEditView` pouvez afficher du texte dans uniquement une police unique. Aucune mise en forme du caractère spécial n’est pris en charge. Consultez la classe [CRichEditView](../../mfc/reference/cricheditview-class.md) pour davantage de fonctionnalités.  
  
-   La quantité de texte un `CEditView` peut contenir est limité. Les limites sont les mêmes que pour les `CEdit` contrôle.  
  
 Pour plus d’informations sur `CEditView`, consultez [dérivées les Classes d’affichage disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxext.h  
  
##  <a name="ceditview"></a>  CEditView::CEditView  
 Construit un objet de type `CEditView`.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit l’objet, vous devez appeler la [CWnd::Create](../../mfc/reference/cwnd-class.md#create) fonction avant que le contrôle d’édition est utilisé. Si vous dérivez une classe de `CEditView` et l’ajouter au modèle en utilisant `CWinApp::AddDocTemplate`, le framework appelle deux ce constructeur et la **créer** (fonction).  
  
##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault  
 Contient le style par défaut de la `CEditView` objet.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>Notes  
 Passer ce membre statique en tant que le `dwStyle` paramètre de la **créer** fonction pour obtenir le style par défaut pour le `CEditView` objet.  
  
##  <a name="findtext"></a>  CEditView::FindText  
 Appelez le `FindText` fonction pour rechercher la `CEditView` mémoire tampon de texte de l’objet.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFind`  
 Le texte à rechercher.  
  
 `bNext`  
 Spécifie la direction de la recherche. Si **TRUE**, la direction de recherche est vers la fin de la mémoire tampon. Si **FALSE**, le sens de la recherche est vers le début de la mémoire tampon.  
  
 `bCase`  
 Spécifie si la recherche respecte la casse. Si **TRUE**, la recherche respecte la casse. Si **FALSE**, la recherche n’est pas la casse.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le texte recherché est trouvé ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction recherche le texte dans la mémoire tampon pour le texte spécifié par `lpszFind`, en commençant à la sélection actuelle, dans le sens spécifié par `bNext`et avec respect de la casse spécifié par `bCase`. Si le texte est trouvé, il définit la sélection sur le texte recherché et retourne une valeur différente de zéro. Si le texte est introuvable, la fonction retourne 0.  
  
 Normalement, vous n’avez pas besoin d’appeler le `FindText` fonction sauf si vous substituez `OnFindNext`, qui appelle `FindText`.  
  
##  <a name="getbufferlength"></a>  CEditView::GetBufferLength  
 Appelez cette fonction membre pour obtenir le nombre de caractères actuellement dans le tampon du contrôle d’édition, non compris le terminateur null.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur de la chaîne dans la mémoire tampon.  
  
##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl  
 Appelez `GetEditCtrl` pour obtenir une référence au contrôle d’édition utilisé par le mode édition.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à un objet `CEdit`.  
  
### <a name="remarks"></a>Notes  
 Ce contrôle est de type [CEdit](../../mfc/reference/cedit-class.md), de sorte que vous pouvez manipuler le contrôle d’édition Windows directement à l’aide de la `CEdit` fonctions membres.  
  
> [!CAUTION]
>  À l’aide de la `CEdit` peut le modifier modifier l’état de fenêtre sous-jacent du contrôle de l’objet. Par exemple, vous ne devez pas modifier les paramètres de tabulation à l’aide de la [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) fonctionne car `CEditView` met en cache ces paramètres pour une utilisation dans le contrôle d’édition et l’impression. Au lieu de cela, utilisez [CEditView::SetTabStops](#settabstops).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont  
 Appelez `GetPrinterFont` pour obtenir un pointeur vers un [CFont](../../mfc/reference/cfont-class.md) objet qui décrit la police d’imprimante en cours.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CFont` objet qui spécifie la police actuelle de l’imprimante ; **NULL** si la police d’imprimante n’a pas été définie. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.  
  
### <a name="remarks"></a>Notes  
 Si la police d’imprimante n'a pas été définie, la valeur par défaut de l’impression du comportement de la `CEditView` classe consiste à imprimer à l’aide de la même police utilisée pour l’affichage.  
  
 Utilisez cette fonction pour déterminer la police d’imprimante en cours. Si elle n’est pas la police d’imprimante de votre choix, utilisez [CEditView::SetPrinterFont](#setprinterfont) pour le modifier.  
  
##  <a name="getselectedtext"></a>  CEditView::GetSelectedText  
 Appelez `GetSelectedText` pour copier le texte sélectionné dans un `CString` objet, jusqu'à la fin de la sélection ou le caractère qui précède le premier caractère de retour chariot dans la sélection.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `strResult`  
 Une référence à la `CString` objet qui doit recevoir le texte sélectionné.  
  
##  <a name="lockbuffer"></a>  CEditView::LockBuffer  
 Appelez cette fonction membre pour obtenir un pointeur vers la mémoire tampon. La mémoire tampon ne doit pas être modifiée.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la mémoire tampon du contrôle d’édition.  
  
##  <a name="onfindnext"></a>  CEditView::OnFindNext  
 Recherche dans la mémoire tampon pour le texte spécifié par le texte `lpszFind`, dans le sens spécifié par `bNext`, avec respect de la casse spécifié par `bCase`.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFind`  
 Le texte à rechercher.  
  
 `bNext`  
 Spécifie la direction de la recherche. Si **TRUE**, la direction de recherche est vers la fin de la mémoire tampon. Si **FALSE**, le sens de la recherche est vers le début de la mémoire tampon.  
  
 `bCase`  
 Spécifie si la recherche respecte la casse. Si **TRUE**, la recherche respecte la casse. Si **FALSE**, la recherche n’est pas la casse.  
  
### <a name="remarks"></a>Notes  
 La recherche commence au début de la sélection actuelle et s’effectue via un appel à [FindText](#findtext). Dans l’implémentation par défaut, `OnFindNext` appelle [OnTextNotFound](#ontextnotfound) si le texte est introuvable.  
  
 Substituer `OnFindNext` modifier la manière dont un `CEditView`-objet dérivé recherche du texte. `CEditView` appels `OnFindNext` quand l’utilisateur choisit le bouton suivant dans la boîte de dialogue de recherche standard.  
  
##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll  
 `CEditView` appels `OnReplaceAll` lorsque l’utilisateur sélectionne le bouton Remplacer tout dans la boîte de dialogue Remplacer standard.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFind`  
 Le texte à rechercher.  
  
 `lpszReplace`  
 Texte à remplacer le texte recherché.  
  
 `bCase`  
 Spécifie si recherche respecte la casse. Si **TRUE**, la recherche respecte la casse. Si **FALSE**, la recherche n’est pas la casse.  
  
### <a name="remarks"></a>Notes  
 `OnReplaceAll` recherche dans la mémoire tampon pour le texte spécifié par le texte `lpszFind`, avec respect de la casse spécifié par `bCase`. La recherche commence au début de la sélection actuelle. Chaque fois que le texte de recherche est trouvé, cette fonction remplace cette occurrence du texte avec le texte spécifié par `lpszReplace`. La recherche s’effectue via un appel à [FindText](#findtext). Dans l’implémentation par défaut, [OnTextNotFound](#ontextnotfound) est appelée si le texte est introuvable.  
  
 Si la sélection actuelle ne correspond pas à `lpszFind`, la sélection est mise à jour pour la première occurrence du texte spécifié par `lpszFind` et une opération de remplacement n’est pas effectuée. Cela permet à l’utilisateur confirmer qu’il s’agit qu’ils souhaitent faire lorsque la sélection ne correspond pas à du texte à remplacer.  
  
 Substituer `OnReplaceAll` modifier la manière dont un `CEditView`-objet dérivé remplace le texte.  
  
##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel  
 `CEditView` appels `OnReplaceSel` lorsque l’utilisateur sélectionne le bouton Remplacer dans la boîte de dialogue Remplacer standard.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFind`  
 Le texte à rechercher.  
  
 `bNext`  
 Spécifie la direction de la recherche. Si **TRUE**, la direction de recherche est vers la fin de la mémoire tampon. Si **FALSE**, le sens de la recherche est vers le début de la mémoire tampon.  
  
 `bCase`  
 Spécifie si la recherche respecte la casse. Si **TRUE**, la recherche respecte la casse. Si **FALSE**, la recherche n’est pas la casse.  
  
 `lpszReplace`  
 Texte à remplacer le texte trouvé.  
  
### <a name="remarks"></a>Notes  
 Après le remplacement de la sélection, cette fonction recherche le texte dans la mémoire tampon pour l’occurrence suivante du texte spécifié par `lpszFind`, dans le sens spécifié par `bNext`, avec respect de la casse spécifié par `bCase`. La recherche s’effectue via un appel à [FindText](#findtext). Si le texte est introuvable, [OnTextNotFound](#ontextnotfound) est appelée.  
  
 Substituer `OnReplaceSel` modifier la manière dont un `CEditView`-objet dérivé remplace le texte sélectionné.  
  
##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound  
 Remplacez cette fonction pour modifier l’implémentation par défaut, qui appelle la fonction Windows **MessageBeep**.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFind`  
 Le texte à rechercher.  
  
##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect  
 Appelez `PrintInsideRect` à imprimer du texte dans le rectangle spécifié par *rectLayout*.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointeur vers le contexte de périphérique d’imprimante.  
  
 *rectLayout*  
 Référence à un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou [Rect, structure](../../mfc/reference/rect-structure1.md) spécifiant le rectangle dans lequel le texte doit être restitué.  
  
 `nIndexStart`  
 Index dans la mémoire tampon du premier caractère à restituer.  
  
 `nIndexStop`  
 Index dans la mémoire tampon du caractère suivant le dernier caractère à restituer.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du caractère suivant à être imprimée (autrement dit, le caractère suivant le dernier caractère de rendu).  
  
### <a name="remarks"></a>Notes  
 Si le `CEditView` contrôle n’a pas le style **ES_AUTOHSCROLL**, le texte est encapsulé dans le rectangle de rendu. Si le contrôle a le style **ES_AUTOHSCROLL**, le texte est tronqué sur le bord droit du rectangle.  
  
 Le **rect.bottom** élément de la *rectLayout* objet est modifié afin que les dimensions du rectangle définissent la partie du rectangle qui est occupé par le texte d’origine.  
  
##  <a name="serializeraw"></a>  CEditView::SerializeRaw  
 Appelez `SerializeRaw` d’avoir un `CArchive` de l’objet en lecture ou d’écrire le texte le `CEditView` objet dans un fichier texte.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 `ar`  
 Référence à la `CArchive` objet qui stocke le texte sérialisé.  
  
### <a name="remarks"></a>Notes  
 `SerializeRaw` diffère de `CEditView`d’implémentation interne de `Serialize` dans la mesure où il lit et écrit le texte uniquement, sans faire précéder les données de la description de l’objet.  
  
##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont  
 Appelez `SetPrinterFont` pour définir la police d’imprimante pour la police spécifiée par `pFont`.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFont`  
 Un pointeur vers un objet de type `CFont`. Si **NULL**, la police utilisée pour l’impression est basée sur la police d’affichage.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez que votre vue à toujours utiliser une police particulière pour l’impression, incluez un appel à `SetPrinterFont` dans votre classe `OnPreparePrinting` (fonction). Cette fonction virtuelle est appelée avant l’impression, afin de la modification de la police a lieu avant le contenu est imprimé.  
  
##  <a name="settabstops"></a>  CEditView::SetTabStops  
 Appelez cette fonction pour définir les taquets de tabulation utilisés pour l’affichage et l’impression.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>Paramètres  
 `nTabStops`  
 Largeur de chaque taquet de tabulation, en unités de boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Uniquement une largeur taquet de tabulation unique est prise en charge. ( `CEdit` objets prennent en charge plusieurs largeurs d’onglet.) Largeurs sont en unités de boîte de dialogue, qui correspondent à un quart de la largeur de caractère moyenne (selon les caractères majuscules et minuscules alphabétiques uniquement) de la police utilisée au moment de l’impression ou l’affichage. Vous ne devez pas utiliser `CEdit::SetTabStops` car `CEditView` doit mettre en cache la valeur taquet de tabulation.  
  
 Cette fonction modifie uniquement les onglets de l’objet pour lequel il est appelé. Pour modifier l’onglet s’arrête pour chaque `CEditView` de l’objet dans votre application, l’appel de chaque objet `SetTabStops` (fonction).  
  
### <a name="example"></a>Exemple  
 Ce fragment de code définit les taquets de tabulation dans le contrôle à chaque quatrième caractère en mesurant avec soin de la police, que le contrôle utilise.  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer  
 Appelez cette fonction membre pour déverrouiller la mémoire tampon.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>Notes  
 Appelez `UnlockBuffer` une fois que vous avez fini d’utiliser le pointeur retourné par [LockBuffer](#lockbuffer).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Classe de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CDocument (classe)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [Classe de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
