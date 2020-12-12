---
description: 'En savoir plus sur : COleDBRecordView, classe'
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
ms.openlocfilehash: bce03a482aff558ed6d22c7720ff74f304a9214f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227310"
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
|[COleDBRecordView :: COleDBRecordView](#coledbrecordview)|Construit un objet `COleDBRecordView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDBRecordView :: OnGetRowset](#ongetrowset)|Retourne une valeur HRESULT standard.|
|[COleDBRecordView :: OnMove](#onmove)|Met à jour l’enregistrement actif (s’il a été modifié) sur la source de données, puis se déplace vers l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue de formulaire directement connectée à un `CRowset` objet. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de l' `CRowset` objet dans les contrôles du modèle de boîte de dialogue. L' `COleDBRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et les fonctionnalités de navigation intégrées `CRowset` à pour automatiser le déplacement des données entre les contrôles du formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` fournit également une implémentation par défaut pour le passage au premier enregistrement, suivant, précédent ou dernier, ainsi qu’une interface pour la mise à jour de l’enregistrement actuellement affiché.

Vous pouvez utiliser les fonctions DDX avec `COleDbRecordView` pour obtenir des données directement à partir de l’ensemble d’enregistrements de la base de données et les afficher dans un contrôle de boîte de dialogue. Vous devez utiliser les `DDX_*` méthodes (telles que `DDX_Text` ), et non les `DDX_Field*` fonctions (telles que `DDX_FieldText` ) avec `COleDbRecordView` . `DDX_FieldText` ne fonctionne pas avec `COleDbRecordView` , car `DDX_FieldText` accepte un argument supplémentaire de type `CRecordset*` (pour `CRecordView` ) ou `CDaoRecordset*` (pour `CDaoRecordView` ).

> [!NOTE]
> Si vous utilisez les classes DAO (Data Access Objects) au lieu des classes de modèle de consommateur OLE DB, utilisez à la place la classe [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView` effectue le suivi de la position de l’utilisateur dans l’ensemble de lignes afin que la vue d’enregistrement puisse mettre à jour l’interface utilisateur. Lorsque l’utilisateur passe à l’une des extrémités de l’ensemble de lignes, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou les boutons de barre d’outils, pour se déplacer dans la même direction.

Pour plus d’informations sur les classes d’ensemble de lignes, consultez l’article [utilisation de modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxoledb. h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a> COleDBRecordView :: COleDBRecordView

Construit un objet `COleDBRecordView`.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Quand vous créez un objet d’un type dérivé de `COleDBRecordView` , appelez l’un des constructeurs pour créer l’objet de vue et identifier la ressource de boîte de dialogue sur laquelle la vue est basée. Vous pouvez identifier la ressource par son nom (passer une chaîne en tant qu’argument au constructeur) ou par son ID (passer un entier non signé comme argument).

> [!NOTE]
> Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, appelez le constructeur, `COleDBRecordView::COleDBRecordView` , avec le nom de la ressource ou l’ID en tant qu’argument.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a> COleDBRecordView :: OnGetRowset

Retourne un handle pour l’objet **CRowset<>** associé à la vue de l’enregistrement.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez substituer cette fonction membre pour construire ou obtenir un objet d’ensemble de lignes et retourner un handle à celui-ci. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’Assistant écrit une substitution par défaut pour vous. L’implémentation par défaut de ClassWizard retourne le handle d’ensemble de lignes stocké dans la vue d’enregistrement, le cas échéant. Si ce n’est pas le cas, il construit un objet d’ensemble de lignes du type que vous avez spécifié avec ClassWizard et appelle la `Open` fonction membre pour ouvrir la table ou exécuter la requête, puis retourne un handle à l’objet.

> [!NOTE]
> Avant MFC 7,0, `OnGetRowset` retourne un pointeur vers `CRowset` . Si vous avez du code qui appelle `OnGetRowset` , vous devez remplacer le type de retour par la classe de classeuse **CRowset<>**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Pour plus d’informations et d’exemples, consultez l’article [vues des enregistrements : utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a> COleDBRecordView :: OnMove

Passe à un autre enregistrement de l’ensemble de lignes et affiche ses champs dans les contrôles de la vue de l’enregistrement.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand*<br/>
L’une des valeurs d’ID de commande standard suivantes :

- ID_RECORD_FIRST : accédez au premier enregistrement du jeu d’enregistrements.

- ID_RECORD_LAST : accédez au dernier enregistrement du jeu d’enregistrements.

- ID_RECORD_NEXT : accédez à l’enregistrement suivant dans le jeu d’enregistrements.

- ID_RECORD_PREV : accédez à l’enregistrement précédent dans le jeu d’enregistrements.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si le déplacement a réussi ; Sinon, 0 si la demande de déplacement a été refusée.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle la `Move` fonction membre appropriée de l' `CRowset` objet associé à la vue de l’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement actif sur la source de données si l’utilisateur l’a modifié dans la vue de l’enregistrement.

L’Assistant application crée une ressource de menu avec les éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option ancrabte de la barre d’outils, l’Assistant application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous déplacez au-delà du dernier enregistrement dans le jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous reculez au-delà du premier enregistrement, la vue de l’enregistrement continue d’afficher le premier enregistrement.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
