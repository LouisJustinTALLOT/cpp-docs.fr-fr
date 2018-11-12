---
title: CSplitButton, classe
ms.date: 11/04/2016
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: ca4899714fa336d058b2a53bcd5103c5b0c993e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547275"
---
# <a name="csplitbutton-class"></a>CSplitButton, classe

Le `CSplitButton` classe représente un contrôle bouton partagé. Le contrôle bouton partagé exécute un comportement par défaut lorsqu’un utilisateur clique sur la partie principale du bouton et affiche un menu déroulant lorsqu’un utilisateur clique sur la flèche déroulante du bouton.

## <a name="syntax"></a>Syntaxe

```
class CSplitButton : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Construit un objet `CSplitButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSplitButton::Create](#create)|Crée un contrôle bouton partagé avec des styles spécifiés et l’attache à actuel `CSplitButton` objet.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Définit le menu déroulant qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle de bouton de fractionnement actuel.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Gère la notification BCN_DROPDOWN envoyé par le système lorsqu’un utilisateur clique sur la flèche déroulante du contrôle de bouton de fractionnement actuel.|

## <a name="remarks"></a>Notes

Le `CSplitButton` classe est dérivée de la [CButton](../../mfc/reference/cbutton-class.md) classe. Le contrôle bouton partagé est un contrôle bouton dont le style est BS_SPLITBUTTON. Il affiche un menu personnalisé lorsqu’un utilisateur clique sur la flèche déroulante. Pour plus d’informations, consultez les styles BS_SPLITBUTTON et BS_DEFSPLITBUTTON [Styles de boutons](/windows/desktop/Controls/button-styles).

L’illustration suivante représente une boîte de dialogue qui contient un contrôle de pagineur et un contrôle bouton partagé (1). La flèche déroulante (2) a déjà été cliqué et le sous-menu (3) s’affiche.

![Boîte de dialogue avec un bouton partagé et un contrôle pager. ](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

Cette classe est pris en charge dans Windows Vista et versions ultérieures.

Exigences supplémentaires pour cette classe sont décrites dans [Build Configuration requise pour Windows Vista contrôles communs](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="create"></a>  CSplitButton::Create

Crée un contrôle bouton partagé avec des styles spécifiés et l’attache à actuel `CSplitButton` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwStyle*|[in] Une combinaison (OR) au niveau du bit de styles à appliquer au contrôle. Pour plus d’informations, consultez [Styles de boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[in] Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui contient la position et la taille du contrôle.|
|*pParentWnd*|[in] Un pointeur non null pour un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parent du contrôle.|
|*nID*|[in] L’ID du contrôle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton

Construit un objet `CSplitButton`. Les paramètres du constructeur spécifient un sous-menu qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle split button.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nMenuId*|[in] L’ID de ressource de la barre de menus.|
|*nSubMenuId*|[in] L’ID de ressource d’un sous-menu.|
|*pMenu*|[in] Un pointeur vers un [CMenu](../../mfc/reference/cmenu-class.md) objet qui spécifie un sous-menu. Le `CSplitButton` supprime l’objet le `CMenu` objet et ses HMENU associé lorsque le `CSplitButton` objet est hors de portée.|

### <a name="remarks"></a>Notes

Utilisez le [CSplitButton::Create](#create) méthode pour créer un contrôle bouton partagé et l’attacher à la `CSplitButton` objet.

##  <a name="ondropdown"></a>  CSplitButton::OnDropDown

Gère la notification BCN_DROPDOWN envoyé par le système lorsqu’un utilisateur clique sur la flèche déroulante du contrôle de bouton de fractionnement actuel.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pNMHDR*|[in] Pointeur vers un [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) structure qui contient des informations sur le [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) notification.|
|*pResult*|[out] (Non utilisé ; aucune valeur n’est retournée). Valeur de retour de la [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) notification.|

### <a name="remarks"></a>Notes

Lorsque l’utilisateur clique sur la flèche de déroulement sur un contrôle bouton partagé, le système envoie une notification BCN_DROPDOWN du message, ce qui le `OnDropDown` descripteurs de méthode. Toutefois, le `CSplitButton` objet ne transfère pas la notification BCN_DROPDOWN au contrôle qui contient le contrôle bouton partagé. Par conséquent, le contrôle conteneur ne peut pas prendre en charge une action personnalisée en réponse à la notification.

Pour implémenter une action personnalisée qui prend en charge du contrôle conteneur, utilisez un [CButton](../../mfc/reference/cbutton-class.md) objet avec un style de BS_SPLITBUTTON au lieu d’un `CSplitButton` objet. Puis implémentez un gestionnaire pour la notification BCN_DROPDOWN dans le `CButton` objet. Pour plus d’informations, consultez [Styles de boutons](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Pour implémenter une action personnalisée que le bouton partagé contrôle lui-même prend en charge, utilisez [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md). Dérivez votre propre classe de la `CSplitButton` classe et nommez-le, par exemple, CMySplitButton. Ajoutez ensuite la table des messages suivants à votre application pour gérer la notification BCN_DROPDOWN :

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu

Définit le menu déroulant qui s’affiche quand un utilisateur clique sur la flèche déroulante du contrôle de bouton de fractionnement actuel.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nMenuId*|[in] L’ID de ressource de la barre de menus.|
|*nSubMenuId*|[in] L’ID de ressource d’un sous-menu.|
|*pMenu*|[in] Pointeur vers un [CMenu](../../mfc/reference/cmenu-class.md) objet qui spécifie un sous-menu. Le `CSplitButton` supprime l’objet le `CMenu` objet et ses HMENU associé lorsque le `CSplitButton` objet est hors de portée.|

### <a name="remarks"></a>Notes

Le *nMenuId* paramètre identifie une barre de menus, qui est une liste d’éléments de barre de menu horizontale. Le *nSubMenuId* paramètre est un nombre d’index de base zéro qui identifie un sous-menu, qui est la liste déroulante d’éléments de menu associé à chaque élément de barre de menu. Par exemple, une application classique a un menu qui contient les éléments de barre de menu « Fichier », « Modifier » et « Help ». L’élément de barre de menu « Fichier » a un sous-menu contenant les éléments de menu « Ouvrir », « Fermer » et « Exit ». Un clic sur la flèche déroulante du contrôle bouton partagé, le contrôle affiche le sous-menu spécifié, pas la barre de menus.

L’illustration suivante représente une boîte de dialogue qui contient un contrôle de pagineur et un contrôle bouton partagé (1). La flèche déroulante (2) a déjà été cliqué et le sous-menu (3) s’affiche.

![Boîte de dialogue avec un bouton partagé et un contrôle pager. ](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")

### <a name="example"></a>Exemple

La première instruction dans l’exemple de code suivant montre le [CSplitButton::SetDropDownMenu](#setdropdownmenu) (méthode). Éditeur qui a nommé automatiquement l’ID de barre de menu, IDR_MENU1, nous avons créé le menu avec la ressource de Visual Studio. Le *nSubMenuId* paramètre, qui est égal à zéro, fait référence à la seul sous-menu de la barre de menus.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[CSplitButton, classe](../../mfc/reference/csplitbutton-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)
