---
title: COleDBRecordView (classe)
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
ms.openlocfilehash: 1b09599479010f87e396e6f576c9524651923f9f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341717"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView (classe)

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
|[COleDBRecordView::OnMove](#onmove)|Met à jour l’enregistrement en cours (si « Dirty ») sur la source de données, puis les déplace vers l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue de formulaire directement connectée à un `CRowset` objet. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue. Le `COleDBRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et la fonctionnalité de navigation intégrée à `CRowset`, pour automatiser le déplacement des données entre les contrôles sur le formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` fournit également une implémentation par défaut pour le déplacement vers le premier, suivant, précédent ou le dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement dans la vue.

Vous pouvez utiliser des fonctions DDX avec `COleDbRecordView` pour obtenir des données directement à partir de l’ensemble d’enregistrements de base de données et les afficher dans un contrôle de boîte de dialogue. Vous devez utiliser le `DDX_*` méthodes (telles que `DDX_Text`), et non le `DDX_Field*` fonctions (telles que `DDX_FieldText`) avec `COleDbRecordView`. `DDX_FieldText` ne fonctionne pas avec `COleDbRecordView` car `DDX_FieldText` prend un argument supplémentaire de type `CRecordset*` (pour `CRecordView`) ou `CDaoRecordset*` (pour `CDaoRecordView`).

> [!NOTE]
>  Si vous travaillez avec les classes d’objets DAO (Data Access) plutôt que les classes de modèle de consommateur OLE DB, utilisez la classe [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView` effectue le suivi de position de l’utilisateur dans l’ensemble de lignes afin que la vue de l’enregistrement peut mettre à jour l’interface utilisateur. Lorsque l’utilisateur se déplace vers chaque extrémité de l’ensemble de lignes, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou des boutons de barre d’outils, de déplacement plus en détail dans la même direction.

Pour plus d’informations sur les classes de l’ensemble de lignes, consultez le [à l’aide de OLE DB modèles du consommateur](../../data/oledb/ole-db-consumer-templates-cpp.md) article.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

Construit un objet `COleDBRecordView`.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet d’un type dérivé `COleDBRecordView`, appeler un des constructeurs pour créer l’objet de vue et d’identifier la ressource de boîte de dialogue sur laquelle repose la vue. Vous pouvez identifier la ressource par son nom (passez une chaîne comme argument au constructeur) ou par son ID (pass un entier non signé comme argument).

> [!NOTE]
>  Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, appelez le constructeur, `COleDBRecordView::COleDBRecordView`, avec le nom de la ressource ou l’ID en tant qu’argument.

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

Retourne un handle pour le **CRowset <>** objet associé à la vue de l’enregistrement.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez substituer cette fonction membre pour créer ou obtenir un objet d’ensemble de lignes et de retourner un handle à ce dernier. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’Assistant écrit une valeur de remplacement par défaut pour vous. Implémentation par défaut de ClassWizard retourne le handle de l’ensemble de lignes stocké dans la vue de l’enregistrement s’il en existe. Si non, il construit un objet d’ensemble de lignes du type que vous avez spécifié avec ClassWizard et appelle son `Open` membre de fonction pour ouvrir la table ou exécuter la requête, puis retourne un handle vers l’objet.

> [!NOTE]
>  Antérieures à 7.0 MFC, `OnGetRowset` retourné un pointeur vers `CRowset`. Si vous avez du code qui appelle `OnGetRowset`, vous devez modifier le type de retour à la classe modélisée **CRowset <>**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Pour plus d’informations et des exemples, consultez l’article [vues d’enregistrements : À l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  COleDBRecordView::OnMove

Afficher de ses champs dans les contrôles de l’enregistrement se déplace vers un autre enregistrement dans l’ensemble de lignes et l’affichage.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand*<br/>
Une des valeurs d’ID de commande standard suivantes :

- ID_RECORD_FIRST — Déplacer vers le premier enregistrement dans le jeu d’enregistrements.

- ID_RECORD_LAST — Déplacer au dernier enregistrement dans le jeu d’enregistrements.

- ID_RECORD_NEXT — Déplacer vers l’enregistrement suivant dans le jeu d’enregistrements.

- ID_RECORD_PREV — Déplacer vers l’enregistrement précédent dans le jeu d’enregistrements.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le déplacement a réussi ; Sinon, 0 si la demande de déplacement a été refusée.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle approprié `Move` fonction membre de la `CRowset` objet associé à la vue de l’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement en cours sur la source de données si l’utilisateur a été modifié dans la vue de l’enregistrement.

L’Assistant Application crée une ressource de menu avec les éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option de la barre d’outils ancrable, l’Assistant Application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous déplacez au-delà du dernier enregistrement dans le jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous déplacez vers l’arrière au-delà du premier enregistrement, la vue de l’enregistrement continue à afficher le premier enregistrement.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
