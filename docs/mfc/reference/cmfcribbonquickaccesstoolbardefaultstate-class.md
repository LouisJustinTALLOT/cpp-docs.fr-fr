---
title: Cmfcribbonquickaccesstoolbardefaultstate, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9ee6a600e4a552e90cd5901340c3759d52a59
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702778"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Cmfcribbonquickaccesstoolbardefaultstate, classe
Une classe d’assistance qui gère l’état par défaut pour la barre d’outils Accès rapide qui est placé sur la barre du ruban ( [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Construit un objet `CMFCRibbonQuickAccessToolbarDefaultState`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Ajoute une commande à l’état par défaut pour la barre d’outils Accès rapide. Cela ne modifie pas la barre d’outils lui-même.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Copie les propriétés d’une barre d’outils Accès rapide à un autre.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Supprime toutes les commandes de la barre d’outils Accès rapide. Cela ne modifie pas la barre d’outils lui-même.|  
  
## <a name="remarks"></a>Notes  
 Après avoir créé la barre d’outils Accès rapide dans votre application, nous vous recommandons de définir son état par défaut en appelant [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Cet état par défaut est restauré lorsqu’un utilisateur clique sur le **réinitialiser** bouton sur le **personnaliser** page de votre application **Options** boîte de dialogue.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCRibbonQuickAccessToolbarDefaultState` classe et comment ajouter une commande à l’état par défaut pour la barre d’outils Accès rapide.  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribbonquickaccesstoolbar.h  
  
##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 Ajoute une commande à l’état par défaut pour la barre d’outils Accès rapide.  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *[in] uiCmd*  
 Spécifie l’ID de commande.  
  
 *[in] bIsVisible*  
 Définit la visibilité de la commande lors de la barre d’outils Accès rapide est dans l’état par défaut.  
  
### <a name="remarks"></a>Notes  
 Ajout d’une commande à le CMFCRibbonQuickAccessToolBarDefaultState accomplit trois résultats. Tout d’abord, chaque commande ajoutée est répertorié dans la liste déroulante située à droite de la barre d’outils Accès rapide. De cette manière, un utilisateur peut facilement ajouter ou supprimer cette commande à partir de la barre d’outils Accès rapide. En second lieu, la barre d’outils Accès rapide est réinitialisé pour afficher uniquement les commandes qui sont répertoriés comme visible dans l’état par défaut lorsque l’utilisateur clique sur le **réinitialiser** situé dans le **personnaliser** boîte de dialogue. Troisième, si vous n’avez pas appelé [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barre d’outils Accès rapide utilise les commandes visibles à partir de cette liste en tant que les commandes visibles par défaut la première fois qu’un utilisateur exécute votre application. Une fois que vous avez ajouté toutes les commandes que vous le souhaitez, appelez [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) pour définir cette instance en tant que l’état par défaut pour la barre d’outils Accès rapide de cette barre du ruban.  
  
##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 Copie les propriétés d’une barre d’outils Accès rapide à un autre.  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>Paramètres  
*src*<br/>
[in] Une référence à la source de `CMFCRibbonQuickAccessToolBarDefaultState` objet à copier.  
  
### <a name="remarks"></a>Notes  
 Cette méthode copie chaque commande à partir de la source `CMFCRibbonQuickAccessToolBarDefaultState` objet de cet objet à l’aide de la [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) (méthode).  
  
##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 Construit l’objet d’état par défaut une barre d’outils Accès rapide.  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, la liste des commandes qui la nouvelle instance de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) contient est vide.  
  
##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 Efface la liste des commandes par défaut dans la barre d’outils Accès rapide.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction supprime de cette instance, toutes les commandes que les appels précédents à [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) ajouté.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
