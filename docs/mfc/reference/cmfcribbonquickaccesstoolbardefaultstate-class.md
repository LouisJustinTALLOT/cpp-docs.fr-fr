---
title: CMFCRibbonQuickAccessToolBarDefault Classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 56219e8ed1833f4b448ec6ffd3c16e9db3c66ada
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368870"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefault Classe

Une classe d’aide qui gère l’état par défaut pour la barre d’outils d’accès rapide qui est positionnée sur la barre de ruban [(classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)).

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
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Ajoute une commande à l’état par défaut pour la barre d’outils d’accès rapide. Cela ne change pas la barre d’outils elle-même.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyDe](#copyfrom)|Copie les propriétés d’une barre d’outils d’accès rapide à une autre.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Supprime toutes les commandes de la barre d’outils d’accès rapide. Cela ne change pas la barre d’outils elle-même.|

## <a name="remarks"></a>Notes

Après avoir créé la barre d’outils d’accès rapide dans votre application, nous vous recommandons de définir son état par défaut en appelant [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Cet état par défaut est rétabli lorsqu’un utilisateur clique sur le bouton **Reset** sur la page **Personnaliser la** page de dialogue **Options** de votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCRibbonQuickAccessToolbarDefaultState` un objet de la classe et comment ajouter une commande à l’état par défaut pour la barre d’outils d’accès rapide.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonquickaccesstoolbar.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Ajoute une commande à l’état par défaut pour la barre d’outils d’accès rapide.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*[en] uiCmd*<br/>
Spécifie l’id de commande.

*[en] bIsVisible*<br/>
Définit la visibilité de la commande lorsque la barre d’outils d’accès rapide est dans l’état par défaut.

### <a name="remarks"></a>Notes

L’ajout d’une commande au CMFCRibbonQuickAccessToolBarDefaultState réalise trois résultats. Tout d’abord, chaque commande ajoutée est répertoriée sur le dropdown sur le côté droit de la barre d’outils d’accès rapide. De cette façon, un utilisateur peut facilement ajouter ou supprimer cette commande de la barre d’outils d’accès rapide. Deuxièmement, la barre d’outils d’accès rapide est réinitialisée pour afficher uniquement les commandes qui sont répertoriées comme visibles dans l’état par défaut lorsque l’utilisateur clique sur le bouton **Reset** dans la boîte de dialogue **Personnaliser.** Troisièmement, si vous n’avez pas appelé [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barre d’outils d’accès rapide utilise les commandes visibles de cette liste que les commandes visibles par défaut la première fois qu’un utilisateur exécute votre application. Après avoir ajouté toutes les commandes que vous voulez, appelez [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) pour définir cette instance comme l’état par défaut pour la barre d’outils d’accès rapide de cette barre de ruban.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyDe

Copie les propriétés d’une barre d’outils d’accès rapide à une autre.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Une référence à `CMFCRibbonQuickAccessToolBarDefaultState` l’objet source à copier.

### <a name="remarks"></a>Notes

Cette méthode copie chaque `CMFCRibbonQuickAccessToolBarDefaultState` commande de l’objet source à cet objet en utilisant la [méthode CMFCRibbonQuickAccessToolBarDefault : :AddCommand](#addcommand) méthode.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Construit l’objet d’état par défaut de la barre d’outils d’accès rapide.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Notes

Par défaut, la liste des commandes que contient la nouvelle instance de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) est vide.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Efface la liste des commandes par défaut dans la barre d’outils d’accès rapide.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Cette fonction supprime de cette instance toutes les commandes que les appels précédents à [CMFCRibbonQuickAccessToolBarDefaultState:AddCommand](#addcommand) ajouté.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
