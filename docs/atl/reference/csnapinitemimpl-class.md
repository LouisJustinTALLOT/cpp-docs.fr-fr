---
title: Classe CSnapInItemImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 04eeba0239789b9f3220b7bfece3eb41dc7f2826
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746424"
---
# <a name="csnapinitemimpl-class"></a>Classe CSnapInItemImpl

Cette classe fournit des méthodes pour la mise en œuvre d’un objet de nœuds accrocheur.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `CSnapInItemImpl`dérivée de .

*bIsExtension (en anglais)*<br/>
VRAI si l’objet est une extension snap-in; autrement FALSE.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Ajoute des éléments de menu à un menu contextuelle.|
|[CSnapInItemImpl::Commande](#command)|Appelé par la console lorsqu’un élément de menu personnalisé est sélectionné.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Ajoute des pages à la feuille de propriété du snap-in.|
|[CSnapInItemImpl::FillData](#filldata)|Copiez les informations sur l’objet de saisie dans un flux spécifié.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Récupère la `RESULTDATAITEM` structure du snap-in.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Détermine le type de vue utilisé par le volet résultat.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Récupère la `SCOPEDATAITEM` structure du snap-in.|
|[CSnapInItemImpl::Notifier](#notify)|Appelé par la console pour informer le snap-in des actions prises par l’utilisateur.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Appelé pour voir si le nœud snap-in prend en charge les pages de propriété.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifie les indicateurs d’insertion du menu pour un objet accrocheur.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Définit les informations du bouton de barre d’outils spécifié.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Mise à jour de l’état d’un élément de menu contextuelle.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Mise à jour de l’état du bouton de barre d’outils spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Le nom de l’objet de snap-in.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|La `RESULTDATAITEM` structure Windows `CSnapInItemImpl` utilisée par l’objet.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|La `SCOPEDATAITEM` structure Windows `CSnapInItemImpl` utilisée par l’objet.|

## <a name="remarks"></a>Notes

`CSnapInItemImpl`fournit une implémentation de base pour un objet de nœud accrocheur, comme l’ajout d’éléments de menu et de barres d’outils, et l’ensecheminement des commandes pour le nœud en rupture avec la fonction de gestionnaire appropriée. Ces fonctionnalités sont implémentées à l’aide de plusieurs interfaces et types de cartes différents. L’implémentation par défaut gère les notifications envoyées à l’objet de nœud en déterminant le bon exemple de la classe dérivée, puis en transmettant le message à la bonne instance.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems

Cette méthode implémente la fonction Win32 [IExtendContextMenu::AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*piCallback piCallback*<br/>
[dans] Pointeur `IContextMenuCallback` sur le qui peut ajouter des éléments au menu contexte.

*pInsertionAllowed*<br/>
[dans, dehors] Identifie les points d’insertion définis par microsoft Console (MMC) qui peuvent être utilisés. Il peut s’agir d’une combinaison des drapeaux suivants :

- CCM_INSERTIONALLOWED_TOP Articles peuvent être insérés en haut d’un menu contextuelle.

- CCM_INSERTIONALLOWED_NEW Articles peuvent être insérés dans le sous-mois Créer un nouveau.

- CCM_INSERTIONALLOWED_TASK Articles peuvent être insérés dans le sous-groupe de la tâche.

- CCM_INSERTIONALLOWED_VIEW Les articles peuvent être insérés dans le menu de vue de la barre d’outils ou dans le sous-présage View du menu de contexte de la vitre de résultat.

*type*<br/>
[dans] Spécifie le type d’objet. Elle peut avoir l’une des valeurs suivantes :

- CCT_SCOPE objet de données pour le contexte de la portée.

- CCT_RESULT objet de données pour le contexte de la vitre des résultats.

- CCT_SNAPIN_MANAGER objet de données pour le contexte du gestionnaire instantané.

- CCT_UNINITIALIZED l’objet de données a un type invalide.

## <a name="csnapinitemimplcommand"></a><a name="command"></a>CSnapInItemImpl::Commande

Cette méthode implémente la fonction Win32 [IExtendContextMenu::Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*lCommandID*<br/>
[dans] Spécifie l’identifiant de commande de l’élément de menu.

*type*<br/>
[dans] Spécifie le type d’objet. Elle peut avoir l’une des valeurs suivantes :

- CCT_SCOPE objet de données pour le contexte de la portée.

- CCT_RESULT objet de données pour le contexte de la vitre des résultats.

- CCT_SNAPIN_MANAGER objet de données pour le contexte du gestionnaire instantané.

- CCT_UNINITIALIZED l’objet de données a un type invalide.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

Cette méthode implémente la fonction Win32 [IExtendPropertySheet::CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*lpProvider*<br/>
[in] Pointeur vers l'interface `IPropertySheetCallback`.

*Poignée*<br/>
[dans] Spécifie la poignée utilisée pour acheminer le message de notification MMCN_PROPERTY_CHANGE à la classe de données appropriée.

*Punk*<br/>
[dans] Pointeur `IExtendPropertySheet` vers l’interface de l’objet qui contient des informations contextuelles sur le nœud.

*type*<br/>
[dans] Spécifie le type d’objet. Elle peut avoir l’une des valeurs suivantes :

- CCT_SCOPE objet de données pour le contexte de la portée.

- CCT_RESULT objet de données pour le contexte de la vitre des résultats.

- CCT_SNAPIN_MANAGER objet de données pour le contexte du gestionnaire instantané.

- CCT_UNINITIALIZED l’objet de données a un type invalide.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

Construit un objet `CSnapInItemImpl`.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>CSnapInItemImpl::FillData

Cette fonction est appelée pour récupérer des informations sur l’élément.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
[dans] Le format (texte, texte riche ou texte riche avec des éléments OLE) du Clipboard.

*pStream*<br/>
[dans] Un pointeur sur le flux contenant les données de l’objet.

### <a name="remarks"></a>Notes

Pour implémenter correctement cette fonction, copiez les informations correctes dans le flux (*pStream*), selon le format Clipboard indiqué par *cf*.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

Appelez cette fonction pour récupérer le type de vue pour la vitre de résultat de l’objet snap-in.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Paramètres

*ppViewType*<br/>
[out] Pointeur à l’adresse du type de vue retourné.

*pViewOptions*<br/>
[out] Pointeur vers le MMC_VIEW_OPTIONS’énumération, qui fournit à la console des options spécifiées par le snap-in propriétaire. Cette valeur peut être l'une des suivantes :

- MMC_VIEW_OPTIONS_NOLISTVIEWS 0x0000001 indique à la console de s’abstenir de présenter des choix de vue de liste standard dans le menu **View.** Permet au snap-in d’afficher ses propres vues personnalisées uniquement dans la vitre de vue de résultat. C’est le seul drapeau d’option défini pour le moment.

- MMC_VIEW_OPTIONS_NONE 0 Permet les options de vue par défaut.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Appelez cette fonction `SCOPEDATAITEM` pour récupérer la structure du snap-in.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Paramètres

*pScopeDataItem (en)*<br/>
[out] Un pointeur `SCOPEDATAITEM` à `CSnapInItemImpl` la structure de l’objet.

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Appelez cette fonction `RESULTDATAITEM` pour récupérer la structure du snap-in.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Paramètres

*pResultDataItem*<br/>
[out] Un pointeur `RESULTDATAITEM` à `CSnapInItemImpl` la structure de l’objet.

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Contient la chaîne affichée pour l’élément nœud.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

La `SCOPEDATAITEM` structure de l’objet de données snap-in.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

La structure [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) de l’objet de données snap-in.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>CSnapInItemImpl::Notifier

Appelé lorsque l’objet de snap-in est agi par l’utilisateur.

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

*event*<br/>
[dans] Identifie une action prise par un utilisateur. Les notifications suivantes sont possibles :

- MMCN_ACTIVATE Envoyé lorsqu’une fenêtre est activée et désactivée.

- MMCN_ADD_IMAGES Envoyé pour ajouter des images à la vitre de résultat.

- MMCN_BTN_CLICK Envoyé lorsque l’utilisateur clique sur l’un des boutons de la barre d’outils.

- MMCN_CLICK Envoyé lorsqu’un utilisateur clique sur un bouton de souris sur un élément de vue de liste.

- MMCN_DBLCLICK Envoyé lorsqu’un utilisateur double clique sur un bouton de souris sur un élément de vue de liste.

- MMCN_DELETE Envoyé pour informer le snap-in que l’objet doit être supprimé.

- MMCN_EXPAND Envoyé lorsqu’un dossier doit être agrandi ou contracté.

- MMCN_MINIMIZED Envoyé lorsqu’une fenêtre est réduite au minimum ou maximisée.

- MMCN_PROPERTY_CHANGE Envoyé pour aviser un objet instantané que la vue de l’objet de snap-in est sur le point de changer.

- MMCN_REMOVE_CHILDREN Envoyé lorsque le snap-in doit supprimer l’ensemble du sous-ensemble, il a ajouté ci-dessous le nœud spécifié.

- MMCN_RENAME Envoyé la première fois à la requête pour un changement de nom et la deuxième fois pour faire le changement de nom.

- MMCN_SELECT Envoyé lorsqu’un élément dans le volet de vue de portée ou de résultat est sélectionné.

- MMCN_SHOW Envoyé lorsqu’un élément de portée est sélectionné ou désélectionné pour la première fois.

- MMCN_VIEW_CHANGE Envoyé lorsque le snap-in peut mettre à jour toutes les vues lorsqu’un changement se produit.

*Arg*<br/>
[dans] Dépend du type de notification.

*Param*<br/>
[dans] Dépend du type de notification.

*pComponentData*<br/>
[out] Un pointeur à `IComponentData`la mise en œuvre de l’objet . Ce paramètre est NULL si la `IComponentData::Notify`notification n’est pas transmise à partir de .

*pComponent*<br/>
[out] Un pointeur à l’objet qui met `IComponent`en œuvre . Ce paramètre est NULL si la `IComponent::Notify`notification n’est pas transmise à partir de .

*type*<br/>
[dans] Spécifie le type d’objet. Elle peut avoir l’une des valeurs suivantes :

- CCT_SCOPE objet de données pour le contexte de la portée.

- CCT_RESULT objet de données pour le contexte de la vitre des résultats.

- CCT_SNAPIN_MANAGER objet de données pour le contexte du gestionnaire instantané.

- CCT_UNINITIALIZED l’objet de données a un type invalide.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

Appelé pour voir si le nœud snap-in prend en charge les pages de propriété.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

Appelez cette fonction pour modifier les indicateurs d’insertion du menu, spécifiés par *pInsertionAllowed*, pour l’objet snap-in.

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Paramètres

*bDeinestinsertion*<br/>
[dans] Nonzero si la fonction doit être appelée avant que les éléments soient ajoutés au menu de contexte ; sinon 0.

*pInsertionAllowed*<br/>
[dans, dehors] Identifie les points d’insertion définis par microsoft Console (MMC) qui peuvent être utilisés. Il peut s’agir d’une combinaison des drapeaux suivants :

- CCM_INSERTIONALLOWED_TOP Articles peuvent être insérés en haut d’un menu contextuelle.

- CCM_INSERTIONALLOWED_NEW Articles peuvent être insérés dans le sous-mois Créer un nouveau.

- CCM_INSERTIONALLOWED_TASK Articles peuvent être insérés dans le sous-groupe de la tâche.

- CCM_INSERTIONALLOWED_VIEW Les articles peuvent être insérés dans le menu de vue de la barre d’outils ou dans le sous-présage View du menu de contexte de la vitre de résultat.

### <a name="remarks"></a>Notes

Si vous développez un snap-in primaire, vous pouvez réinitialiser l’un des drapeaux d’insertion comme un moyen de restreindre le type d’éléments de menu qu’une extension tierce peut ajouter. Par exemple, le snap-in primaire peut effacer le drapeau CCM_INSERTIONALLOWED_NEW pour empêcher les extensions d’ajouter leurs propres éléments de menu Créer de nouveaux.

Vous ne devriez pas essayer de définir des bits dans *pInsertionAllowed* qui ont été initialement effacés. Les versions futures de MMC peuvent utiliser des bits qui ne sont pas définis actuellement, vous ne devriez donc pas modifier les bits qui ne sont pas définis actuellement.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Appelez cette fonction pour modifier tous les styles de bouton de barre d’outils, de l’objet de snap-in, avant que la barre d’outils soit créée.

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’ID du bouton de la barre d’outils à régler.

*fsState (États-Unis)*<br/>
[dans] Les drapeaux d’état du bouton. Peut être un ou plusieurs des éléments suivants :

- TBSTATE_CHECKED Le bouton a le style TBSTYLE_CHECKED et est pressé.

- TBSTATE_ENABLED Le bouton accepte l’entrée de l’utilisateur. Un bouton qui n’a pas cet état n’accepte pas l’entrée de l’utilisateur et est grisé.

- TBSTATE_HIDDEN Le bouton n’est pas visible et ne peut pas recevoir d’entrée utilisateur.

- TBSTATE_INDETERMINATE Le bouton est grisé.

- TBSTATE_PRESSED Le bouton est pressé.

- TBSTATE_WRAP Une rupture de ligne suit le bouton. Le bouton doit également avoir la TBSTATE_ENABLED.

*fsType*<br/>
[dans] Les drapeaux d’état du bouton. Peut être un ou plusieurs des éléments suivants :

- TBSTYLE_BUTTON crée un bouton poussoir standard.

- TBSTYLE_CHECK crée un bouton qui bascule entre les états pressés et non pressés chaque fois que l’utilisateur clique dessus. Le bouton a une couleur de fond différente quand il est dans l’état pressé.

- TBSTYLE_CHECKGROUP crée un bouton de contrôle qui reste pressé jusqu’à ce qu’un autre bouton dans le groupe soit pressé.

- TBSTYLE_GROUP crée un bouton qui reste pressé jusqu’à ce qu’un autre bouton dans le groupe soit pressé.

- TBSTYLE_SEP crée un séparateur, fournissant un petit espace entre les groupes de boutons. Un bouton qui a ce style ne reçoit pas l’entrée de l’utilisateur.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Appelez cette fonction pour modifier un élément de menu avant qu’il ne soit inséré dans le menu contextuelle de l’objet snap-in.

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’ID de l’élément de menu à définir.

*pBuf (pBuf)*<br/>
[dans] Un pointeur à la chaîne pour l’élément de menu à mettre à jour.

*flags*<br/>
[dans] Spécifie les nouveaux drapeaux de l’État. Il peut s’agir d’une combinaison des drapeaux suivants :

- MF_POPUP précise qu’il s’agit d’un sous-mois dans le menu du contexte. Des éléments de menu, des points d’insertion et d’autres sous-hommes peuvent être ajoutés à ce sous-mois en utilisant son `lCommandID` comme leur `IInsertionPointID`.

- MF_BITMAP et MF_OWNERDRAW Ces drapeaux ne sont pas autorisés et se traduiront par une valeur de retour de E_INVALIDARG.

- MF_SEPARATOR dessine une ligne de démarcation horizontale. Il `IContextMenuProvider` est seulement permis d’ajouter des éléments de menu avec MF_SEPARATOR ensemble.

- MF_CHECKED Place une marque de contrôle à côté de l’élément menu.

- MF_DISABLED désactive l’élément de menu de sorte qu’il ne peut pas être sélectionné, mais le drapeau ne le grisonne pas.

- MF_ENABLED permet l’élément de menu afin qu’il puisse être sélectionné, le restaurer à partir de son état grisé.

- MF_GRAYED désactive l’élément de menu, le grisonnement afin qu’il ne puisse pas être sélectionné.

- MF_MENUBARBREAK fonctions de la même que le drapeau MF_MENUBREAK pour une barre de menu. Pour un menu déroulant, un sous-menu ou un menu raccourci, la nouvelle colonne est séparée de l’ancienne colonne par une ligne verticale.

- MF_MENUBREAK Place l’article sur une nouvelle ligne (pour une barre de menu) ou dans une nouvelle colonne (pour un menu déroulant, un sous-menu ou un menu raccourci) sans séparer les colonnes.

- MF_UNCHECKED Ne place pas de point de contrôle à côté de l’élément (par défaut).

Les groupes de drapeaux suivants ne peuvent pas être utilisés ensemble :

- MF_DISABLED, MF_ENABLED et MF_GRAYED.

- MF_MENUBARBREAK et MF_MENUBREAK.

- MF_CHECKED et MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Appelez cette fonction pour modifier un bouton de barre d’outils, de l’objet de snap-in, avant qu’il ne soit affiché.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
Spécifie l’ID bouton du bouton de la barre d’outils à mettre à jour.

*fsState (États-Unis)*<br/>
Spécifie un état de bouton de barre d’outils. Si cet état doit être défini, retournez VRAI. Il peut s’agir d’une combinaison des drapeaux suivants :

- ENABLED Le bouton accepte l’entrée de l’utilisateur. Un bouton qui n’a pas cet état n’accepte pas l’entrée de l’utilisateur et est grisé.

- CHECKED Le bouton a le style CHECKED et est pressé.

- HIDDEN Le bouton n’est pas visible et ne peut pas recevoir l’entrée de l’utilisateur.

- INDETERMINATE Le bouton est grisé.

- BUTTONPRESSED Le bouton est pressé.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
