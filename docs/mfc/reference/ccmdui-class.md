---
title: CCmdUI, classe
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: 3e167d9e305481e05808f5e553222c10abbc88de
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752727"
---
# <a name="ccmdui-class"></a>CCmdUI, classe

Est utilisé uniquement `ON_UPDATE_COMMAND_UI` au `CCmdTarget`sein d’un gestionnaire dans une classe dérivée.

## <a name="syntax"></a>Syntaxe

```
class CCmdUI
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCmdUI::ContinuerRouting](#continuerouting)|Indique au mécanisme de routage de commande de continuer à acheminer le message actuel dans la chaîne des gestionnaires.|
|[CCmdUI::Active](#enable)|Permet ou désactive l’élément utilisateur-interface pour cette commande.|
|[CCmdUI::SetCheck](#setcheck)|Définit l’état de contrôle de l’élément utilisateur-interface pour cette commande.|
|[CCmdUI::SetRadio](#setradio)|Comme `SetCheck` la fonction membre, mais fonctionne sur les groupes de radio.|
|[CCmdUI::SetText](#settext)|Définit le texte pour l’élément utilisateur-interface pour cette commande.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCmdUI:m_nID](#m_nid)|L’ID de l’objet utilisateur-interface.|
|[CCmdUI:m_nIndex](#m_nindex)|L’index de l’objet utilisateur-interface.|
|[CCmdUI::m_pMenu](#m_pmenu)|Points au menu représenté `CCmdUI` par l’objet.|
|[CCmdUI:m_pOther](#m_pother)|Indique l’objet de fenêtre qui a envoyé la notification.|
|[CCmdUI:m_pSubMenu](#m_psubmenu)|Points vers le sous-menu contenu `CCmdUI` représenté par l’objet.|

## <a name="remarks"></a>Notes

`CCmdUI`n’a pas de classe de base.

Lorsqu’un utilisateur de votre application tire vers le bas un menu, chaque élément de menu doit savoir s’il doit être affiché comme activé ou désactivé. La cible d’une commande de menu fournit cette information en mettant en œuvre un gestionnaire de ON_UPDATE_COMMAND_UI. Pour chacun des objets d’interface utilisateur de commande de votre application, utilisez la fenêtre [Class Wizard](mfc-class-wizard.md) ou **Properties** (dans **Class View**) pour créer une entrée de carte de message et un prototype de fonction pour chaque gestionnaire.

Lorsque le menu est retiré, le cadre recherche et appelle chaque `CCmdUI` ON_UPDATE_COMMAND_UI gestionnaire, `Enable` chaque `Check`gestionnaire appelle les fonctions des membres telles que et, et le cadre affiche ensuite de manière appropriée chaque élément de menu.

Un élément de menu peut être remplacé par un bouton de barre de `ON_UPDATE_COMMAND_UI` contrôle ou un autre objet d’interface utilisateur de commande sans changer le code dans le gestionnaire.

Le tableau suivant résume `CCmdUI`l’effet des fonctions des membres sur divers éléments d’interface utilisateur de commande.

|Article utilisateur-interface|Activer|SetCheck SetCheck (setCheck)|SetRadio SetRadio|SetText (en)|
|--------------------------|------------|--------------|--------------|-------------|
|Élément de menu|Permet ou désactive|Vérifications ou déco chèques|Vérifications à l’aide d’un point|Définit le texte de l’élément|
|Bouton de la barre d'outils|Permet ou désactive|Sélectionne, désélectionnable ou indéterminée|Identique à `SetCheck`|(Non applicable)|
|Volet statut-bar|Rend le texte visible ou invisible|Définit la frontière pop-out ou normale|Identique à `SetCheck`|Définit le texte de la vitre|
|Bouton normal dans`CDialogBar`|Permet ou désactive|Vérifications ou décocheurs case à cocher|Identique à `SetCheck`|Définit le texte du bouton|
|Contrôle normal dans`CDialogBar`|Permet ou désactive|(Non applicable)|(Non applicable)|Définit le texte de fenêtre|

Pour en savoir plus sur l’utilisation de cette classe, voir [Comment mettre à jour les objets utilisateur-interface](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CCmdUI`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::ContinuerRouting

Appelez cette fonction de membre pour indiquer au mécanisme de routage de commande de continuer à acheminer le message actuel vers le bas de la chaîne de gestionnaires.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Notes

Il s’agit d’une fonction de membre avancée qui doit être utilisée en conjonction avec un gestionnaire de ON_COMMAND_EX qui retourne FALSE. Pour plus d’informations, voir [Note technique 6](../../mfc/tn006-message-maps.md).

## <a name="ccmduienable"></a><a name="enable"></a>CCmdUI::Active

Appelez cette fonction de membre pour activer ou désactiver l’élément utilisateur-interface pour cette commande.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
VRAI pour permettre à l’article, FALSE de le désactiver.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI:m_nID

L’ID de l’élément de menu, le bouton de `CCmdUI` barre d’outils ou tout autre objet utilisateur-interface représenté par l’objet.

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI:m_nIndex

L’index de l’élément de menu, le bouton de `CCmdUI` barre d’outils ou tout autre objet utilisateur-interface représenté par l’objet.

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu

Pointeur `CMenu` (de type) au menu `CCmdUI` représenté par l’objet.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Notes

NULL si l’article n’est pas un menu.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CCmdUI:m_pSubMenu

Pointeur `CMenu` (de type) au sous-menu `CCmdUI` contenu représenté par l’objet.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Notes

NULL si l’article n’est pas un menu. Si le sous-menu est un pop-up, *m_nID* contient l’ID du premier élément dans le menu pop-up. Pour plus d’informations, voir [Note technique 21](../../mfc/tn021-command-and-message-routing.md).

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CCmdUI:m_pOther

Pointeur (de type `CWnd`) à l’objet de fenêtre, tel qu’un outil ou une barre de statut, qui a envoyé la notification.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Notes

NULL si l’article est un `CWnd` menu ou un non-objet.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck

Appelez cette fonction de membre pour définir l’élément utilisateur-interface de cette commande à l’état de contrôle approprié.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Paramètres

*nCheck (en)*<br/>
Spécifie l’état de contrôle à définir. Si 0, décocheurs; si 1, vérifie; et si 2, fixe une durée indéterminée.

### <a name="remarks"></a>Notes

Cette fonction de membre fonctionne pour les éléments de menu et les boutons de barre d’outils. L’état d’une durée indéterminée ne s’applique qu’aux boutons de barre d’outils.

## <a name="ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio

Appelez cette fonction de membre pour définir l’élément utilisateur-interface de cette commande à l’état de contrôle approprié.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
VRAI pour activer l’article; autrement FALSE.

### <a name="remarks"></a>Notes

Cette fonction de `SetCheck`membre fonctionne comme, sauf qu’elle fonctionne sur des éléments d’interface utilisateur agissant dans le cadre d’un groupe de radio. Décocher les autres éléments du groupe n’est pas automatique à moins que les éléments eux-mêmes maintiennent le comportement du groupe radio.

## <a name="ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText

Appelez cette fonction de membre pour définir le texte de l’élément utilisateur-interface pour cette commande.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Un pointeur à une chaîne de texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
