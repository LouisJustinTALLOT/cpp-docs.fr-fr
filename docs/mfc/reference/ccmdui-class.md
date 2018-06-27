---
title: CCmdUI (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dd417872ab4009a9e0f6c06fc0958f5780de477
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954150"
---
# <a name="ccmdui-class"></a>CCmdUI (classe)
Est utilisé uniquement dans un `ON_UPDATE_COMMAND_UI` gestionnaire dans un `CCmdTarget`-classe dérivée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|Indique au mécanisme de routage des commandes pour continuer le routage du message en cours dans la chaîne de gestionnaires.|  
|[CCmdUI::Enable](#enable)|Active ou désactive l’élément d’interface utilisateur pour cette commande.|  
|[CCmdUI::SetCheck](#setcheck)|Définit l’état d’activation de l’élément d’interface utilisateur pour cette commande.|  
|[CCmdUI::SetRadio](#setradio)|Comme le `SetCheck` fonction membre, mais fonctionne sur les groupes de cases d’option.|  
|[CCmdUI::SetText](#settext)|Définit le texte de l’élément d’interface utilisateur pour cette commande.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|L’ID de l’objet d’interface utilisateur.|  
|[CCmdUI::m_nIndex](#m_nindex)|L’index de l’objet d’interface utilisateur.|  
|[CCmdUI::m_pMenu](#m_pmenu)|Pointe vers le menu représenté par le `CCmdUI` objet.|  
|[CCmdUI::m_pOther](#m_pother)|Pointe vers l’objet de fenêtre qui a envoyé la notification.|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Pointe vers le sous-menu contenu représenté par le `CCmdUI` objet.|  
  
## <a name="remarks"></a>Notes  
 `CCmdUI` ne dispose pas d’une classe de base.  
  
 Lorsqu’un utilisateur de votre application extrait un menu, chaque élément de menu doit savoir si elle doit être affiché comme activé ou désactivé. La cible d’une commande de menu fournit ces informations en implémentant un `ON_UPDATE_COMMAND_UI` gestionnaire. Pour chacun des objets d’interface utilisateur de commande dans votre application, utilisez la fenêtre Propriétés pour créer un prototype d’entrée et de la fonction table des messages pour chaque gestionnaire.  
  
 Lorsque le menu est extraite, l’infrastructure recherche et appelle chacune `ON_UPDATE_COMMAND_UI` gestionnaire, chaque gestionnaire appelle `CCmdUI` telles que les fonctions membres `Enable` et `Check`, le framework puis convenablement affiche chaque élément de menu.  
  
 Un élément de menu peut être remplacé par un bouton de barre de contrôle ou un autre objet d’interface utilisateur de commande sans modifier le code dans le `ON_UPDATE_COMMAND_UI` gestionnaire.  
  
 Le tableau suivant résume l’effet `CCmdUI`de fonctions membres ont sur les divers éléments d’interface utilisateur de commande.  
  
|Élément d’Interface utilisateur|Activer|SetCheck|SetRadio|SetText|  
|--------------------------|------------|--------------|--------------|-------------|  
|Menu Item|Active ou désactive|Active ou désactive|Vérifications à l’aide d’un point|Texte d’élément de jeux|  
|Bouton de barre d’outils|Active ou désactive|Sélectionne, est désélectionnée, ou indéterminé|Identique à `SetCheck`|(Non applicable)|  
|Volet de barre d’état|Rend le texte visible ou invisible|Bordure contextuelle ou normale de jeux|Identique à `SetCheck`|Définit le texte du volet|  
|Bouton normal dans `CDialogBar`|Active ou désactive|Active ou désactive la case à cocher|Identique à `SetCheck`|Texte du bouton de jeux|  
|Contrôle normal dans `CDialogBar`|Active ou désactive|(Non applicable)|(Non applicable)|Définit le texte de la fenêtre|  
  
 Pour plus d’informations sur l’utilisation de cette classe, consultez [comment les objets d’Interface utilisateur de mise à jour](../../mfc/how-to-update-user-interface-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CCmdUI`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting  
 Appelez cette fonction membre pour indiquer le mécanisme de routage des commandes pour continuer le routage du message en cours dans la chaîne de gestionnaires.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’une fonction membre avancée qui doit être utilisée conjointement avec un `ON_COMMAND_EX` gestionnaire retourne **FALSE**. Pour plus d’informations, consultez [Technical Note 6](../../mfc/tn006-message-maps.md).  
  
##  <a name="enable"></a>  CCmdUI::Enable  
 Appelez cette fonction membre pour activer ou désactiver l’élément d’interface utilisateur pour cette commande.  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bOn*  
 **TRUE** pour activer l’élément, **FALSE** pour la désactiver.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>  CCmdUI::m_nID  
 L’ID de l’élément de menu, le bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par le `CCmdUI` objet.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>  CCmdUI::m_nIndex  
 L’index de l’élément de menu, le bouton de barre d’outils ou un autre objet d’interface utilisateur représenté par le `CCmdUI` objet.  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu  
 Pointeur (de `CMenu` type) au menu représenté par le `CCmdUI` objet.  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>Notes  
 **NULL** si l’élément n’est pas un menu.  
  
##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu  
 Pointeur (de `CMenu` type) pour le sous-menu contenu représenté par le `CCmdUI` objet.  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>Notes  
 **NULL** si l’élément n’est pas un menu. Si le sous-menu est une fenêtre contextuelle, *m_nID* contient l’ID du premier élément dans le menu contextuel. Pour plus d’informations, consultez [Note technique 21](../../mfc/tn021-command-and-message-routing.md).  
  
##  <a name="m_pother"></a>  CCmdUI::m_pOther  
 Pointeur (de type `CWnd`) à l’objet fenêtre, comme une barre d’outil ou d’état, qui la notification est envoyée.  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>Notes  
 **NULL** si l’élément est un menu ou non - `CWnd` objet.  
  
##  <a name="setcheck"></a>  CCmdUI::SetCheck  
 Appelez cette fonction membre pour définir l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVérifiez*  
 Spécifie l’état de la vérification à définir. Si 0, désactive ; Si 1, les contrôles ; et si le 2 définit indéterminé.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre fonctionne pour les éléments de menu et boutons de barre d’outils. L’état indéterminé s’applique uniquement aux boutons de barre d’outils.  
  
##  <a name="setradio"></a>  CCmdUI::SetRadio  
 Appelez cette fonction membre pour définir l’élément d’interface utilisateur pour cette commande à l’état d’activation appropriée.  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bOn`  
 **TRUE** pour activer l’élément ; sinon **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre fonctionne comme `SetCheck`, à ceci près qu’elle fonctionne sur les éléments d’interface utilisateur qui agit en tant que partie d’un groupe de cases d’option. Si vous décochez les autres éléments dans le groupe n’est pas automatique, sauf si les éléments proprement dits préserver le comportement de groupe de cases d’option.  
  
##  <a name="settext"></a>  CCmdUI::SetText  
 Appelez cette fonction membre pour définir le texte de l’élément d’interface utilisateur pour cette commande.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszText*  
 Pointeur vers une chaîne de texte.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MDI](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)
