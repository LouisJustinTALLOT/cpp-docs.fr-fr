---
title: COleDBRecordView, classe
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366101"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView, classe

Vue qui affiche des enregistrements de base de données dans des contrôles.

## <a name="syntax"></a>Syntaxe

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Construit un objet `COleDBRecordView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Retourne une valeur HRESULT standard.|
|[COleDBRecordView::OnMove](#onmove)|Mise à jour de l’enregistrement actuel (si sale) sur la source de données, puis passe à l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue `CRowset` de formulaire directement connectée à un objet. La vue est créée à partir d’une `CRowset` ressource de modèle de dialogue et affiche les champs de l’objet dans les contrôles du modèle de dialogue. L’objet `COleDBRecordView` utilise l’échange de données de dialogue (DDX), et la fonctionnalité de navigation intégrée, `CRowset`pour automatiser le mouvement des données entre les contrôles sur la forme et les champs de l’aviron. `COleDBRecordView`fournit également une implémentation par défaut pour passer à la première, suivante, précédente, ou dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement à l’affiche.

Vous pouvez utiliser les fonctions DDX pour `COleDbRecordView` obtenir des données directement à partir de l’enregistrement de base de données et les afficher dans un contrôle de dialogue. Vous devez `DDX_*` utiliser les `DDX_Text`méthodes (telles que ), pas les `DDX_Field*` fonctions (telles que `DDX_FieldText`) avec `COleDbRecordView`. `DDX_FieldText`ne fonctionnera `COleDbRecordView` pas `DDX_FieldText` avec parce que `CRecordset*` prend `CRecordView`un `CDaoRecordset*` argument `CDaoRecordView`supplémentaire de type (pour ) ou (pour ).

> [!NOTE]
> Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt qu’avec les classes OLE DB Consumer Template, utilisez plutôt la classe [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Pour plus d’informations, voir l’article [Aperçu: Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView`garde une trace de la position de l’utilisateur dans le jeu de lignes afin que la vue d’enregistrement puisse mettre à jour l’interface utilisateur. Lorsque l’utilisateur se déplace à l’une ou l’autre extrémité de la ligne, la vue d’enregistrement désactive les objets d’interface utilisateur — tels que les éléments de menu ou les boutons de barre d’outils — pour aller plus loin dans la même direction.

Pour plus d’informations sur les classes rowset, voir [l’article Using OLE DB Consumer Templates.](../../data/oledb/ole-db-consumer-templates-cpp.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView

Construit un objet `COleDBRecordView`.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de dialogue-modèle.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de dialogue.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet `COleDBRecordView`d’un type dérivé de , invoquez l’un des constructeurs pour créer l’objet de vue et identifier la ressource de dialogue sur laquelle la vue est basée. Vous pouvez identifier la ressource soit par son nom (passez une chaîne comme argument au constructeur) ou par sa pièce d’identité (passez un insignable non signé comme argument).

> [!NOTE]
> Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, invoquez le constructeur, `COleDBRecordView::COleDBRecordView`, avec le nom de ressource ou ID comme argument.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset

Retourne une poignée pour l’objet **<>CRowset** associé à la vue d’enregistrement.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez remplacer cette fonction de membre pour construire ou obtenir un objet encastré et y retourner une poignée. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’assistant vous écrit un remplacement par défaut. L’implémentation par défaut de ClassWizard renvoie la poignée rowset stockée dans la vue d’enregistrement si elle existe. Si ce n’est pas le cas, il construit un objet `Open` encastré du type que vous avez spécifié avec ClassWizard et appelle sa fonction de membre pour ouvrir la table ou exécuter la requête, puis renvoie une poignée à l’objet.

> [!NOTE]
> Avant MFC 7.0, `OnGetRowset` retourné `CRowset`un pointeur à . Si vous avez `OnGetRowset`du code qui appelle, vous devez modifier le type de retour à la classe templatisée **CRowset<>**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Pour plus d’informations et d’exemples, voir l’article [Affichages d’enregistrement: Utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove

Se déplace vers un enregistrement différent dans le rowset et affiche ses champs dans les commandes de la vue d’enregistrement.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand (en)*<br/>
L’une des valeurs d’identification de commande standard suivantes :

- ID_RECORD_FIRST — Passez au premier disque dans le dossier.

- ID_RECORD_LAST — Passez au dernier record dans le dossier.

- ID_RECORD_NEXT — Passez au prochain disque dans le dossier.

- ID_RECORD_PREV — Passez au record précédent dans le dossier.

### <a name="return-value"></a>Valeur de retour

Nonzero si le déménagement a été un succès; autrement 0 si la demande de déménagement a été refusée.

### <a name="remarks"></a>Notes

La mise en `Move` œuvre `CRowset` par défaut appelle la fonction membre appropriée de l’objet associé à la vue d’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement actuel sur la source de données si l’utilisateur l’a modifié dans la vue d’enregistrement.

L’Assistant d’application crée une ressource de menu avec First Record, Last Record, Next Record et Les éléments de menu Précédent Record. Si vous sélectionnez l’option Dockable Toolbar, The Application Wizard crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous passez au-delà du dernier enregistrement dans le recordet, la vue d’enregistrement continue d’afficher le dernier enregistrement. Si vous reculez au-delà du premier enregistrement, la vue d’enregistrement continue d’afficher le premier enregistrement.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
