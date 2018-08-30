---
title: Csnapinitemimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b120ab308e8d46ac4c874681d62bbeaaa86588
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205542"
---
# <a name="csnapinitemimpl-class"></a>Csnapinitemimpl, classe
Cette classe fournit des méthodes pour implémenter un objet de nœud de composant logiciel enfichable.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `CSnapInItemImpl`.  
  
 *bIsExtension*  
 TRUE si l’objet est une extension de composant logiciel enfichable ; Sinon, FALSE.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Ajoute des éléments de menu à un menu contextuel.|  
|[CSnapInItemImpl::Command](#command)|Appelée par la console lorsqu’un élément de menu personnalisé est sélectionné.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Ajoute des pages à la feuille de propriétés du composant logiciel enfichable.|  
|[CSnapInItemImpl::FillData](#filldata)|Copie les informations sur l’objet de composant logiciel enfichable dans un flux spécifié.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Récupère le `RESULTDATAITEM` structure de l’utilisation du composant logiciel enfichable.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Détermine le type d’affichage utilisé par le volet de résultats.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Récupère le `SCOPEDATAITEM` structure de l’utilisation du composant logiciel enfichable.|  
|[CSnapInItemImpl::Notify](#notify)|Appelé par la console pour notifier le composant logiciel enfichable des actions effectuées par l’utilisateur.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Appelé pour déterminer si le nœud de composant logiciel enfichable prend en charge les pages de propriétés.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifie les indicateurs d’insertion de menu pour un objet de composant logiciel enfichable.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Définit les informations du bouton de barre d’outils spécifiée.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Met à jour l’état de l’élément de menu contextuel.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Met à jour l’état du bouton de barre d’outils spécifiée.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Le nom de l’objet de composant logiciel enfichable.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Le Windows `RESULTDATAITEM` structure utilisée par le `CSnapInItemImpl` objet.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Le Windows `SCOPEDATAITEM` structure utilisée par le `CSnapInItemImpl` objet.|  
  
## <a name="remarks"></a>Notes  
 `CSnapInItemImpl` Fournit une implémentation de base pour un objet de nœud de composant logiciel enfichable, telles que l’ajout de barres d’outils et des éléments de menu et le transfert de commandes pour le nœud de composant logiciel enfichable à la fonction gestionnaire approprié. Ces fonctionnalités sont implémentées à l’aide de plusieurs interfaces différentes et mappent les types. L’implémentation par défaut gère les notifications envoyées à l’objet de nœud par la détermination de l’instance correcte de la classe dérivée et puis transférer le message à l’instance correcte.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlsnap.h  
  
##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems  
 Cette méthode implémente la fonction Win32 [IExtendContextMenu::AddMenuItems](https://msdn.microsoft.com/library/aa814841).  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Paramètres  
 *piCallback*  
 [in] Pointeur vers le `IContextMenuCallback` qui peut ajouter des éléments au menu contextuel.  
  
 *pInsertionAllowed*  
 [in, out] Identifie définies par Microsoft Management Console MMC, élément de menu points d’insertion qui peuvent être utilisés. Cela peut être une combinaison des indicateurs suivants :  
  
- CCM_INSERTIONALLOWED_TOP éléments peuvent être insérées en haut d’un menu contextuel.  
  
- CCM_INSERTIONALLOWED_NEW éléments peuvent être insérés dans le sous-menu de créer un nouveau.  
  
- CCM_INSERTIONALLOWED_TASK éléments peuvent être insérés dans le sous-menu de la tâche.  
  
- CCM_INSERTIONALLOWED_VIEW éléments peuvent être insérés dans le menu Affichage de barre d’outils ou dans le sous-menu de l’affichage du menu contextuel de volet de résultats.  
  
 *type*  
 [in] Spécifie le type d’objet. Il peut avoir l’une des valeurs suivantes :  
  
- Objet de données de CCT_SCOPE pour le contexte de volet d’étendue.  
  
- Objet de données de CCT_RESULT pour le contexte de volet de résultats.  
  
- Objet de données de CCT_SNAPIN_MANAGER pour le contexte du composant logiciel enfichable Gestionnaire.  
  
- Objet de données de CCT_UNINITIALIZED a un type non valide.  
  
##  <a name="command"></a>  CSnapInItemImpl::Command  
 Cette méthode implémente la fonction Win32 [IExtendContextMenu::Command](https://msdn.microsoft.com/library/aa814842).  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Paramètres  
 *lCommandID*  
 [in] Spécifie l’identificateur de commande de l’élément de menu.  
  
 *type*  
 [in] Spécifie le type d’objet. Il peut avoir l’une des valeurs suivantes :  
  
- Objet de données de CCT_SCOPE pour le contexte de volet d’étendue.  
  
- Objet de données de CCT_RESULT pour le contexte de volet de résultats.  
  
- Objet de données de CCT_SNAPIN_MANAGER pour le contexte du composant logiciel enfichable Gestionnaire.  
  
- Objet de données de CCT_UNINITIALIZED a un type non valide.  
  
##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages  
 Cette méthode implémente la fonction Win32 [IExtendPropertySheet::CreatePropertyPages](https://msdn.microsoft.com/library/aa814846).  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpProvider*  
 [in] Pointeur vers le `IPropertySheetCallback` interface.  
  
 *handle*  
 [in] Spécifie le handle utilisé pour router le message de notification MMCN_PROPERTY_CHANGE à la classe de données approprié.  
  
 *pUnk*  
 [in] Pointeur vers le `IExtendPropertySheet` interface sur l’objet qui contient des informations de contexte sur le nœud.  
  
 *type*  
 [in] Spécifie le type d’objet. Il peut avoir l’une des valeurs suivantes :  
  
- Objet de données de CCT_SCOPE pour le contexte de volet d’étendue.  
  
- Objet de données de CCT_RESULT pour le contexte de volet de résultats.  
  
- Objet de données de CCT_SNAPIN_MANAGER pour le contexte du composant logiciel enfichable Gestionnaire.  
  
- Objet de données de CCT_UNINITIALIZED a un type non valide.  
  
##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl  
 Construit un objet `CSnapInItemImpl`.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>  CSnapInItemImpl::FillData  
 Cette fonction est appelée pour récupérer des informations sur l’élément.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>Paramètres  
 *CF*  
 [in] Le format (texte, texte enrichi ou texte enrichi avec les éléments OLE) du Presse-papiers.  
  
 *pStream*  
 [in] Un pointeur vers le flux contenant les données d’objet.  
  
### <a name="remarks"></a>Notes  
 Pour implémenter correctement cette fonction, copiez les informations correctes dans le flux (*pStream*), selon le format de Presse-papiers indiqué par *cf*.  
  
##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType  
 Appelez cette fonction pour récupérer le type de l’affichage du volet de résultats de l’objet de composant logiciel enfichable.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppViewType*  
 [out] Pointeur vers l’adresse du type de vue renvoyé.  
  
 *pViewOptions*  
 [out] Pointeur vers l’énumération MMC_VIEW_OPTIONS, qui fournit la console avec les options spécifiées par le composant logiciel enfichable propriétaire. Cette valeur peut être une des opérations suivantes :  
  
- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0 x 00000001 indique à la console à ne pas présenter des choix d’affichage de liste standard dans le **vue** menu. Permet le composant logiciel enfichable afficher ses propres affichages personnalisés uniquement dans le volet résultat. Il s’agit de l’indicateur d’option uniquement défini pour l’instant.  
  
- MMC_VIEW_OPTIONS_NONE = 0 autorise les options d’affichage par défaut.  
  
##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo  
 Appelez cette fonction pour récupérer le `SCOPEDATAITEM` structure de l’utilisation du composant logiciel enfichable.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pScopeDataItem*  
 [out] Un pointeur vers le `SCOPEDATAITEM` structure de le `CSnapInItemImpl` objet.  
  
##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo  
 Appelez cette fonction pour récupérer le `RESULTDATAITEM` structure de l’utilisation du composant logiciel enfichable.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pResultDataItem*  
 [out] Un pointeur vers le `RESULTDATAITEM` structure de le `CSnapInItemImpl` objet.  
  
##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName  
 Contient la chaîne affichée pour l’élément de nœud.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem  
 Le `SCOPEDATAITEM` structure de l’objet de données du composant logiciel enfichable.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem  
 Le [RESULTDATAITEM](https://msdn.microsoft.com/library/aa815165) structure de l’objet de données du composant logiciel enfichable.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>  CSnapInItemImpl::Notify  
 Appelé lorsque l’objet de composant logiciel enfichable est appliquée par l’utilisateur.  
  
```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 *event*  
 [in] Identifie une action effectuée par un utilisateur. Les notifications suivantes sont possibles :  
  
- MMCN_ACTIVATE envoyé lorsqu’une fenêtre est activée et désactivée.  
  
- MMCN_ADD_IMAGES envoyé pour ajouter des images vers le volet de résultats.  
  
- MMCN_BTN_CLICK envoyé lorsque l’utilisateur clique sur un des boutons de barre d’outils.  
  
- MMCN_CLICK envoyé lorsqu’un utilisateur clique sur un bouton de la souris sur un élément de liste.  
  
- MMCN_DBLCLICK envoyé lorsqu’un utilisateur double-clique sur un bouton de la souris sur un élément de liste.  
  
- MMCN_DELETE envoyé pour informer le composant logiciel enfichable dans l’objet doit être supprimé.  
  
- MMCN_EXPAND envoyé lorsqu’un dossier doit être développé ou contractées.  
  
- MMCN_MINIMIZED envoyé lorsqu’une fenêtre est réduite ou agrandie.  
  
- MMCN_PROPERTY_CHANGE envoyé pour informer un composant logiciel enfichable objet vue du composant logiciel enfichable dans l’objet va être modifiée.  
  
- MMCN_REMOVE_CHILDREN envoyé lorsque le composant logiciel enfichable doit supprimer l’ensemble du sous-arbre a ajouté sous le nœud spécifié.  
  
- MMCN_RENAME envoyé la première fois à la requête pour un changement de nom et la deuxième fois pour effectuer le changement de nom.  
  
- MMCN_SELECT envoyé lorsqu’un élément dans le volet de vue étendue ou le résultat est sélectionné.  
  
- MMCN_SHOW envoyé lorsqu’un élément de portée est sélectionné ou désélectionné pour la première fois.  
  
- MMCN_VIEW_CHANGE envoyé lorsque le composant logiciel enfichable peut mettre à jour toutes les vues lorsqu’une modification se produit.  
  
 *arg*  
 [in] Varie selon le type de notification.  
  
 *param*  
 [in] Varie selon le type de notification.  
  
 *pComponentData*  
 [out] Un pointeur vers l’objet qui implémente `IComponentData`. Ce paramètre est NULL si la notification n’est pas transférée à partir de `IComponentData::Notify`.  
  
 *pComponent*  
 [out] Un pointeur vers l’objet qui implémente `IComponent`. Ce paramètre est NULL si la notification n’est pas transférée à partir de `IComponent::Notify`.  
  
 *type*  
 [in] Spécifie le type d’objet. Il peut avoir l’une des valeurs suivantes :  
  
- Objet de données de CCT_SCOPE pour le contexte de volet d’étendue.  
  
- Objet de données de CCT_RESULT pour le contexte de volet de résultats.  
  
- Objet de données de CCT_SNAPIN_MANAGER pour le contexte du composant logiciel enfichable Gestionnaire.  
  
- Objet de données de CCT_UNINITIALIZED a un type non valide.  
  
##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor  
 Appelé pour déterminer si le nœud de composant logiciel enfichable prend en charge les pages de propriétés.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags  
 Appelez cette fonction pour modifier les indicateurs d’insertion de menu, spécifiés par *pInsertionAllowed*, pour l’objet de composant logiciel enfichable.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>Paramètres  
 *bBeforeInsertion*  
 [in] Différent de zéro si la fonction doit être appelée avant que les éléments sont ajoutés au menu contextuel ; sinon 0.  
  
 *pInsertionAllowed*  
 [in, out] Identifie définies par Microsoft Management Console MMC, élément de menu points d’insertion qui peuvent être utilisés. Cela peut être une combinaison des indicateurs suivants :  
  
- CCM_INSERTIONALLOWED_TOP éléments peuvent être insérées en haut d’un menu contextuel.  
  
- CCM_INSERTIONALLOWED_NEW éléments peuvent être insérés dans le sous-menu de créer un nouveau.  
  
- CCM_INSERTIONALLOWED_TASK éléments peuvent être insérés dans le sous-menu de la tâche.  
  
- CCM_INSERTIONALLOWED_VIEW éléments peuvent être insérés dans le menu Affichage de barre d’outils ou dans le sous-menu de l’affichage du menu contextuel de volet de résultats.  
  
### <a name="remarks"></a>Notes  
 Si vous développez un composant logiciel enfichable principal, vous pouvez réinitialiser un des indicateurs d’insertion comme un moyen de limiter le type d’éléments de menu qui a une extension tierce peut ajouter. Par exemple, le composant logiciel enfichable principal peut effacer l’indicateur CCM_INSERTIONALLOWED_NEW pour empêcher des extensions d’ajouter leurs propres éléments de menu créer un nouveau.  
  
 Vous ne devez pas tenter de définir des bits *pInsertionAllowed* qui ont été effacées à l’origine. Les versions futures de la console MMC peuvent utiliser bits pas actuellement définis afin de vous ne devez pas modifier les bits qui ne sont pas actuellement définis.  
  
##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo  
 Appelez cette fonction pour modifier les styles de bouton de barre d’outils, de l’objet composant logiciel enfichable, avant la création de la barre d’outils.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 [in] L’ID du bouton de barre d’outils à définir.  
  
 *fsState*  
 [in] Les indicateurs d’état du bouton. Peut être une ou plusieurs des opérations suivantes :  
  
- TBSTATE_CHECKED le bouton a le style TBSTYLE_CHECKED et est enfoncé.  
  
- Le bouton TBSTATE_ENABLED accepte les entrées utilisateur. Un bouton qui n’a pas de cet état n’accepte pas d’entrée d’utilisateur et est grisé.  
  
- TBSTATE_HIDDEN le bouton n’est pas visible et ne peut pas recevoir l’entrée d’utilisateur.  
  
- TBSTATE_INDETERMINATE le bouton est grisé.  
  
- TBSTATE_PRESSED le bouton est enfoncé.  
  
- Saut de ligne A TBSTATE_WRAP suit le bouton. Le bouton doit également avoir le TBSTATE_ENABLED.  
  
 *(fsType)*  
 [in] Les indicateurs d’état du bouton. Peut être une ou plusieurs des opérations suivantes :  
  
- TBSTYLE_BUTTON crée un bouton de commande standard.  
  
- TBSTYLE_CHECK crée un bouton qui fait basculer entre les États enfoncés et non-enfoncé chaque fois que l’utilisateur clique dessus. Le bouton a une couleur d’arrière-plan différente lorsqu’il est dans un état appuyé.  
  
- TBSTYLE_CHECKGROUP crée un bouton de vérification qui reste enfoncé jusqu'à ce que l’utilisateur appuie sur un autre bouton dans le groupe.  
  
- TBSTYLE_GROUP crée un bouton qui reste enfoncé jusqu'à ce que l’utilisateur appuie sur un autre bouton dans le groupe.  
  
- TBSTYLE_SEP crée un séparateur, en fournissant un petit intervalle entre les groupes de bouton. Un bouton qui a ce style ne reçoit pas d’entrée d’utilisateur.  
  
##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState  
 Appelez cette fonction pour modifier un élément de menu avant qu’il est inséré dans le menu contextuel de l’objet de composant logiciel enfichable.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 [in] ID de l’élément de menu à définir.  
  
 *pBuf*  
 [in] Pointeur vers la chaîne de l’élément de menu à mettre à jour.  
  
 *flags*  
 [in] Spécifie les indicateurs d’état. Cela peut être une combinaison des indicateurs suivants :  
  
- MF_POPUP Spécifie qu’il s’agit d’un sous-menu dans le menu contextuel. Éléments de menu, les points d’insertion et les sous-menus davantage peuvent être ajoutés à ce sous-menu à l’aide de son `lCommandID` en tant que leur `IInsertionPointID`.  
  
- MF_BITMAP et MF_OWNERDRAW ces indicateurs ne sont pas autorisés et provoqueront une valeur de retour de E_INVALIDARG.  
  
- MF_SEPARATOR Dessine une ligne de démarcation horizontale. Uniquement `IContextMenuProvider` est autorisé à ajouter des éléments de menu avec MF_SEPARATOR ensemble.  
  
- MF_CHECKED place une coche en regard de l’élément de menu.  
  
- MF_DISABLED désactive l’élément de menu afin qu’il ne peut pas être sélectionné, mais l’indicateur ne pas gris il.  
  
- MF_ENABLED permet à l’élément de menu afin qu’il peut être sélectionné, restaurant à partir de son état grisé.  
  
- MF_GRAYED désactive l’élément de menu, qui elle devient donc il ne peut pas être sélectionné.  
  
- Les fonctions MF_MENUBARBREAK identique à la MF_MENUBREAK indicateur pour une barre de menus. Pour un menu déroulant, un sous-menu ou un menu contextuel, la nouvelle colonne est l’ancienne colonne séparée par une ligne verticale.  
  
- MF_MENUBREAK place l’élément sur une nouvelle ligne (pour une barre de menus) ou dans une nouvelle colonne (pour un menu déroulant, un sous-menu ou un menu contextuel) sans séparation des colonnes.  
  
- MF_UNCHECKED pas impose une case à cocher en regard de l’élément (par défaut).  
  
 Les groupes d’indicateurs suivants ne peuvent pas être utilisés ensemble :  
  
- MF_DISABLED, MF_ENABLED et MF_GRAYED.  
  
- MF_MENUBARBREAK et MF_MENUBREAK.  
  
- MF_CHECKED et MF_UNCHECKED.  
  
##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton  
 Appelez cette fonction pour modifier un bouton de barre d’outils, de l’objet composant logiciel enfichable, avant son affichage.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 Spécifie l’ID de bouton du bouton de barre d’outils de mise à jour.  
  
 *fsState*  
 Spécifie un état du bouton de barre d’outils. Si cet état doit être défini, retourne la valeur TRUE. Cela peut être une combinaison des indicateurs suivants :  
  
- ACTIVÉ le bouton accepte l’entrée d’utilisateur. Un bouton qui n’a pas de cet état n’accepte pas d’entrée d’utilisateur et est grisé.  
  
- Vérifiez que le bouton a le style activé et est enfoncé.  
  
- HIDDEN le bouton n’est pas visible et ne peut pas recevoir l’entrée d’utilisateur.  
  
- Le bouton est grisé indéterminé.  
  
- BUTTONPRESSED le bouton est enfoncé.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
