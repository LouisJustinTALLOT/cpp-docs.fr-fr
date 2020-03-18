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
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418824"
---
# <a name="ccmdui-class"></a>CCmdUI, classe

Est utilisé uniquement dans un gestionnaire de `ON_UPDATE_COMMAND_UI` dans une classe dérivée de `CCmdTarget`.

## <a name="syntax"></a>Syntaxe

```
class CCmdUI
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CCmdUI :: ContinueRouting](#continuerouting)|Indique au mécanisme de routage de commande de continuer à acheminer le message actuel vers le dessous de la chaîne de gestionnaires.|
|[CCmdUI :: Enable](#enable)|Active ou désactive l’élément d’interface utilisateur pour cette commande.|
|[CCmdUI :: SetCheck](#setcheck)|Définit l’état d’activation de l’élément d’interface utilisateur pour cette commande.|
|[CCmdUI :: SetRadio](#setradio)|Comme la fonction membre `SetCheck`, mais fonctionne sur les groupes radio.|
|[CCmdUI :: SetText](#settext)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CCmdUI :: m_nID](#m_nid)|ID de l’objet d’interface utilisateur.|
|[CCmdUI :: m_nIndex](#m_nindex)|Index de l’objet d’interface utilisateur.|
|[CCmdUI :: m_pMenu](#m_pmenu)|Pointe vers le menu représenté par l’objet `CCmdUI`.|
|[CCmdUI :: m_pOther](#m_pother)|Pointe vers l’objet de fenêtre qui a envoyé la notification.|
|[CCmdUI :: m_pSubMenu](#m_psubmenu)|Pointe vers le sous-menu contenu représenté par l’objet `CCmdUI`.|

## <a name="remarks"></a>Notes

`CCmdUI` n’a pas de classe de base.

Lorsqu’un utilisateur de votre application extrait un menu, chaque élément de menu doit savoir s’il doit être affiché comme activé ou désactivé. La cible d’une commande de menu fournit ces informations en implémentant un gestionnaire de ON_UPDATE_COMMAND_UI. Pour chacun des objets d’interface utilisateur de commande de votre application, utilisez l' [Assistant classe](mfc-class-wizard.md) ou la fenêtre **propriétés** (dans **affichage de classes**) pour créer une entrée de table des messages et un prototype de fonction pour chaque gestionnaire.

Lorsque le menu est extrait, l’infrastructure recherche et appelle chaque gestionnaire de ON_UPDATE_COMMAND_UI, chaque gestionnaire appelle `CCmdUI` fonctions membres telles que `Enable` et `Check`, et l’infrastructure affiche ensuite de manière appropriée chaque élément de menu.

Un élément de menu peut être remplacé par un bouton de barre de contrôle ou un autre objet d’interface utilisateur de commande sans modifier le code dans le gestionnaire de `ON_UPDATE_COMMAND_UI`.

Le tableau suivant résume l’effet que les fonctions membres de `CCmdUI`ont sur différents éléments de l’interface utilisateur de commande.

|Élément d’interface utilisateur|Activer|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Élément de menu|Active ou désactive|Vérifie ou décoche|Vérifications à l’aide d’un point|Définit le texte de l’élément|
|Bouton de la barre d'outils|Active ou désactive|Sélectionne, désélectionne ou indéterminé|Identique à `SetCheck`|(Non applicable)|
|Volet de la barre d’État|Rend le texte visible ou invisible|Définit la bordure normale ou contextuelle|Identique à `SetCheck`|Définit le texte du volet|
|Bouton normal dans `CDialogBar`|Active ou désactive|Case à cocher vérifications ou décoches|Identique à `SetCheck`|Définit le texte du bouton|
|Contrôle normal dans `CDialogBar`|Active ou désactive|(Non applicable)|(Non applicable)|Définit le texte de la fenêtre|

Pour plus d’informations sur l’utilisation de cette classe, consultez [Comment mettre à jour des objets d’interface utilisateur](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`CCmdUI`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="continuerouting"></a>CCmdUI :: ContinueRouting

Appelez cette fonction membre pour indiquer au mécanisme de routage de commande de continuer à acheminer le message actuel vers le bout de la chaîne de gestionnaires.

```
void ContinueRouting();
```

### <a name="remarks"></a>Notes

Il s’agit d’une fonction membre avancée qui doit être utilisée conjointement avec un gestionnaire de ON_COMMAND_EX qui retourne FALSe. Pour plus d’informations, consultez [Technical note 6](../../mfc/tn006-message-maps.md).

##  <a name="enable"></a>CCmdUI :: Enable

Appelez cette fonction membre pour activer ou désactiver l’élément d’interface utilisateur pour cette commande.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Paramètres

*Ble*<br/>
TRUE pour activer l’élément, FALSe pour le désactiver.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI :: m_nID

ID de l’élément de menu, du bouton de barre d’outils ou d’un autre objet de l’interface utilisateur représenté par l’objet `CCmdUI`.

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI :: m_nIndex

Index de l’élément de menu, du bouton de barre d’outils ou d’un autre objet de l’interface utilisateur représenté par l’objet `CCmdUI`.

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI :: m_pMenu

Pointeur (de `CMenu` type) vers le menu représenté par l’objet `CCmdUI`.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Notes

NULL si l’élément n’est pas un menu.

##  <a name="m_psubmenu"></a>CCmdUI :: m_pSubMenu

Pointeur (de `CMenu` type) vers le sous-menu contenu représenté par l’objet `CCmdUI`.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Notes

NULL si l’élément n’est pas un menu. Si le sous-menu est une fenêtre contextuelle, *m_nID* contient l’ID du premier élément dans le menu contextuel. Pour plus d’informations, consultez la [note technique 21](../../mfc/tn021-command-and-message-routing.md).

##  <a name="m_pother"></a>CCmdUI :: m_pOther

Pointeur (de type `CWnd`) vers l’objet de fenêtre, tel qu’un outil ou une barre d’État, qui a envoyé la notification.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Notes

NULL si l’élément est un menu ou un objet non `CWnd`.

##  <a name="setcheck"></a>CCmdUI :: SetCheck

Appelez cette fonction membre pour définir l’état d’activation approprié pour l’élément d’interface utilisateur de cette commande.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Paramètres

*nConsultez*<br/>
Spécifie l’état d’activation à définir. Si la valeur est 0, l’option est désactivée ; Si 1, vérifie ; et si 2, définit le paramètre Indeterminate.

### <a name="remarks"></a>Notes

Cette fonction membre fonctionne pour les éléments de menu et les boutons de barre d’outils. L’état indéterminé s’applique uniquement aux boutons de la barre d’outils.

##  <a name="setradio"></a>CCmdUI :: SetRadio

Appelez cette fonction membre pour définir l’état d’activation approprié pour l’élément d’interface utilisateur de cette commande.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Paramètres

*Ble*<br/>
TRUE pour activer l’élément ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction membre fonctionne comme `SetCheck`, sauf qu’elle fonctionne sur des éléments d’interface utilisateur agissant dans le cadre d’un groupe de cases d’option. Le fait de décocher les autres éléments du groupe n’est pas automatique, à moins que les éléments eux-mêmes ne maintiennent pas le comportement de groupe de cases d’option.

##  <a name="settext"></a>CCmdUI :: SetText

Appelez cette fonction membre pour définir le texte de l’élément d’interface utilisateur pour cette commande.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointeur vers une chaîne de texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
