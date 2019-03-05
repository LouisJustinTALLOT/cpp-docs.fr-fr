---
title: CRecordView (classe)
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: a91a9e320b4221b04bbcf996ffa60f1de4b35ec5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262465"
---
# <a name="crecordview-class"></a>CRecordView (classe)

Vue qui affiche des enregistrements de base de données dans des contrôles.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|Construit un objet `CRecordView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le premier enregistrement dans le jeu d’enregistrements.|
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le dernier enregistrement dans le jeu d’enregistrements.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Retourne un pointeur vers un objet d’une classe dérivée de `CRecordset`. ClassWizard remplace cette fonction pour vous et crée le jeu d’enregistrements si nécessaire.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Si l’enregistrement en cours a changé, il met à jour sur la source de données, puis passe à l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue de formulaire directement connectée à un `CRecordset` objet. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de la `CRecordset` objet dans les contrôles du modèle de boîte de dialogue. Le `CRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et l’échange de champs d’enregistrements (RFX) pour automatiser le déplacement des données entre les contrôles sur le formulaire et les champs du recordset. `CRecordView` fournit également une implémentation par défaut pour le déplacement vers le premier, suivant, précédent ou le dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement dans la vue.

> [!NOTE]
>  Si vous travaillez avec les classes d’objets DAO (Data Access) plutôt que les classes de base de données connectivité ODBC (Open), utilisez la classe [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

La plus courante consiste à créer votre vue de l’enregistrement avec l’Assistant Application. Assistant Création d’applications TGE crée la classe de vue d’enregistrement et sa classe de recordset associé dans le cadre de votre application squelette starter. Si vous ne créez pas la classe de vue d’enregistrement avec l’Assistant Application, vous pouvez le créer ultérieurement avec ClassWizard. Si vous avez simplement besoin d’un formulaire unique, l’approche de l’Assistant Création d’applications est plus facile. ClassWizard vous permet de décider d’utiliser une vue d’enregistrement plus loin dans le processus de développement. Pour créer une vue d’enregistrement et un jeu d’enregistrements séparément et puis de les connecter à l’aide de ClassWizard est l’approche la plus flexible, car il vous donne davantage de contrôle dans la classe de jeu d’enregistrements d’affectation de noms et sa. H /. Fichiers CPP. Cette approche vous permet également d’avoir plusieurs vues d’enregistrements sur la même classe de jeu d’enregistrements.

Pour faciliter aux utilisateurs finaux de passer d’un enregistrement à l’autre dans la vue de l’enregistrement, l’Assistant Application crée menu (et éventuellement de barre d’outils) ressources pour passer à la première, suivant, précédent ou le dernier enregistrement. Si vous créez une classe de vue d’enregistrement avec ClassWizard, vous devez créer ces ressources vous-même avec le menu et bitmap éditeurs.

Pour plus d’informations sur l’implémentation par défaut pour le déplacement d’un enregistrement à l’autre, consultez `IsOnFirstRecord` et `IsOnLastRecord` et l’article [à l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView` effectue le suivi de position de l’utilisateur dans le jeu d’enregistrements afin que la vue de l’enregistrement peut mettre à jour l’interface utilisateur. Lorsque l’utilisateur se déplace vers chaque extrémité de l’ensemble d’enregistrements, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou des boutons de barre d’outils, de déplacement plus en détail dans la même direction.

Pour plus d’informations sur la déclaration et utilisation de votre vue d’enregistrement et les classes de jeu d’enregistrements, consultez « Conception et création d’une vue enregistrement » dans l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur comment travail vues d’enregistrement et de leur utilisation, consultez l’article [à l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdb.h

##  <a name="crecordview"></a>  CRecordView::CRecordView

Lorsque vous créez un objet d’un type dérivé `CRecordView`, appelez des deux formes du constructeur pour initialiser l’objet de vue et d’identifier la ressource de boîte de dialogue sur laquelle repose la vue.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Vous pouvez soit identifier la ressource par nom (passez une chaîne comme argument au constructeur) ou par son ID (pass un entier non signé comme argument). ID à l’aide d’une ressource est recommandé.

> [!NOTE]
>  Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordView::CRecordView` avec le nom de la ressource ou l’ID en tant qu’argument, comme illustré dans l’exemple ci-dessous.

`CRecordView::OnInitialUpdate` appels `UpdateData`, qui appelle `DoDataExchange`. Cet appel initial à `DoDataExchange` se connecte `CRecordView` contrôle (indirectement) de `CRecordset` champ des membres de données créés par ClassWizard. Ces membres de données ne peut pas être utilisés jusqu'à ce que, après l’appel de la classe de base `CFormView::OnInitialUpdate` fonction membre.

> [!NOTE]
>  Si vous utilisez ClassWizard, l’Assistant définit un **enum** valeur `CRecordView::IDD`, il spécifie dans la déclaration de classe et l’utilise dans la liste d’initialisation de membre pour le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord

Appelez cette fonction membre pour déterminer si l’enregistrement actif est le premier enregistrement de l’objet recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’enregistrement actif est le premier enregistrement dans le jeu d’enregistrements ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations de valeur par défaut des gestionnaires de mise à jour de commande écrits par ClassWizard.

Si l’utilisateur se déplace vers le premier enregistrement, le framework désactive les objets d’interface utilisateur que vous disposez pour le passage à la première ou de l’enregistrement précédent.

##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord

Appelez cette fonction membre pour déterminer si l’enregistrement actif est le dernier enregistrement de l’objet recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’enregistrement actif est le dernier enregistrement dans le jeu d’enregistrements ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations de la valeur par défaut des gestionnaires de mise à jour de commandes ClassWizard écrit pour prendre en charge une interface utilisateur pour le déplacement d’un enregistrement à l’autre.

> [!CAUTION]
>  Le résultat de cette fonction est fiable, à ceci près que la vue ne peut pas détecter la fin de l’objet recordset jusqu'à ce que l’utilisateur a déplacé au-delà de celle-ci. L’utilisateur doit déplacer au-delà du dernier enregistrement avant l’affichage de l’enregistrement peut indiquer qu’il doit désactiver les objets d’interface utilisateur pour le passage à l’enregistrement suivant ou la dernière. Si l’utilisateur se déplace au delà du dernier enregistrement, puis déplace le curseur vers le dernier enregistrement (ou avant qu’elle), la vue de l’enregistrement peut effectuer le suivi de la position de l’utilisateur dans le jeu d’enregistrements et désactiver les objets d’interface utilisateur correctement. `IsOnLastRecord` est également peu fiable après un appel à la fonction de l’implémentation `OnRecordLast`, qui gère la commande ID_RECORD_LAST, ou `CRecordset::MoveLast`.

##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset

Retourne un pointeur vers le `CRecordset`-dérivés d’objet associé à la vue de l’enregistrement.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CRecordset`-objet dérivé si l’objet a été créé avec succès ; sinon un pointeur NULL.

### <a name="remarks"></a>Notes

Vous devez substituer cette fonction membre pour construire ou obtenir un objet de jeu d’enregistrements et retourner un pointeur vers elle. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’Assistant écrit une valeur de remplacement par défaut pour vous. Implémentation par défaut de ClassWizard retourne le pointeur de jeu d’enregistrements stocké dans la vue de l’enregistrement s’il en existe. Si non, il construit un objet recordset du type que vous avez spécifié avec ClassWizard et appelle son `Open` membre de fonction pour ouvrir la table ou exécuter la requête, puis retourne un pointeur vers l’objet.

Pour plus d’informations et des exemples, consultez l’article [vues d’enregistrements : À l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  CRecordView::OnMove

Appelez cette fonction membre pour déplacer vers un autre enregistrement dans le jeu d’enregistrements et afficher ses champs dans les contrôles de la vue de l’enregistrement.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand*<br/>
Une des valeurs d’ID de commande standard suivantes :

- ID_RECORD_FIRST déplacer vers le premier enregistrement dans le jeu d’enregistrements.

- ID_RECORD_LAST déplacer vers le dernier enregistrement dans le jeu d’enregistrements.

- ID_RECORD_NEXT déplacer vers l’enregistrement suivant dans le jeu d’enregistrements.

- ID_RECORD_PREV déplacer vers l’enregistrement précédent dans le jeu d’enregistrements.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le déplacement a réussi ; Sinon, 0 si la demande de déplacement a été refusée.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle approprié `Move` fonction membre de la `CRecordset` objet associé à la vue de l’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement en cours sur la source de données si l’utilisateur a été modifié dans la vue de l’enregistrement.

L’Assistant Application crée une ressource de menu avec les éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option de la barre d’outils ancrable, l’Assistant Application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous déplacez au-delà du dernier enregistrement dans le jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous déplacez vers l’arrière au-delà du premier enregistrement, la vue de l’enregistrement continue à afficher le premier enregistrement.

> [!CAUTION]
>  Appel `OnMove` lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Appelez la fonction de gestionnaire de mise à jour interface utilisateur appropriée : `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, ou `OnUpdateRecordPrev` — avant le correspondantes du déplacement pour déterminer si le jeu d’enregistrements a tous les enregistrements.

## <a name="see-also"></a>Voir aussi

[CFormView, classe](../../mfc/reference/cformview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)
