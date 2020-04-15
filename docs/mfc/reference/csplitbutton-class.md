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
ms.openlocfilehash: 0b54324c3c5503182add15a3dd0a9ecd07c24b18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318111"
---
# <a name="csplitbutton-class"></a>CSplitButton, classe

La `CSplitButton` classe représente un contrôle de bouton fendu. Le contrôle bouton partagé exécute un comportement par défaut lorsqu’un utilisateur clique sur la partie principale du bouton et affiche un menu déroulant lorsqu’un utilisateur clique sur la flèche déroulante du bouton.

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
|[CSplitButton::Créer](#create)|Crée un contrôle de bouton fendu avec `CSplitButton` des styles spécifiés et le fixe à l’objet actuel.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Définit le menu de dépôt qui s’affiche lorsqu’un utilisateur clique sur la flèche de chute du contrôle du bouton fractionné actuel.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Gère la notification BCN_DROPDOWN que le système envoie lorsqu’un utilisateur clique sur la flèche de chute du contrôle actuel du bouton fractionné.|

## <a name="remarks"></a>Notes

La `CSplitButton` classe est dérivée de la classe [CButton.](../../mfc/reference/cbutton-class.md) Le contrôle du bouton fendu est un contrôle de bouton dont le style est BS_SPLITBUTTON. Il affiche un menu personnalisé lorsqu’un utilisateur clique sur la flèche de dépôt. Pour plus d’informations, voir les styles BS_SPLITBUTTON et BS_DEFSPLITBUTTON dans [Button Styles](/windows/win32/Controls/button-styles).

La figure suivante représente une boîte de dialogue qui contient un contrôle de téléavertisseur et un (1) contrôle du bouton fendu. La flèche (2) drop-down a déjà été cliqué et le (3) submenu est affiché.

![Dialogue avec un bouton partagé et un contrôle pager.](../../mfc/reference/media/splitbutton_pager.png "Dialogue avec un bouton partagé et un contrôle pager.")

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

Cette classe est prise en charge dans Windows Vista et plus tard.

Des exigences supplémentaires pour cette classe sont décrites dans [Build Requirements for Windows Vista Common Controls](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplitButton::Créer

Crée un contrôle de bouton fendu avec `CSplitButton` des styles spécifiés et le fixe à l’objet actuel.

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
|*dwStyle (en)*|[dans] Une combinaison bitwise (OU) de styles à appliquer au contrôle. Pour plus d’informations, voir [Button Styles](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[dans] Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui contient la position et la taille du contrôle.|
|*pParentWnd*|[dans] Un pointeur non nul à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle.|
|*nID*|[dans] L’id du contrôle.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>CSplitButton::CSplitButton

Construit un objet `CSplitButton`. Les paramètres du constructeur spécifient un sous-mois qui s’affiche lorsqu’un utilisateur clique sur la flèche de chute du contrôle du bouton fractionné.

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
|*nMenuId (en anglais)*|[dans] L’ID de ressource de la barre de menu.|
|*nSubMenuId*|[dans] L’ID de ressource d’un sous-mois.|
|*pMenu*|[dans] Un pointeur à un objet [CMenu](../../mfc/reference/cmenu-class.md) qui spécifie un sous-mois. L’objet `CSplitButton` supprime `CMenu` l’objet et son `CSplitButton` HMENU associé lorsque l’objet devient hors de portée.|

### <a name="remarks"></a>Notes

Utilisez le [CSplitButton: :: Créez la](#create) méthode pour `CSplitButton` créer un contrôle de bouton fendu et attachez-le à l’objet.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplitButton::OnDropDown

Gère la notification BCN_DROPDOWN que le système envoie lorsqu’un utilisateur clique sur la flèche de chute du contrôle actuel du bouton fractionné.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pNMHDR (en)*|[dans] Pointeur vers une structure [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) qui contient des informations sur la [notification BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|
|*pResult*|[out] (Non utilisé; aucune valeur n’est retournée.) Valeur de retour de la notification [BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|

### <a name="remarks"></a>Notes

Lorsque l’utilisateur clique sur la flèche de dépôt sur un contrôle de bouton `OnDropDown` fractionné, le système envoie un message de notification BCN_DROPDOWN, que la méthode gère. Toutefois, `CSplitButton` l’objet ne transmet pas la notification BCN_DROPDOWN au contrôle qui contient le contrôle du bouton fractionné. Par conséquent, le contrôle de confinement ne peut pas prendre en charge une action personnalisée en réponse à la notification.

Pour implémenter une action personnalisée que le contrôle contenant prend en charge, `CSplitButton` utilisez un objet [CButton](../../mfc/reference/cbutton-class.md) avec un style de BS_SPLITBUTTON au lieu d’un objet. Ensuite, implémentez un gestionnaire pour `CButton` la notification BCN_DROPDOWN dans l’objet. Pour plus d’informations, voir [Button Styles](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Pour implémenter une action personnalisée que le bouton fractionné prend en charge elle-même, utilisez [la réflexion du message](../../mfc/tn062-message-reflection-for-windows-controls.md). Dérivez votre propre `CSplitButton` classe de la classe et nommez-la, par exemple, CMySplitButton. Ajoutez ensuite la carte de message suivante à votre application pour gérer la notification BCN_DROPDOWN :

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu

Définit le menu de dépôt qui s’affiche lorsqu’un utilisateur clique sur la flèche de chute du contrôle du bouton fractionné actuel.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nMenuId (en anglais)*|[dans] L’ID de ressource de la barre de menu.|
|*nSubMenuId*|[dans] L’ID de ressource d’un sous-mois.|
|*pMenu*|[dans] Pointeur à un objet [CMenu](../../mfc/reference/cmenu-class.md) qui spécifie un sous-mois. L’objet `CSplitButton` supprime `CMenu` l’objet et son `CSplitButton` HMENU associé lorsque l’objet devient hors de portée.|

### <a name="remarks"></a>Notes

Le *paramètre nMenuId* identifie une barre de menu, qui est une liste horizontale d’éléments de barre de menu. Le paramètre *nSubMenuId* est un numéro d’index basé à zéro qui identifie un sous-mois, qui est la liste déroulante des éléments de menu associés à chaque élément de barre de menu. Par exemple, une application typique a un menu qui contient les éléments de barre de menu, "File", "Modifier," et "Aide." L’élément bar du menu "File" dispose d’un sous-mois qui contient les éléments du menu, "Open", "Close" et "Exit". Lorsque la flèche de chute du contrôle du bouton fendu est cliqué, le contrôle affiche le sous-mois spécifié, pas la barre de menu.

La figure suivante représente une boîte de dialogue qui contient un contrôle de téléavertisseur et un (1) contrôle du bouton fendu. La flèche (2) drop-down a déjà été cliqué et le (3) submenu est affiché.

![Dialogue avec un bouton partagé et un contrôle pager.](../../mfc/reference/media/splitbutton_pager.png "Dialogue avec un bouton partagé et un contrôle pager.")

### <a name="example"></a>Exemple

La première déclaration dans l’exemple de code suivant démontre la méthode [CSplitButton::SetDropDownMenu.](#setdropdownmenu) Nous avons créé le menu avec l’éditeur de ressources Visual Studio, qui a automatiquement nommé l’ID barre de menu, IDR_MENU1. Le paramètre *nSubMenuId,* qui est nul, se réfère au seul sous-mois de la barre de menu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[CSplitButton, classe](../../mfc/reference/csplitbutton-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)
