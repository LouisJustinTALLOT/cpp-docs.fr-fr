---
title: CSplitButton, classe
ms.date: 11/19/2018
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
ms.openlocfilehash: 484cef2787c9e5c166a7b20b017251b559d7221c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562543"
---
# <a name="csplitbutton-class"></a>CSplitButton, classe

La `CSplitButton` classe représente un contrôle bouton partagé. Le contrôle bouton partagé exécute un comportement par défaut lorsqu’un utilisateur clique sur la partie principale du bouton et affiche un menu déroulant lorsqu’un utilisateur clique sur la flèche déroulante du bouton.

## <a name="syntax"></a>Syntaxe

```
class CSplitButton : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSplitButton :: CSplitButton](#csplitbutton)|Construit un objet `CSplitButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSplitButton :: Create](#create)|Crée un contrôle bouton partagé avec les styles spécifiés et l’attache à l' `CSplitButton` objet actuel.|
|[CSplitButton :: SetDropDownMenu](#setdropdownmenu)|Définit le menu déroulant qui s’affiche lorsqu’un utilisateur clique sur la flèche déroulante du contrôle bouton partagé actuel.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSplitButton :: OnDropDown](#ondropdown)|Gère le BCN_DROPDOWN notification que le système envoie lorsqu’un utilisateur clique sur la flèche déroulante du contrôle bouton partagé actuel.|

## <a name="remarks"></a>Notes

La `CSplitButton` classe est dérivée de la classe [CButton](../../mfc/reference/cbutton-class.md) . Le contrôle bouton partagé est un contrôle bouton dont le style est BS_SPLITBUTTON. Il affiche un menu personnalisé lorsqu’un utilisateur clique sur la flèche déroulante. Pour plus d’informations, consultez les styles BS_SPLITBUTTON et BS_DEFSPLITBUTTON dans les [styles de bouton](/windows/win32/Controls/button-styles).

L’illustration suivante représente une boîte de dialogue qui contient un contrôle de pagineur et un contrôle de bouton partagé (1). La flèche de déroulement (2) a déjà été cliquée et le sous-menu (3) s’affiche.

![Dialogue avec un bouton partagé et un contrôle pager.](../../mfc/reference/media/splitbutton_pager.png "Dialogue avec un bouton partagé et un contrôle pager.")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

Cette classe est prise en charge dans Windows Vista et versions ultérieures.

Des exigences supplémentaires pour cette classe sont décrites dans [exigences de build pour les contrôles communs Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="csplitbuttoncreate"></a><a name="create"></a> CSplitButton :: Create

Crée un contrôle bouton partagé avec les styles spécifiés et l’attache à l' `CSplitButton` objet actuel.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*\
dans Combinaison d’opérations de bits (ou) de styles à appliquer au contrôle. Pour plus d’informations, consultez [styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*rectangulaire*\
dans Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle.

*pParentWnd*\
dans Pointeur non null vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle.

*nID*\
dans ID du contrôle.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a> CSplitButton :: CSplitButton

Construit un objet `CSplitButton`. Les paramètres du constructeur spécifient un sous-menu qui s’affiche lorsqu’un utilisateur clique sur la flèche déroulante du contrôle bouton partagé.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Paramètres

*nMenuId*\
dans ID de ressource de la barre de menus.

*nSubMenuId*\
dans ID de ressource d’un sous-menu.

*pMenu*\
dans Pointeur vers un objet [CMenu](../../mfc/reference/cmenu-class.md) qui spécifie un sous-menu. L' `CSplitButton` objet supprime l' `CMenu` objet et son HMENU associé lorsque l' `CSplitButton` objet est hors de portée.

### <a name="remarks"></a>Notes

Utilisez la méthode [CSplitButton :: Create](#create) pour créer un contrôle bouton partagé et l’attacher à l' `CSplitButton` objet.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a> CSplitButton :: OnDropDown

Gère le BCN_DROPDOWN notification que le système envoie lorsqu’un utilisateur clique sur la flèche déroulante du contrôle bouton partagé actuel.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Paramètres

*pNMHDR*\
dans Pointeur vers une structure [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) qui contient des informations sur la notification de [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) .

*pResult*\
à (Non utilisé ; aucune valeur n’est retournée.) Valeur de retour de la notification de [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) .

### <a name="remarks"></a>Notes

Quand l’utilisateur clique sur la flèche déroulante d’un contrôle bouton partagé, le système envoie un message de notification BCN_DROPDOWN que la `OnDropDown` méthode gère. Toutefois, l' `CSplitButton` objet ne transfère pas la notification BCN_DROPDOWN au contrôle qui contient le contrôle bouton partagé. Par conséquent, le contrôle conteneur ne peut pas prendre en charge une action personnalisée en réponse à la notification.

Pour implémenter une action personnalisée prise en charge par le contrôle conteneur, utilisez un objet [CButton](../../mfc/reference/cbutton-class.md) avec un style de BS_SPLITBUTTON au lieu d’un `CSplitButton` objet. Implémentez ensuite un gestionnaire pour la notification de BCN_DROPDOWN dans l' `CButton` objet. Pour plus d’informations, consultez [styles de bouton](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Pour implémenter une action personnalisée prise en charge par le contrôle de bouton partagé, utilisez la [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md). Dérivez votre propre classe de la `CSplitButton` classe et nommez-la, par exemple CMySplitButton. Ajoutez ensuite la table des messages suivante à votre application pour gérer le BCN_DROPDOWN notification :

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a> CSplitButton :: SetDropDownMenu

Définit le menu déroulant qui s’affiche lorsqu’un utilisateur clique sur la flèche déroulante du contrôle bouton partagé actuel.

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

*nMenuId*\
dans ID de ressource de la barre de menus.

*nSubMenuId*\
dans ID de ressource d’un sous-menu.

*pMenu*\
dans Pointeur vers un objet [CMenu](../../mfc/reference/cmenu-class.md) qui spécifie un sous-menu. L' `CSplitButton` objet supprime l' `CMenu` objet et son HMENU associé lorsque l' `CSplitButton` objet est hors de portée.

### <a name="remarks"></a>Notes

Le paramètre *nMenuId* identifie une barre de menus, qui est une liste horizontale d’éléments de barre de menus. Le paramètre *nSubMenuId* est un numéro d’index de base zéro qui identifie un sous-menu, qui est la liste déroulante des éléments de menu associés à chaque élément de barre de menus. Par exemple, une application classique possède un menu qui contient les éléments de barre de menus, « fichier », « modifier » et « aide ». L’élément de barre de menus « fichier » possède un sous-menu qui contient les éléments de menu « ouvrir », « fermer » et « quitter ». Quand l’utilisateur clique sur la flèche déroulante du contrôle de bouton partagé, le contrôle affiche le sous-menu spécifié, et non la barre de menus.

L’illustration suivante représente une boîte de dialogue qui contient un contrôle de pagineur et un contrôle de bouton partagé (1). La flèche de déroulement (2) a déjà été cliquée et le sous-menu (3) s’affiche.

![Dialogue avec un bouton partagé et un contrôle pager.](../../mfc/reference/media/splitbutton_pager.png "Dialogue avec un bouton partagé et un contrôle pager.")

### <a name="example"></a>Exemple

La première instruction de l’exemple de code suivant illustre la méthode [CSplitButton :: SetDropDownMenu](#setdropdownmenu) . Nous avons créé le menu avec l’éditeur de ressources de Visual Studio, qui a automatiquement nommé ID de barre de menus, IDR_MENU1. Le paramètre *nSubMenuId* , qui est égal à zéro, fait référence au seul sous-menu de la barre de menus.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[CSplitButton, classe](../../mfc/reference/csplitbutton-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)
