---
title: CEditView, classe
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
ms.openlocfilehash: 33b5975eea534eeaf308f73b5ca7fca2cd76787f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753198"
---
# <a name="ceditview-class"></a>CEditView, classe

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
|[CEditView::GetBufferLength](#getbufferlength)|Obtient la longueur du tampon de caractère.|
|[CEditView::GetEditCtrl](#geteditctrl)|Donne accès `CEdit` à la `CEditView` partie d’un objet (le contrôle de modification Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Récupère la police d’imprimante actuelle.|
|[CEditView::GetSelectedText](#getselectedtext)|Récupère la sélection de texte en cours.|
|[CEditView::LockBuffer](#lockbuffer)|Verrouille le tampon.|
|[CEditView::PrintInsideRect](#printinsiderect)|Rend le texte à l’intérieur d’un rectangle donné.|
|[CEditView::SerializeRaw](#serializeraw)|Sérialise `CEditView` un objet au disque sous forme de texte brut.|
|[CEditView::SetPrinterFont](#setprinterfont)|Définit une nouvelle police d’imprimante.|
|[CEditView::SetTabStops](#settabstops)|Définit les arrêts d’onglet pour l’affichage de l’écran et l’impression.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Débloque le tampon.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Trouve l’occurrence suivante d’une chaîne de texte.|
|[CEditView::OnReplaceAll](#onreplaceall)|Remplace tous les occurrences d’une chaîne donnée par une nouvelle chaîne.|
|[CEditView::OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Appelé quand une opération de recherche ne correspond pas à tout autre texte.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Style par défaut `CEditView`pour les objets de type .|

## <a name="remarks"></a>Notes

La `CEditView` classe fournit les fonctions supplémentaires suivantes :

- Impression.

- Trouver et remplacer.

Parce `CEditView` que la classe `CView`est un `CEditView` dérivé de classe, les objets de classe peuvent être utilisés avec des documents et des modèles de documents.

Le `CEditView` texte de chaque contrôle est conservé dans son propre objet de mémoire global. Votre application peut avoir `CEditView` n’importe quel nombre d’objets.

Créez des `CEditView` objets de type si vous voulez une fenêtre de modification avec les fonctionnalités ajoutées énumérées ci-dessus, ou si vous voulez une fonctionnalité simple d’éditeur de texte. Un `CEditView` objet peut occuper toute la zone client d’une fenêtre. Dérivez vos `CEditView` propres classes pour ajouter ou modifier la fonctionnalité de base, ou pour déclarer les classes qui peuvent être ajoutées à un modèle de document.

La mise en `CEditView` œuvre par défaut de la classe gère les commandes suivantes : ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT et ID_FILE_PRINT.

La limite de `CEditView` caractère par défaut \* est (1024 1024 - 1 - 1048575). Cela peut être modifié en appelant la fonction EM_LIMITTEXT du contrôle de modification sous-jacent. Toutefois, les limites sont différentes selon le système d’exploitation et le type de contrôle de modification (simple ou multilinré). Pour plus d’informations sur ces limites, voir [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Pour modifier cette limite dans votre `OnCreate()` contrôle, `CEditView` remplacez la fonction de votre classe et insérez la ligne de code suivante :

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Les objets `CEditView` de type (ou de types dérivés) `CEditView`ont les limites suivantes :

- `CEditView`ne met pas en œuvre vrai ce que vous voyez est ce que vous obtenez (WYSIWYG) édition. Lorsqu’il y a un choix entre la `CEditView` lisibilité à l’écran et la sortie imprimée correspondante, opte pour la lisibilité à l’écran.

- `CEditView`peut afficher du texte en une seule police. Aucun formatage spécial de caractère n’est pris en charge. Consultez la classe [CRichEditView](../../mfc/reference/cricheditview-class.md) pour de plus grandes capacités.

- La quantité de `CEditView` texte qu’un peut contenir est limitée. Les limites sont les `CEdit` mêmes que pour le contrôle.

Pour plus `CEditView`d’informations sur , voir [Les classes de vue dérivées disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView

Construit un objet de type `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Notes

Après la construction de l’objet, vous devez appeler le [CWnd: :Créer](../../mfc/reference/cwnd-class.md#create) la fonction avant que le contrôle de modification est utilisé. Si vous dérivez `CEditView` une classe et `CWinApp::AddDocTemplate`l’ajoutez au modèle à `Create` l’aide, le cadre appelle à la fois ce constructeur et la fonction.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault

Contient le style `CEditView` par défaut de l’objet.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Notes

Passez ce membre statique comme paramètre *dwStyle* de la `Create` `CEditView` fonction pour obtenir le style par défaut pour l’objet.

## <a name="ceditviewfindtext"></a><a name="findtext"></a>CEditView::FindText

Appelez `FindText` la fonction `CEditView` pour rechercher le tampon texte de l’objet.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à trouver.

*bNext (en)*<br/>
Spécifie la direction de la recherche. Si VRAI, la direction de recherche est vers la fin du tampon. Si FALSE, la direction de recherche est vers le début du tampon.

*bCase*<br/>
Précise si la fouille est sensible au cas. Si VRAI, la recherche est sensible au cas. Si FALSE, la recherche n’est pas sensible au cas.

### <a name="return-value"></a>Valeur de retour

Nonzero si le texte de recherche est trouvé; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction recherche le texte dans le tampon pour le texte spécifié par *lpszFind*, à partir de la sélection actuelle, dans la direction spécifiée par *bNext*, et avec la sensibilité du cas spécifié *par bCase*. Si le texte est trouvé, il définit la sélection au texte trouvé et renvoie une valeur non zéro. Si le texte n’est pas trouvé, la fonction renvoie 0.

Vous n’avez normalement pas `FindText` besoin d’appeler la fonction à moins que vous ne l’emportez `OnFindNext`, qui appelle `FindText`.

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength

Appelez cette fonction de membre pour obtenir le nombre de caractères actuellement dans le tampon du contrôle de modification, sans compter le terminateur nul.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur de la chaîne dans le tampon.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl

Appelez `GetEditCtrl` pour obtenir une référence au contrôle de modification utilisé par la vue de modification.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à un objet `CEdit`.

### <a name="remarks"></a>Notes

Ce contrôle est du type [CEdit](../../mfc/reference/cedit-class.md), de sorte `CEdit` que vous pouvez manipuler le contrôle de modification Windows directement en utilisant les fonctions du membre.

> [!CAUTION]
> L’utilisation de l’objet `CEdit` peut modifier l’état du contrôle de modification Windows sous-jacent. Par exemple, vous ne devez pas modifier les paramètres de l’onglet `CEditView` à l’aide de la fonction [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) car cache ces paramètres pour une utilisation à la fois dans le contrôle de modification et dans l’impression. Utilisez [plutôt CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont

Appelez `GetPrinterFont` pour obtenir un pointeur à un objet [CFont](../../mfc/reference/cfont-class.md) qui décrit la police d’imprimante actuelle.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFont` à un objet qui spécifie la police d’imprimante actuelle; NULL si la police d’imprimante n’a pas été réglée. Le pointeur peut être temporaire et ne doit pas être stocké pour une utilisation ultérieure.

### <a name="remarks"></a>Notes

Si la police d’imprimante n’a pas `CEditView` été définie, le comportement d’impression par défaut de la classe est d’imprimer à l’aide de la même police utilisée pour l’affichage.

Utilisez cette fonction pour déterminer la police d’imprimante actuelle. Si ce n’est pas la police d’imprimante désirée, utilisez [CEditView::SetPrinterFont](#setprinterfont) pour la modifier.

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText

Appelez `GetSelectedText` pour copier le `CString` texte sélectionné dans un objet, jusqu’à la fin de la sélection ou le personnage précédant le premier personnage de transport-retour dans la sélection.

```cpp
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Paramètres

*strResult*<br/>
Une référence `CString` à l’objet qui doit recevoir le texte sélectionné.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer

Appelez cette fonction de membre pour obtenir un pointeur au tampon. Le tampon ne doit pas être modifié.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le tampon du contrôle de modification.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>CEditView::OnFindNext

Recherche le texte dans le tampon pour le texte spécifié par *lpszFind*, dans la direction spécifiée par *bNext*, avec la sensibilité du cas spécifié *par bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à trouver.

*bNext (en)*<br/>
Spécifie la direction de la recherche. Si VRAI, la direction de recherche est vers la fin du tampon. Si FALSE, la direction de recherche est vers le début du tampon.

*bCase*<br/>
Précise si la fouille est sensible au cas. Si VRAI, la recherche est sensible au cas. Si FALSE, la recherche n’est pas sensible au cas.

### <a name="remarks"></a>Notes

La recherche commence au début de la sélection actuelle et se fait par un appel à [FindText](#findtext). Dans la implémentation par défaut, `OnFindNext` appelle [OnTextNotFound](#ontextnotfound) si le texte n’est pas trouvé.

Remplacer `OnFindNext` pour modifier la `CEditView`façon dont un objet dérivé recherche le texte. `CEditView`appelle `OnFindNext` lorsque l’utilisateur choisit le bouton Trouver ensuite dans la boîte de dialogue Localiser standard.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>CEditView::OnReplaceAll

`CEditView`appelle `OnReplaceAll` lorsque l’utilisateur sélectionne le bouton Remplacer tous dans la boîte de dialogue remplacez standard.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à trouver.

*lpszReplace*<br/>
Le texte pour remplacer le texte de recherche.

*bCase*<br/>
Précise si la fouille est sensible aux cas. Si VRAI, la recherche est sensible au cas. Si FALSE, la recherche n’est pas sensible au cas.

### <a name="remarks"></a>Notes

`OnReplaceAll`recherche le texte dans le tampon pour le texte spécifié par *lpszFind*, avec la sensibilité de cas spécifiée par *bCase*. La recherche commence au début de la sélection actuelle. Chaque fois que le texte de recherche est trouvé, cette fonction remplace cette occurrence du texte par le texte spécifié par *lpszReplace*. La recherche est effectuée par un appel à [FindText](#findtext). Dans la implémentation par défaut, [OnTextNotFound](#ontextnotfound) est appelé si le texte n’est pas trouvé.

Si la sélection actuelle ne correspond pas *lpszFind*, la sélection est mise à jour à la première occurrence du texte spécifié par *lpszFind* et un remplacement n’est pas effectué. Cela permet à l’utilisateur de confirmer que c’est ce qu’il veut faire lorsque la sélection ne correspond pas au texte à remplacer.

Remplacer `OnReplaceAll` pour modifier la `CEditView`façon dont un objet dérivé remplace le texte.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel

`CEditView`appelle `OnReplaceSel` lorsque l’utilisateur sélectionne le bouton Remplacer dans la boîte de dialogue remplacez standard.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à trouver.

*bNext (en)*<br/>
Spécifie la direction de la recherche. Si VRAI, la direction de recherche est vers la fin du tampon. Si FALSE, la direction de recherche est vers le début du tampon.

*bCase*<br/>
Précise si la fouille est sensible au cas. Si VRAI, la recherche est sensible au cas. Si FALSE, la recherche n’est pas sensible au cas.

*lpszReplace*<br/>
Le texte pour remplacer le texte trouvé.

### <a name="remarks"></a>Notes

Après avoir remplacé la sélection, cette fonction recherche le texte dans le tampon pour la prochaine occurrence du texte spécifié par *lpszFind*, dans la direction spécifiée par *bNext*, avec la sensibilité du cas spécifié *par bCase*. La recherche est effectuée par un appel à [FindText](#findtext). Si le texte n’est pas trouvé, [OnTextNotFound](#ontextnotfound) est appelé.

Remplacement `OnReplaceSel` pour modifier la `CEditView`façon dont un objet dérivé remplace le texte sélectionné.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CEditView::OnTextNotFound

Remplacer cette fonction pour modifier l’implémentation par défaut, qui appelle la fonction `MessageBeep`Windows .

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à trouver.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect

Appelez `PrintInsideRect` pour imprimer du texte dans le rectangle spécifié par *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur sur le contexte de l’appareil d’imprimante.

*rectLayout (rectLayout)*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou [structure RECT](/windows/win32/api/windef/ns-windef-rect) spécifiant le rectangle dans lequel le texte doit être rendu.

*nIndexStart*<br/>
Index dans le tampon du premier personnage à être rendu.

*nIndexStop*<br/>
Index dans le tampon du personnage suivant le dernier caractère à rendre.

### <a name="return-value"></a>Valeur de retour

L’index du prochain personnage à imprimer (c’est-à-dire le personnage suivant le dernier personnage rendu).

### <a name="remarks"></a>Notes

Si `CEditView` le contrôle n’a pas le style ES_AUTOHSCROLL, le texte est enveloppé dans le rectangle de rendu. Si le contrôle a le style ES_AUTOHSCROLL, le texte est coupé au bord droit du rectangle.

L’élément `rect.bottom` de *l’objet rectLayout* est modifié de sorte que les dimensions du rectangle définissent la partie du rectangle d’origine qui est occupée par le texte.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw

Appelez `SerializeRaw` pour `CArchive` faire lire ou écrire `CEditView` le texte dans l’objet d’un fichier texte.

```cpp
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
Référence à `CArchive` l’objet qui stocke le texte sérialisé.

### <a name="remarks"></a>Notes

`SerializeRaw`diffère de `CEditView`la mise `Serialize` en œuvre interne de 's en ce qu’il lit et écrit seulement le texte, sans données de description d’objet précédentes.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont

Appelez `SetPrinterFont` pour définir la police d’imprimante à la police spécifiée par *pFont*.

```cpp
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Un pointeur à `CFont`un objet de type . Si NULL, la police utilisée pour l’impression est basée sur la police d’affichage.

### <a name="remarks"></a>Notes

Si vous voulez que votre vue utilise toujours une `SetPrinterFont` police particulière pour `OnPreparePrinting` l’impression, incluez un appel dans la fonction de votre classe. Cette fonction virtuelle est appelée avant l’impression se produit, de sorte que le changement de police a lieu avant que le contenu de la vue est imprimé.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabStops

Appelez cette fonction pour définir les arrêts d’onglet utilisés pour l’affichage et l’impression.

```cpp
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Paramètres

*nTabStops (en)*<br/>
Largeur de chaque arrêt d’onglet, dans les unités de dialogue.

### <a name="remarks"></a>Notes

Seule une seule largeur d’arrêt d’onglet est prise en charge. ( `CEdit` les objets prennent en charge plusieurs largeurs d’onglet.) Les largeurs sont dans les unités de dialogue, qui égalent un quart de la largeur moyenne de caractère (basée sur les caractères alphabétique de uppercase et de minuscule seulement) de la police employée au moment de l’impression ou de l’affichage. Vous ne `CEdit::SetTabStops` devez `CEditView` pas utiliser parce qu’il faut mettre en cache la valeur de l’onglet-arrêt.

Cette fonction ne modifie que les onglets de l’objet pour lequel elle est appelée. Pour modifier les arrêts d’onglet pour chaque `CEditView` `SetTabStops` objet de votre application, appelez la fonction de chaque objet.

### <a name="example"></a>Exemple

Ce fragment de code définit l’onglet s’arrête dans le contrôle à un personnage sur quatre en mesurant soigneusement la police que le contrôle utilise.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::UnlockBuffer

Appelez cette fonction de membre pour déverrouiller le tampon.

```cpp
void UnlockBuffer() const;
```

### <a name="remarks"></a>Notes

Appelez `UnlockBuffer` après avoir terminé l’utilisation du pointeur retourné par [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Classe CRichEditView](../../mfc/reference/cricheditview-class.md)
