---
title: CSnapInItemImpl, classe
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
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496547"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl, classe

Cette classe fournit des méthodes pour implémenter un objet de nœud de composant logiciel enfichable.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `CSnapInItemImpl`de.

*bIsExtension*<br/>
TRUE si l’objet est une extension de composant logiciel enfichable; Sinon, FALSe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Ajoute des éléments de menu à un menu contextuel.|
|[CSnapInItemImpl::Command](#command)|Appelé par la console lorsqu’un élément de menu personnalisé est sélectionné.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Ajoute des pages à la feuille de propriétés du composant logiciel enfichable.|
|[CSnapInItemImpl::FillData](#filldata)|Copie les informations sur l’objet de composant logiciel enfichable dans un flux de données spécifié.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Récupère la `RESULTDATAITEM` structure du composant logiciel enfichable.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Détermine le type de vue utilisé par le volet de résultats.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Récupère la `SCOPEDATAITEM` structure du composant logiciel enfichable.|
|[CSnapInItemImpl::Notify](#notify)|Appelé par la console pour notifier le composant logiciel enfichable des actions effectuées par l’utilisateur.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Appelé pour déterminer si le nœud de composant logiciel enfichable prend en charge les pages de propriétés.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifie les indicateurs d’insertion de menu pour un objet composant logiciel enfichable.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Définit les informations du bouton de barre d’outils spécifié.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Met à jour l’état d’un élément de menu contextuel.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Met à jour l’état du bouton de barre d’outils spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nom de l’objet de composant logiciel enfichable.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Structure Windows `RESULTDATAITEM` utilisée par l' `CSnapInItemImpl` objet.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Structure Windows `SCOPEDATAITEM` utilisée par l' `CSnapInItemImpl` objet.|

## <a name="remarks"></a>Notes

`CSnapInItemImpl`fournit une implémentation de base pour un objet de nœud de composant logiciel enfichable, comme l’ajout d’éléments de menu et de barres d’outils, et le transfert de commandes pour le nœud de composant logiciel enfichable vers la fonction de gestionnaire appropriée. Ces fonctionnalités sont implémentées à l’aide de différentes interfaces et types de mappages. L’implémentation par défaut gère les notifications envoyées à l’objet de nœud en déterminant l’instance correcte de la classe dérivée, puis en retransférant le message à l’instance correcte.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlsnap. h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

Cette méthode implémente la fonction Win32 [IExtendContextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*piCallback*<br/>
dans Pointeur vers le `IContextMenuCallback` qui peut ajouter des éléments au menu contextuel.

*pInsertionAllowed*<br/>
[in, out] Identifie les points d’insertion d’élément de menu définis par la console MMC (Microsoft Management Console), qui peuvent être utilisés. Il peut s’agir d’une combinaison des indicateurs suivants:

- Les éléments CCM_INSERTIONALLOWED_TOP peuvent être insérés en haut d’un menu contextuel.

- Vous pouvez insérer des éléments CCM_INSERTIONALLOWED_NEW dans le sous-menu créer.

- Les éléments CCM_INSERTIONALLOWED_TASK peuvent être insérés dans le sous-menu tâche.

- Les éléments CCM_INSERTIONALLOWED_VIEW peuvent être insérés dans le menu Affichage de la barre d’outils ou dans le sous-menu Affichage du menu contextuel du volet de résultats.

*type*<br/>
dans Spécifie le type d’objet. Il peut prendre l’une des valeurs suivantes:

- Objet de données CCT_SCOPE pour le contexte du volet d’étendue.

- Objet de données CCT_RESULT pour le contexte du volet de résultats.

- Objet de données CCT_SNAPIN_MANAGER pour le contexte du gestionnaire de composants logiciels enfichables.

- Le type de l’objet de données CCT_UNINITIALIZED n’est pas valide.

##  <a name="command"></a>  CSnapInItemImpl::Command

Cette méthode implémente la fonction Win32 [IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*lCommandID*<br/>
dans Spécifie l’identificateur de commande de l’élément de menu.

*type*<br/>
dans Spécifie le type d’objet. Il peut prendre l’une des valeurs suivantes:

- Objet de données CCT_SCOPE pour le contexte du volet d’étendue.

- Objet de données CCT_RESULT pour le contexte du volet de résultats.

- Objet de données CCT_SNAPIN_MANAGER pour le contexte du gestionnaire de composants logiciels enfichables.

- Le type de l’objet de données CCT_UNINITIALIZED n’est pas valide.

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

Cette méthode implémente la fonction Win32 [IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Paramètres

*lpProvider*<br/>
dans Pointeur vers l' `IPropertySheetCallback` interface.

*handle*<br/>
dans Spécifie le descripteur utilisé pour acheminer le message de notification MMCN_PROPERTY_CHANGE à la classe de données appropriée.

*pUnk*<br/>
dans Pointeur vers l' `IExtendPropertySheet` interface sur l’objet qui contient des informations de contexte sur le nœud.

*type*<br/>
dans Spécifie le type d’objet. Il peut prendre l’une des valeurs suivantes:

- Objet de données CCT_SCOPE pour le contexte du volet d’étendue.

- Objet de données CCT_RESULT pour le contexte du volet de résultats.

- Objet de données CCT_SNAPIN_MANAGER pour le contexte du gestionnaire de composants logiciels enfichables.

- Le type de l’objet de données CCT_UNINITIALIZED n’est pas valide.

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

Construit un objet `CSnapInItemImpl`.

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

Cette fonction est appelée pour extraire des informations sur l’élément.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Paramètres

*cf*<br/>
dans Format (texte, texte enrichi ou texte enrichi avec éléments OLE) du presse-papiers.

*pStream*<br/>
dans Pointeur vers le flux contenant les données d’objet.

### <a name="remarks"></a>Notes

Pour implémenter correctement cette fonction, copiez les informations correctes dans le flux (*pStream*), en fonction du format du presse-papiers indiqué par *CF*.

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

Appelez cette fonction pour récupérer le type de vue du volet de résultats de l’objet de composant logiciel enfichable.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Paramètres

*ppViewType*<br/>
à Pointeur vers l’adresse du type de vue retourné.

*pViewOptions*<br/>
à Pointeur vers l’énumération MMC_VIEW_OPTIONS, qui fournit la console avec les options spécifiées par le composant logiciel enfichable propriétaire. Cette valeur peut être l’une des suivantes:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 indique à la console de s’abstenir de présenter les choix de vue de liste standard dans le menu **affichage** . Permet au composant logiciel enfichable d’afficher ses propres vues personnalisées uniquement dans le volet affichage des résultats. Il s’agit du seul indicateur d’option défini à ce stade.

- MMC_VIEW_OPTIONS_NONE = 0 autorise les options d’affichage par défaut.

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

Appelez cette fonction pour récupérer la `SCOPEDATAITEM` structure du composant logiciel enfichable.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Paramètres

*pScopeDataItem*<br/>
à Pointeur vers la `SCOPEDATAITEM` structure de l' `CSnapInItemImpl` objet.

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

Appelez cette fonction pour récupérer la `RESULTDATAITEM` structure du composant logiciel enfichable.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Paramètres

*pResultDataItem*<br/>
à Pointeur vers la `RESULTDATAITEM` structure de l' `CSnapInItemImpl` objet.

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

Contient la chaîne affichée pour l’élément de nœud.

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM` Structure de l’objet de données du composant logiciel enfichable.

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

Structure [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) de l’objet de données du composant logiciel enfichable.

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

Appelé lorsque l’objet composant logiciel enfichable est traité par l’utilisateur.

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
dans Identifie une action entreprise par un utilisateur. Les notifications suivantes sont possibles:

- MMCN_ACTIVATE envoyé lorsqu’une fenêtre est activée et désactivée.

- MMCN_ADD_IMAGES envoyé pour ajouter des images au volet des résultats.

- MMCN_BTN_CLICK envoyé lorsque l’utilisateur clique sur l’un des boutons de la barre d’outils.

- MMCN_CLICK envoyé quand un utilisateur clique sur un bouton de la souris sur un élément de la vue liste.

- MMCN_DBLCLICK envoyé quand un utilisateur double-clique sur un bouton de la souris sur un élément de la vue liste.

- MMCN_DELETE envoyé pour informer le composant logiciel enfichable que l’objet doit être supprimé.

- MMCN_EXPAND envoyé lorsqu’un dossier doit être développé ou contracté.

- MMCN_MINIMIZED envoyé lorsqu’une fenêtre est réduite ou agrandie.

- MMCN_PROPERTY_CHANGE envoyé pour notifier un objet composant logiciel enfichable que la vue de l’objet composant logiciel enfichable va modifier.

- MMCN_REMOVE_CHILDREN envoyé lorsque le composant logiciel enfichable doit supprimer l’intégralité de la sous-arborescence qu’il a ajoutée sous le nœud spécifié.

- MMCN_RENAME a envoyé la première fois pour demander un changement de nom et la deuxième fois pour effectuer le changement de nom.

- MMCN_SELECT envoyé lorsqu’un élément du volet étendue ou affichage des résultats est sélectionné.

- MMCN_SHOW envoyé lorsqu’un élément d’étendue est sélectionné ou désélectionné pour la première fois.

- MMCN_VIEW_CHANGE envoyé lorsque le composant logiciel enfichable peut mettre à jour toutes les vues lorsqu’une modification se produit.

*arg*<br/>
dans Dépend du type de notification.

*param*<br/>
dans Dépend du type de notification.

*pComponentData*<br/>
à Pointeur vers l’objet qui implémente `IComponentData`. Ce paramètre a la valeur NULL si la notification n’est pas `IComponentData::Notify`transférée à partir de.

*pComponent*<br/>
à Pointeur vers l’objet qui implémente `IComponent`. Ce paramètre a la valeur NULL si la notification n’est pas `IComponent::Notify`transférée à partir de.

*type*<br/>
dans Spécifie le type d’objet. Il peut prendre l’une des valeurs suivantes:

- Objet de données CCT_SCOPE pour le contexte du volet d’étendue.

- Objet de données CCT_RESULT pour le contexte du volet de résultats.

- Objet de données CCT_SNAPIN_MANAGER pour le contexte du gestionnaire de composants logiciels enfichables.

- Le type de l’objet de données CCT_UNINITIALIZED n’est pas valide.

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

*bBeforeInsertion*<br/>
dans Différent de zéro si la fonction doit être appelée avant que les éléments ne soient ajoutés au menu contextuel; Sinon, 0.

*pInsertionAllowed*<br/>
[in, out] Identifie les points d’insertion d’élément de menu définis par la console MMC (Microsoft Management Console), qui peuvent être utilisés. Il peut s’agir d’une combinaison des indicateurs suivants:

- Les éléments CCM_INSERTIONALLOWED_TOP peuvent être insérés en haut d’un menu contextuel.

- Vous pouvez insérer des éléments CCM_INSERTIONALLOWED_NEW dans le sous-menu créer.

- Les éléments CCM_INSERTIONALLOWED_TASK peuvent être insérés dans le sous-menu tâche.

- Les éléments CCM_INSERTIONALLOWED_VIEW peuvent être insérés dans le menu Affichage de la barre d’outils ou dans le sous-menu Affichage du menu contextuel du volet de résultats.

### <a name="remarks"></a>Notes

Si vous développez un composant logiciel enfichable principal, vous pouvez réinitialiser tous les indicateurs d’insertion comme un moyen de limiter le type d’éléments de menu qu’une extension tierce peut ajouter. Par exemple, le composant logiciel enfichable principal peut effacer l’indicateur CCM_INSERTIONALLOWED_NEW pour empêcher les extensions d’ajouter leurs propres éléments de menu créer.

Vous ne devez pas essayer de définir des bits dans *pInsertionAllowed* qui ont été effacés à l’origine. Les futures versions de la console MMC peuvent utiliser des bits qui ne sont pas actuellement définis. par conséquent, vous ne devez pas modifier les bits qui ne sont pas actuellement définis.

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

Appelez cette fonction pour modifier tous les styles de boutons de barre d’outils, de l’objet de composant logiciel enfichable, avant la création de la barre d’outils.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans ID du bouton de barre d’outils à définir.

*fsState*<br/>
dans Indicateurs d’État du bouton. Il peut s’agir d’un ou plusieurs des éléments suivants:

- TBSTATE_CHECKED le bouton a le style TBSTYLE_CHECKED et est enfoncé.

- TBSTATE_ENABLED le bouton accepte l’intervention de l’utilisateur. Un bouton qui n’a pas cet État n’accepte pas les entrées d’utilisateur et est grisé.

- TBSTATE_HIDDEN le bouton n’est pas visible et ne peut pas recevoir d’entrée d’utilisateur.

- TBSTATE_INDETERMINATE le bouton est grisé.

- TBSTATE_PRESSED le bouton est enfoncé.

- TBSTATE_WRAP un saut de ligne suit le bouton. Le bouton doit également avoir le TBSTATE_ENABLED.

*fsType*<br/>
dans Indicateurs d’État du bouton. Il peut s’agir d’un ou plusieurs des éléments suivants:

- TBSTYLE_BUTTON crée un bouton de commande standard.

- TBSTYLE_CHECK crée un bouton qui bascule entre les États enfoncé et non enfoncé chaque fois que l’utilisateur clique dessus. Le bouton a une couleur d’arrière-plan différente lorsqu’il est dans un état appuyé.

- TBSTYLE_CHECKGROUP crée un bouton de vérification qui reste enfoncé jusqu’à ce qu’un autre bouton du groupe soit enfoncé.

- TBSTYLE_GROUP crée un bouton qui reste enfoncé jusqu’à ce qu’un autre bouton du groupe soit enfoncé.

- TBSTYLE_SEP crée un séparateur en fournissant un petit intervalle entre les groupes de boutons. Un bouton qui a ce style ne reçoit pas d’entrée d’utilisateur.

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

Appelez cette fonction pour modifier un élément de menu avant qu’il ne soit inséré dans le menu contextuel de l’objet composant logiciel enfichable.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans ID de l’élément de menu à définir.

*pBuf*<br/>
dans Pointeur vers la chaîne de l’élément de menu à mettre à jour.

*flags*<br/>
dans Spécifie les nouveaux indicateurs d’État. Il peut s’agir d’une combinaison des indicateurs suivants:

- MF_POPUP spécifie qu’il s’agit d’un sous-menu dans le menu contextuel. Les éléments de menu, les points d’insertion et d’autres sous-menus peuvent être ajoutés à ce `lCommandID` sous- `IInsertionPointID`menu à l’aide de son.

- MF_BITMAP et MF_OWNERDRAW ces indicateurs ne sont pas autorisés et entraînent la valeur de retour E_INVALIDARG.

- MF_SEPARATOR dessine une ligne de séparation horizontale. Seul `IContextMenuProvider` est autorisé à ajouter des éléments de menu avec MF_SEPARATOR Set.

- MF_CHECKED place une coche en regard de l’élément de menu.

- MF_DISABLED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné, mais l’indicateur ne le grise pas.

- MF_ENABLED active l’élément de menu pour qu’il puisse être sélectionné, en le restaurant de son état grisé.

- MF_GRAYED désactive l’élément de menu, en le grisant afin qu’il ne puisse pas être sélectionné.

- MF_MENUBARBREAK fonctionne de la même façon que l’indicateur MF_MENUBREAK pour une barre de menus. Dans le cas d’un menu déroulant, d’un sous-menu ou d’un menu contextuel, la nouvelle colonne est séparée de l’ancienne colonne par une ligne verticale.

- MF_MENUBREAK place l’élément sur une nouvelle ligne (pour une barre de menus) ou dans une nouvelle colonne (pour un menu déroulant, un sous-menu ou un menu contextuel) sans séparer les colonnes.

- MF_UNCHECKED ne place pas de coche en regard de l’élément (valeur par défaut).

Les groupes d’indicateurs suivants ne peuvent pas être utilisés ensemble:

- MF_DISABLED, MF_ENABLED et MF_GRAYED.

- MF_MENUBARBREAK et MF_MENUBREAK.

- MF_CHECKED et MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

Appelez cette fonction pour modifier un bouton de barre d’outils, de l’objet de composant logiciel enfichable, avant qu’il ne soit affiché.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
Spécifie l’ID du bouton de barre d’outils à mettre à jour.

*fsState*<br/>
Spécifie un état de bouton de barre d’outils. Si cet État doit être défini, retourne la valeur TRUE. Il peut s’agir d’une combinaison des indicateurs suivants:

- ACTIVÉ le bouton accepte les entrées utilisateur. Un bouton qui n’a pas cet État n’accepte pas les entrées d’utilisateur et est grisé.

- COCHÉ le bouton a le style coché et est enfoncé.

- MASQUÉ le bouton n’est pas visible et ne peut pas recevoir d’entrée d’utilisateur.

- INDÉTERMINÉ le bouton est grisé.

- BUTTONPRESSED le bouton est enfoncé.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
