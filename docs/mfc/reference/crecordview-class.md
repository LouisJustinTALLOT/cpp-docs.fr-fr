---
title: CRecordView, classe
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
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368352"
---
# <a name="crecordview-class"></a>CRecordView, classe

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
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Retourne nonzero si l’enregistrement actuel est le premier enregistrement dans le dossier associé.|
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Retourne nonzero si le dossier actuel est le dernier enregistrement dans le dossier associé.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Retourne un pointeur à un `CRecordset`objet d’une classe dérivé de . ClassWizard remplace cette fonction pour vous et crée l’enregistrement si nécessaire.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Si l’enregistrement actuel a changé, le met à jour sur la source de données, puis passe à l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue `CRecordset` de formulaire directement connectée à un objet. La vue est créée à partir d’une `CRecordset` ressource de modèle de dialogue et affiche les champs de l’objet dans les contrôles du modèle de dialogue. L’objet `CRecordView` utilise l’échange de données de dialogue (DDX) et l’échange de champs d’enregistrement (RFX) pour automatiser le mouvement des données entre les contrôles sur la forme et les champs de l’enregistrement. `CRecordView`fournit également une implémentation par défaut pour passer à la première, suivante, précédente, ou dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement à l’affiche.

> [!NOTE]
> Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt qu’avec les classes de connectivité à base de données ouvertes (ODBC), utilisez plutôt la classe [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Pour plus d’informations, voir l’article [Aperçu: Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

La façon la plus courante de créer votre vue d’enregistrement est avec l’Assistant d’Application. L’Assistant d’application crée à la fois la classe de vue d’enregistrement et sa classe de records associé dans le cadre de votre application de démarrage squelette. Si vous ne créez pas la classe de vue d’enregistrement avec l’Assistant d’Application, vous pouvez le créer plus tard avec ClassWizard. Si vous avez simplement besoin d’un seul formulaire, l’approche Application Wizard est plus facile. ClassWizard vous permet de décider d’utiliser une vue d’enregistrement plus tard dans le processus de développement. Utiliser ClassWizard pour créer une vue d’enregistrement et un ensemble d’enregistrements séparément, puis les connecter est l’approche la plus flexible, car il vous donne plus de contrôle dans le nom de la classe de nombre et son . H/. Dossiers du RPC. Cette approche vous permet également d’avoir plusieurs points de vue d’enregistrement sur la même classe de nombre d’enregistrements.

Pour faciliter le passage des utilisateurs finaux d’un enregistrement à l’autre dans la vue d’enregistrement, l’Assistant d’application crée des ressources de menu (et optionnellement toolbar) pour passer au premier, suivant, précédent ou dernier enregistrement. Si vous créez un cours de vue d’enregistrement avec ClassWizard, vous devez créer ces ressources vous-même avec le menu et les éditeurs de bitmap.

Pour plus d’informations sur la mise `IsOnFirstRecord` en `IsOnLastRecord` œuvre par défaut pour passer d’enregistrement en enregistrement, voir et l’article [à l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`garde une trace de la position de l’utilisateur dans le jeu d’enregistrement afin que la vue d’enregistrement puisse mettre à jour l’interface utilisateur. Lorsque l’utilisateur se déplace à l’une ou l’autre extrémité de l’ensemble d’enregistrements, la vue d’enregistrement désactive les objets d’interface utilisateur — tels que les éléments de menu ou les boutons de barre d’outils — pour aller plus loin dans la même direction.

Pour plus d’informations sur la déclaration et l’utilisation de votre vue d’enregistrement et des classes de recordset, voir "Designing and Creating a Record View" dans l’article [Record Views](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur le fonctionnement des affichages d’enregistrement et sur la façon de les utiliser, consultez [l’article Using a Record View](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView::CRecordView

Lorsque vous créez un objet `CRecordView`d’un type dérivé de , appelez l’une ou l’autre forme du constructeur pour initialiser l’objet de vue et identifier la ressource de dialogue sur laquelle la vue est basée.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de modèle de dialogue.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de dialogue.

### <a name="remarks"></a>Notes

Vous pouvez soit identifier la ressource par nom (passer une chaîne comme argument au constructeur) ou par sa pièce d’identité (passer un integer non signé comme argument). L’utilisation d’une pièce d’identité de ressource est recommandée.

> [!NOTE]
> Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordView::CRecordView` avec le nom de ressource ou d’identification comme argument, comme le montre l’exemple ci-dessous.

`CRecordView::OnInitialUpdate`appels `UpdateData`, `DoDataExchange`qui appelle . Cet appel `DoDataExchange` initial `CRecordView` pour connecter les `CRecordset` contrôles (indirectement) aux données sur le terrain des membres créés par ClassWizard. Ces membres de données ne peuvent pas `CFormView::OnInitialUpdate` être utilisés avant d’appeler la fonction membre de la classe de base.

> [!NOTE]
> Si vous utilisez ClassWizard, l’assistant `CRecordView::IDD`définit une valeur **enum,** la spécifie dans la déclaration de classe, et l’utilise dans la liste d’initialisation des membres pour le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord

Appelez cette fonction de membre pour déterminer si le dossier actuel est le premier enregistrement de l’objet de l’enregistrement associé à cette vue d’enregistrement.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le record actuel est le premier enregistrement dans le record; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations de gestionnaires de mise à jour de commande par défaut écrits par ClassWizard.

Si l’utilisateur passe au premier enregistrement, le cadre désactive tous les objets d’interface utilisateur que vous avez pour passer au premier ou à l’enregistrement précédent.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IsOnLastRecord

Appelez cette fonction de membre pour déterminer si le dossier actuel est le dernier enregistrement de l’objet de l’enregistrement associé à cette vue d’enregistrement.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le record actuel est le dernier enregistrement dans le record; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations des gestionnaires de mise à jour de commande par défaut que ClassWizard écrit pour prendre en charge une interface utilisateur pour passer d’enregistrement en enregistrement.

> [!CAUTION]
> Le résultat de cette fonction est fiable, sauf que la vue ne peut pas détecter la fin de l’enregistrement jusqu’à ce que l’utilisateur a passé. L’utilisateur doit aller au-delà du dernier enregistrement avant que la vue d’enregistrement puisse indiquer qu’il doit désactiver tous les objets d’interface utilisateur pour passer au prochain ou dernier enregistrement. Si l’utilisateur passe au-delà du dernier enregistrement, puis retourne au dernier enregistrement (ou avant lui), la vue d’enregistrement peut suivre la position de l’utilisateur dans le jeu d’enregistrements et désactiver correctement les objets d’interface utilisateur. `IsOnLastRecord`n’est pas fiable après un `OnRecordLast`appel à la fonction de mise `CRecordset::MoveLast`en œuvre , qui gère la commande ID_RECORD_LAST, ou .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::OnGetRecordset

Renvoie un `CRecordset`pointeur à l’objet dérivé associé à la vue d’enregistrement.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CRecordset`vers un objet dérivé si l’objet a été créé avec succès; sinon un pointeur NULL.

### <a name="remarks"></a>Notes

Vous devez remplacer cette fonction de membre pour construire ou obtenir un objet de recordet et y retourner un pointeur. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’assistant vous écrit un remplacement par défaut. L’implémentation par défaut de ClassWizard renvoie le pointeur d’enregistrement stocké dans la vue d’enregistrement si l’on existe. Si ce n’est pas le cas, il construit un objet `Open` record du type que vous avez spécifié avec ClassWizard et appelle sa fonction de membre pour ouvrir la table ou exécuter la requête, puis renvoie un pointeur à l’objet.

Pour plus d’informations et d’exemples, voir l’article [Affichages d’enregistrement: Utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::OnMove

Appelez cette fonction de membre pour passer à un enregistrement différent dans l’ensemble d’enregistrements et afficher ses champs dans les contrôles de la vue d’enregistrement.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand (en)*<br/>
L’une des valeurs d’identification de commande standard suivantes :

- ID_RECORD_FIRST Passez au premier disque dans le record.

- ID_RECORD_LAST Passez au dernier record dans le record.

- ID_RECORD_NEXT Passez à la prochaine fiche dans le record.

- ID_RECORD_PREV Passez à l’enregistrement précédent dans le record.

### <a name="return-value"></a>Valeur de retour

Nonzero si le déménagement a été un succès; autrement 0 si la demande de déménagement a été refusée.

### <a name="remarks"></a>Notes

La mise en `Move` œuvre `CRecordset` par défaut appelle la fonction membre appropriée de l’objet associé à la vue d’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement actuel sur la source de données si l’utilisateur l’a modifié dans la vue d’enregistrement.

L’Assistant d’application crée une ressource de menu avec First Record, Last Record, Next Record et Les éléments de menu Précédent Record. Si vous sélectionnez l’option Dockable Toolbar, l’Assistant d’Application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous passez au-delà du dernier enregistrement dans le recordet, la vue d’enregistrement continue d’afficher le dernier enregistrement. Si vous reculez au-delà du premier enregistrement, la vue d’enregistrement continue d’afficher le premier enregistrement.

> [!CAUTION]
> Appeler `OnMove` jette une exception si le recordet n’a pas de dossiers. Appelez la fonction appropriée de `OnUpdateRecordFirst` `OnUpdateRecordLast`gestionnaire `OnUpdateRecordNext`de `OnUpdateRecordPrev` mise à jour d’interface utilisateur — , , , ou — avant l’opération de déménagement correspondante pour déterminer si le dossier a des enregistrements.

## <a name="see-also"></a>Voir aussi

[Classe CFormView](../../mfc/reference/cformview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Classe CFormView](../../mfc/reference/cformview-class.md)
