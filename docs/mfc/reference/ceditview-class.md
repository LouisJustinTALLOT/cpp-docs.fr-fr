---
description: 'En savoir plus sur : classe CEditView'
title: Classe CEditView
ms.date: 11/04/2016
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
ms.openlocfilehash: b83b83b90fe530d2615a507d80e2af771397d286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184710"
---
# <a name="ceditview-class"></a>Classe CEditView

Type de classe d'affichage qui fournit les fonctionnalités d'un contrôle d'édition Windows et peut être utilisé pour implémenter des fonctionnalités d'éditeur de texte simples.

## <a name="syntax"></a>Syntaxe

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CEditView :: CEditView](#ceditview)|Construit un objet de type `CEditView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CEditView :: FindText](#findtext)|Recherche une chaîne dans le texte.|
|[CEditView :: GetBufferLength](#getbufferlength)|Obtient la longueur de la mémoire tampon de caractères.|
|[CEditView :: GetEditCtrl](#geteditctrl)|Fournit l’accès à la `CEdit` partie d’un `CEditView` objet (le contrôle d’édition Windows).|
|[CEditView :: GetPrinterFont](#getprinterfont)|Récupère la police actuelle de l’imprimante.|
|[CEditView :: GetSelectedText](#getselectedtext)|Récupère la sélection de texte actuelle.|
|[CEditView :: LockBuffer](#lockbuffer)|Verrouille la mémoire tampon.|
|[CEditView ::P rintInsideRect](#printinsiderect)|Restitue le texte à l’intérieur d’un rectangle donné.|
|[CEditView :: SerializeRaw](#serializeraw)|Sérialise un `CEditView` objet sur le disque sous forme de texte brut.|
|[CEditView :: SetPrinterFont](#setprinterfont)|Définit une nouvelle police d’imprimante.|
|[CEditView :: SetTabStops](#settabstops)|Définit des taquets de tabulation pour l’affichage à l’écran et l’impression.|
|[CEditView :: UnlockBuffer](#unlockbuffer)|Déverrouille la mémoire tampon.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CEditView :: OnFindNext](#onfindnext)|Recherche l’occurrence suivante d’une chaîne de texte.|
|[CEditView :: OnReplaceAll](#onreplaceall)|Remplace toutes les occurrences d’une chaîne donnée par une nouvelle chaîne.|
|[CEditView :: OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|
|[CEditView :: OnTextNotFound](#ontextnotfound)|Appelé lorsqu’une opération de recherche ne parvient pas à faire correspondre un texte supplémentaire.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CEditView ::d wStyleDefault](#dwstyledefault)|Style par défaut pour les objets de type `CEditView` .|

## <a name="remarks"></a>Notes

La `CEditView` classe fournit les fonctions supplémentaires suivantes :

- Impression.

- Rechercher et remplacer.

Étant donné que `CEditView` la classe est une dérivée de la classe `CView` , les objets de la classe `CEditView` peuvent être utilisés avec des documents et des modèles de document.

`CEditView`Le texte de chaque contrôle est conservé dans son propre objet de mémoire globale. Votre application peut avoir un nombre quelconque d' `CEditView` objets.

Créer des objets de type `CEditView` si vous souhaitez une fenêtre d’édition avec la fonctionnalité ajoutée indiquée ci-dessus, ou si vous souhaitez une fonctionnalité d’éditeur de texte simple. Un `CEditView` objet peut occuper la totalité de la zone cliente d’une fenêtre. Dérivez vos propres classes à partir de `CEditView` pour ajouter ou modifier les fonctionnalités de base, ou pour déclarer des classes qui peuvent être ajoutées à un modèle de document.

L’implémentation par défaut de `CEditView` la classe gère les commandes suivantes : ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT et ID_FILE_PRINT.

La limite de caractères par défaut pour `CEditView` est (1024 \* 1024-1 = 1048575). Cela peut être modifié en appelant la fonction EM_LIMITTEXT du contrôle d’édition sous-jacent. Toutefois, les limites sont différentes selon le système d’exploitation et le type de contrôle d’édition (simple ou multiligne). Pour plus d’informations sur ces limites, consultez [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Pour modifier cette limite dans votre contrôle, remplacez la `OnCreate()` fonction de votre `CEditView` classe et insérez la ligne de code suivante :

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Les objets de type `CEditView` (ou de types dérivés de `CEditView` ) présentent les limitations suivantes :

- `CEditView` n’implémente pas true ce que vous voyez est la modification (WYSIWYG) de ce que vous obtenez. Lorsqu’il existe un choix entre la lisibilité à l’écran et la sortie imprimée correspondante, `CEditView` opte pour la lisibilité de l’écran.

- `CEditView` peut afficher du texte dans une seule police. Aucune mise en forme de caractères spéciaux n’est prise en charge. Consultez la classe [CRichEditView](../../mfc/reference/cricheditview-class.md) pour obtenir des fonctionnalités plus avancées.

- La quantité de texte qu’un `CEditView` peut contenir est limitée. Les limites sont les mêmes que pour le `CEdit` contrôle.

Pour plus d’informations sur `CEditView` , consultez [classes de vue dérivées disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="ceditviewceditview"></a><a name="ceditview"></a> CEditView :: CEditView

Construit un objet de type `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Notes

Après avoir construit l’objet, vous devez appeler la fonction [CWnd :: Create](../../mfc/reference/cwnd-class.md#create) avant d’utiliser le contrôle d’édition. Si vous dérivez une classe de `CEditView` et l’ajoutez au modèle à l’aide de `CWinApp::AddDocTemplate` , le Framework appelle à la fois ce constructeur et la `Create` fonction.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a> CEditView ::d wStyleDefault

Contient le style par défaut de l' `CEditView` objet.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Notes

Transmettez ce membre static en tant que paramètre *dwStyle* de la `Create` fonction pour obtenir le style par défaut de l' `CEditView` objet.

## <a name="ceditviewfindtext"></a><a name="findtext"></a> CEditView :: FindText

Appelez la `FindText` fonction pour rechercher la `CEditView` mémoire tampon de texte de l’objet.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à rechercher.

*bNext*<br/>
Spécifie la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSe, le sens de la recherche est dirigé vers le début de la mémoire tampon.

*bCase*<br/>
Spécifie si la recherche respecte la casse. Si la valeur est TRUE, la recherche respecte la casse. Si la valeur est FALSe, la recherche ne respecte pas la casse.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le texte recherché est trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction recherche le texte spécifié par *lpszFind* dans le texte de la mémoire tampon, en commençant à la sélection actuelle, dans la direction spécifiée par *Bnext*, et avec le respect de la casse spécifié par *bCase*. Si le texte est trouvé, il définit la sélection sur le texte trouvé et retourne une valeur différente de zéro. Si le texte est introuvable, la fonction retourne 0.

Normalement, vous n’avez pas besoin d’appeler la `FindText` fonction, sauf si vous substituez `OnFindNext` , qui appelle `FindText` .

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a> CEditView :: GetBufferLength

Appelez cette fonction membre pour obtenir le nombre de caractères actuellement dans la mémoire tampon du contrôle d’édition, à l’exclusion de la marque de fin null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur de la chaîne dans la mémoire tampon.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a> CEditView :: GetEditCtrl

Appelez `GetEditCtrl` pour obtenir une référence au contrôle d’édition utilisé par la vue Edit.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à un objet `CEdit`.

### <a name="remarks"></a>Notes

Ce contrôle étant de type [CEdit](../../mfc/reference/cedit-class.md), vous pouvez manipuler le contrôle d’édition Windows directement à l’aide des `CEdit` fonctions membres.

> [!CAUTION]
> L’utilisation `CEdit` de l’objet peut modifier l’état du contrôle d’édition Windows sous-jacent. Par exemple, vous ne devez pas modifier les paramètres de tabulation à l’aide de la fonction [CEdit :: SetTabStops](../../mfc/reference/cedit-class.md#settabstops) car `CEditView` met en cache ces paramètres pour les utiliser dans le contrôle d’édition et dans l’impression. Au lieu de cela, utilisez [CEditView :: SetTabStops](#settabstops).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a> CEditView :: GetPrinterFont

Appelez `GetPrinterFont` pour obtenir un pointeur vers un objet [CFont](../../mfc/reference/cfont-class.md) qui décrit la police d’imprimante actuelle.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un `CFont` objet qui spécifie la police actuelle de l’imprimante ; NULL si la police de l’imprimante n’a pas été définie. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.

### <a name="remarks"></a>Notes

Si la police de l’imprimante n’a pas été définie, le comportement d’impression par défaut de la `CEditView` classe consiste à imprimer à l’aide de la même police que celle utilisée pour l’affichage.

Utilisez cette fonction pour déterminer la police actuelle de l’imprimante. S’il ne s’agit pas de la police d’imprimante souhaitée, utilisez [CEditView :: SetPrinterFont](#setprinterfont) pour le modifier.

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a> CEditView :: GetSelectedText

Appelez `GetSelectedText` pour copier le texte sélectionné dans un `CString` objet, jusqu’à la fin de la sélection ou le caractère qui précède le premier caractère de retour chariot dans la sélection.

```cpp
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Paramètres

*strResult*<br/>
Référence à l' `CString` objet qui doit recevoir le texte sélectionné.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a> CEditView :: LockBuffer

Appelez cette fonction membre pour obtenir un pointeur vers la mémoire tampon. La mémoire tampon ne doit pas être modifiée.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la mémoire tampon du contrôle d’édition.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a> CEditView :: OnFindNext

Recherche le texte spécifié par *lpszFind* dans le texte de la mémoire tampon, dans la direction spécifiée par *Bnext*, avec le respect de la casse spécifié par *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à rechercher.

*bNext*<br/>
Spécifie la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSe, le sens de la recherche est dirigé vers le début de la mémoire tampon.

*bCase*<br/>
Spécifie si la recherche respecte la casse. Si la valeur est TRUE, la recherche respecte la casse. Si la valeur est FALSe, la recherche ne respecte pas la casse.

### <a name="remarks"></a>Notes

La recherche commence au début de la sélection actuelle et est accomplie par un appel à [TexteCherché](#findtext). Dans l’implémentation par défaut, `OnFindNext` appelle [OnTextNotFound](#ontextnotfound) si le texte est introuvable.

Substituez `OnFindNext` pour modifier la façon dont un `CEditView` objet dérivé de recherche du texte. `CEditView` appelle `OnFindNext` lorsque l’utilisateur clique sur le bouton suivant de la boîte de dialogue Rechercher standard.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a> CEditView :: OnReplaceAll

`CEditView` appelle `OnReplaceAll` lorsque l’utilisateur sélectionne le bouton remplacer tout dans la boîte de dialogue remplacer standard.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à rechercher.

*lpszReplace*<br/>
Texte pour remplacer le texte recherché.

*bCase*<br/>
Spécifie si la recherche respecte la casse. Si la valeur est TRUE, la recherche respecte la casse. Si la valeur est FALSe, la recherche ne respecte pas la casse.

### <a name="remarks"></a>Notes

`OnReplaceAll` recherche le texte spécifié par *lpszFind* dans le texte de la mémoire tampon, avec le respect de la casse spécifié par *bCase*. La recherche commence au début de la sélection actuelle. Chaque fois que le texte recherché est trouvé, cette fonction remplace cette occurrence du texte par le texte spécifié par *lpszReplace*. La recherche s’effectue à l’aide d’un appel à [TexteCherché](#findtext). Dans l’implémentation par défaut, [OnTextNotFound](#ontextnotfound) est appelé si le texte est introuvable.

Si la sélection actuelle ne correspond pas à *lpszFind*, la sélection est mise à jour en fonction de la première occurrence du texte spécifié par *lpszFind* et un remplacement n’est pas effectué. Cela permet à l’utilisateur de confirmer que c’est ce qu’il souhaite faire lorsque la sélection ne correspond pas au texte à remplacer.

Substituez `OnReplaceAll` pour modifier la façon dont un `CEditView` objet dérivé de remplace le texte.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a> CEditView :: OnReplaceSel

`CEditView` appelle `OnReplaceSel` lorsque l’utilisateur sélectionne le bouton remplacer dans la boîte de dialogue remplacer standard.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à rechercher.

*bNext*<br/>
Spécifie la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSe, le sens de la recherche est dirigé vers le début de la mémoire tampon.

*bCase*<br/>
Spécifie si la recherche respecte la casse. Si la valeur est TRUE, la recherche respecte la casse. Si la valeur est FALSe, la recherche ne respecte pas la casse.

*lpszReplace*<br/>
Texte pour remplacer le texte trouvé.

### <a name="remarks"></a>Notes

Après avoir remplacé la sélection, cette fonction recherche dans le texte de la mémoire tampon l’occurrence suivante du texte spécifié par *lpszFind*, dans la direction spécifiée par *Bnext*, avec le respect de la casse spécifié par *bCase*. La recherche s’effectue à l’aide d’un appel à [TexteCherché](#findtext). Si le texte est introuvable, [OnTextNotFound](#ontextnotfound) est appelé.

Substituez `OnReplaceSel` pour modifier la façon dont un `CEditView` objet dérivé de remplace le texte sélectionné.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a> CEditView :: OnTextNotFound

Substituez cette fonction pour modifier l’implémentation par défaut, qui appelle la fonction Windows `MessageBeep` .

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à rechercher.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a> CEditView ::P rintInsideRect

Appelez `PrintInsideRect` pour imprimer du texte dans le rectangle spécifié par *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers le contexte de périphérique d’impression.

*rectLayout*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou à une [structure Rect](/windows/win32/api/windef/ns-windef-rect) spécifiant le rectangle dans lequel le texte doit être rendu.

*nIndexStart*<br/>
Index dans la mémoire tampon du premier caractère à restituer.

*nIndexStop*<br/>
Index dans la mémoire tampon du caractère qui suit le dernier caractère à restituer.

### <a name="return-value"></a>Valeur renvoyée

Index du caractère suivant à imprimer (autrement dit, le caractère qui suit le dernier rendu du caractère).

### <a name="remarks"></a>Notes

Si le `CEditView` contrôle n’a pas le style ES_AUTOHSCROLL, le texte est renvoyé à la ligne dans le rectangle de rendu. Si le style du contrôle est ES_AUTOHSCROLL, le texte est coupé au bord droit du rectangle.

L' `rect.bottom` élément de l’objet *rectLayout* est modifié de sorte que les dimensions du rectangle définissent la partie du rectangle d’origine occupée par le texte.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a> CEditView :: SerializeRaw

Appelez `SerializeRaw` pour que `CArchive` l’objet ait lu ou écrit le texte de l' `CEditView` objet dans un fichier texte.

```cpp
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
Référence à l' `CArchive` objet qui stocke le texte sérialisé.

### <a name="remarks"></a>Notes

`SerializeRaw` diffère de l' `CEditView` implémentation interne de `Serialize` en ce qu’il lit et écrit uniquement le texte, sans les données de description d’objet précédentes.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a> CEditView :: SetPrinterFont

Appelez `SetPrinterFont` pour définir la police de l’imprimante avec la police spécifiée par *pFont*.

```cpp
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Pointeur vers un objet de type `CFont` . Si la valeur est NULL, la police utilisée pour l’impression est basée sur la police d’affichage.

### <a name="remarks"></a>Notes

Si vous souhaitez que votre vue utilise toujours une police particulière pour l’impression, incluez un appel à `SetPrinterFont` dans la fonction de votre classe `OnPreparePrinting` . Cette fonction virtuelle est appelée avant l’impression, donc la modification de la police a lieu avant l’impression du contenu de la vue.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a> CEditView :: SetTabStops

Appelez cette fonction pour définir les taquets de tabulation utilisés pour l’affichage et l’impression.

```cpp
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Paramètres

*nTabStops*<br/>
Largeur de chaque taquet de tabulation, en unités de boîte de dialogue.

### <a name="remarks"></a>Notes

Seule une largeur de taquet de tabulation unique est prise en charge. (les `CEdit` objets prennent en charge plusieurs largeurs d’onglets.) Les largeurs sont en unités de boîte de dialogue, qui sont égales à un quart de la largeur moyenne des caractères (en fonction des caractères alphabétiques majuscules et minuscules uniquement) de la police utilisée au moment de l’impression ou de l’affichage. Vous ne devez pas utiliser `CEdit::SetTabStops` car `CEditView` doit mettre en cache la valeur d’arrêt de tabulation.

Cette fonction modifie uniquement les onglets de l’objet pour lequel elle est appelée. Pour modifier les taquets de tabulation pour chaque `CEditView` objet de votre application, appelez la fonction de chaque objet `SetTabStops` .

### <a name="example"></a>Exemple

Ce fragment de code définit les taquets de tabulation dans le contrôle à chaque quatrième caractère en mesurant minutieusement la police utilisée par le contrôle.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a> CEditView :: UnlockBuffer

Appelez cette fonction membre pour déverrouiller la mémoire tampon.

```cpp
void UnlockBuffer() const;
```

### <a name="remarks"></a>Notes

Appelez `UnlockBuffer` une fois que vous avez fini d’utiliser le pointeur retourné par [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Voir aussi

[Exemple MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView (classe)](../../mfc/reference/cricheditview-class.md)
