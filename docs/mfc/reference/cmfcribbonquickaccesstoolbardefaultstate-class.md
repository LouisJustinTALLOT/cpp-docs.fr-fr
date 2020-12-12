---
description: 'En savoir plus sur : classe CMFCRibbonQuickAccessToolBarDefaultState'
title: CMFCRibbonQuickAccessToolBarDefaultState, classe
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
ms.openlocfilehash: d6cd0c32cd8698259de0a78a6a6a7dc42012e92f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321798"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState, classe

Classe d’assistance qui gère l’État par défaut de la barre d’outils accès rapide positionnée sur la barre de ruban ( [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)).

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
|[CMFCRibbonQuickAccessToolBarDefaultState :: AddCommand](#addcommand)|Ajoute une commande à l’État par défaut pour la barre d’outils accès rapide. Cela ne modifie pas la barre d’outils elle-même.|
|[CMFCRibbonQuickAccessToolBarDefaultState :: CopyFrom](#copyfrom)|Copie les propriétés d’une barre d’outils accès rapide vers une autre.|
|[CMFCRibbonQuickAccessToolBarDefaultState :: RemoveAll](#removeall)|Supprime toutes les commandes de la barre d’outils accès rapide. Cela ne modifie pas la barre d’outils elle-même.|

## <a name="remarks"></a>Notes

Après avoir créé la barre d’outils accès rapide dans votre application, nous vous recommandons de définir son état par défaut en appelant [CMFCRibbonBar :: SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Cet État par défaut est rétabli lorsqu’un utilisateur clique sur le bouton **Réinitialiser** dans la page **personnaliser** de la boîte de dialogue **options** de votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCRibbonQuickAccessToolbarDefaultState` classe et comment ajouter une commande à l’État par défaut pour la barre d’outils accès rapide.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxribbonquickaccesstoolbar. h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a> CMFCRibbonQuickAccessToolBarDefaultState :: AddCommand

Ajoute une commande à l’État par défaut pour la barre d’outils accès rapide.

```cpp
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Paramètres

*[in] uiCmd*<br/>
Spécifie l’ID de la commande.

*[in] bIsVisible*<br/>
Définit la visibilité de la commande lorsque la barre d’outils accès rapide est dans l’État par défaut.

### <a name="remarks"></a>Notes

L’ajout d’une commande à CMFCRibbonQuickAccessToolBarDefaultState accomplit trois résultats. Tout d’abord, chaque commande ajoutée s’affiche dans la liste déroulante à droite de la barre d’outils accès rapide. De cette manière, un utilisateur peut facilement ajouter ou supprimer cette commande à partir de la barre d’outils accès rapide. Deuxièmement, la barre d’outils accès rapide est réinitialisée pour afficher uniquement les commandes répertoriées comme visibles dans l’État par défaut quand l’utilisateur clique sur le bouton **Réinitialiser** dans la boîte de dialogue **personnaliser** . Troisièmement, si vous n’avez pas appelé [CMFCRibbonBar :: SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), la barre d’outils accès rapide utilise les commandes visibles de cette liste comme commandes visibles par défaut la première fois qu’un utilisateur exécute votre application. Après avoir ajouté toutes les commandes souhaitées, appelez [CMFCRibbonBar :: SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) pour définir cette instance comme État par défaut de la barre d’outils accès rapide de cette barre de ruban.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a> CMFCRibbonQuickAccessToolBarDefaultState :: CopyFrom

Copie les propriétés d’une barre d’outils accès rapide vers une autre.

```cpp
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Référence à l’objet source `CMFCRibbonQuickAccessToolBarDefaultState` à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Cette méthode copie chaque commande de l' `CMFCRibbonQuickAccessToolBarDefaultState` objet source vers cet objet à l’aide de la méthode [CMFCRibbonQuickAccessToolBarDefaultState :: AddCommand](#addcommand) .

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a> CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Construit l’objet d’État par défaut de la barre d’outils accès rapide.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Notes

Par défaut, la liste des commandes que la nouvelle instance de [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) contient est vide.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a> CMFCRibbonQuickAccessToolBarDefaultState :: RemoveAll

Efface la liste des commandes par défaut dans la barre d’outils accès rapide.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Cette fonction supprime de cette instance toutes les commandes ajoutées par les appels précédents à [CMFCRibbonQuickAccessToolBarDefaultState :: AddCommand](#addcommand) .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
