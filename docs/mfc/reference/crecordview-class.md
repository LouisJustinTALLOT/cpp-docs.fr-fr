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
ms.openlocfilehash: 409739d97c9f7ae9a730ac8f05bd86e647da2c71
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215531"
---
# <a name="crecordview-class"></a>CRecordView (classe)

Vue qui affiche des enregistrements de base de données dans des contrôles.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|nom|Description|
|----------|-----------------|
|[CRecordView :: CRecordView](#crecordview)|Construit un objet `CRecordView`.|

### <a name="public-methods"></a>Méthodes publiques

|nom|Description|
|----------|-----------------|
|[CRecordView :: IsOnFirstRecord](#isonfirstrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le premier enregistrement dans le jeu d’enregistrements associé.|
|[CRecordView :: IsOnLastRecord](#isonlastrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le dernier enregistrement du Recordset associé.|
|[CRecordView :: OnGetRecordset](#ongetrecordset)|Retourne un pointeur vers un objet d’une classe dérivée de `CRecordset`. ClassWizard remplace cette fonction pour vous et crée le Recordset si nécessaire.|
|[CRecordView :: OnMove](#onmove)||

### <a name="protected-methods"></a>Méthodes protégées

|nom|Description|
|----------|-----------------|
|[CRecordView :: OnMove](#onmove)|Si l’enregistrement en cours a changé, le met à jour sur la source de données, puis se déplace vers l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue de formulaire directement connectée à un objet `CRecordset`. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de l’objet `CRecordset` dans les contrôles du modèle de boîte de dialogue. L’objet `CRecordView` utilise l’échange de données de boîtes de dialogue (DDX) et l’échange de champs d’enregistrements (RFX) pour automatiser le déplacement des données entre les contrôles du formulaire et les champs de l’ensemble d’enregistrements. `CRecordView` fournit également une implémentation par défaut pour passer au premier enregistrement, suivant, précédent ou dernier, ainsi qu’une interface pour la mise à jour de l’enregistrement actuellement affiché.

> [!NOTE]
>  Si vous utilisez les classes DAO (Data Access Objects) au lieu des classes Open Database Connectivity (ODBC), utilisez à la place la classe [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

La méthode la plus courante pour créer votre vue d’enregistrement consiste à utiliser l’Assistant Application. L’Assistant application crée la classe de vue d’enregistrement et sa classe de Recordset associée dans le cadre de votre application de démarrage squelette. Si vous ne créez pas la classe d’affichage d’enregistrement avec l’Assistant Application, vous pouvez la créer ultérieurement avec ClassWizard. Si vous avez simplement besoin d’un formulaire unique, l’approche de l’Assistant application est plus facile. ClassWizard vous permet de décider d’utiliser une vue d’enregistrement plus tard dans le processus de développement. L’utilisation de ClassWizard pour créer une vue d’enregistrement et un Recordset séparément, puis les connecter est l’approche la plus souple, car elle vous donne davantage de contrôle sur l’affectation de noms à la classe Recordset et à son. H/. Fichiers CPP. Cette approche vous permet également d’avoir plusieurs vues d’enregistrement sur la même classe Recordset.

Pour permettre aux utilisateurs finaux de passer facilement d’un enregistrement à l’autre dans la vue d’enregistrement, l’Assistant application crée des ressources menu (et éventuellement des barres d’outils) pour passer au premier enregistrement, suivant, précédent ou dernier. Si vous créez une classe d’affichage d’enregistrement avec ClassWizard, vous devez créer vous-même ces ressources avec les éditeurs de menu et bitmap.

Pour plus d’informations sur l’implémentation par défaut pour le déplacement d’un enregistrement à un autre, consultez `IsOnFirstRecord` et `IsOnLastRecord` et l’article [utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView` effectue le suivi de la position de l’utilisateur dans le Recordset afin que la vue d’enregistrement puisse mettre à jour l’interface utilisateur. Lorsque l’utilisateur passe à l’une des extrémités de l’ensemble d’enregistrements, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou les boutons de barre d’outils, pour se déplacer dans la même direction.

Pour plus d’informations sur la déclaration et l’utilisation de vos classes d’affichage des enregistrements et de jeux d’enregistrements, consultez « conception et création d’une vue d’enregistrement » dans l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur le fonctionnement des vues d’enregistrement et leur utilisation, consultez l’article [utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

##  <a name="crecordview"></a>CRecordView :: CRecordView

Lorsque vous créez un objet d’un type dérivé de `CRecordView`, appelez l’une ou l’autre forme du constructeur pour initialiser l’objet de vue et identifier la ressource de boîte de dialogue sur laquelle la vue est basée.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Vous pouvez identifier la ressource par son nom (passer une chaîne en tant qu’argument au constructeur) ou par son ID (passer un entier non signé comme argument). L’utilisation d’un ID de ressource est recommandée.

> [!NOTE]
>  Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordView::CRecordView` avec l’ID ou le nom de la ressource comme argument, comme indiqué dans l’exemple ci-dessous.

`CRecordView::OnInitialUpdate` appelle `UpdateData`, qui appelle `DoDataExchange`. Cet appel initial à `DoDataExchange` permet de se connecter `CRecordView` contrôles (indirectement) à `CRecordset` membres de données de champ créés par ClassWizard. Ces membres de données ne peuvent pas être utilisés tant que vous n’avez pas appelé la classe de base `CFormView::OnInitialUpdate` fonction membre.

> [!NOTE]
>  Si vous utilisez ClassWizard, l’Assistant définit une valeur **enum** `CRecordView::IDD`, le spécifie dans la déclaration de classe et l’utilise dans la liste d’initialisation des membres pour le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>CRecordView :: IsOnFirstRecord

Appelez cette fonction membre pour déterminer si l’enregistrement en cours est le premier enregistrement de l’objet Recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’enregistrement actif est le premier enregistrement dans le Recordset ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations des gestionnaires de mise à jour de commandes par défaut écrits par ClassWizard.

Si l’utilisateur passe au premier enregistrement, l’infrastructure désactive tous les objets d’interface utilisateur dont vous disposez pour passer au premier enregistrement ou à l’enregistrement précédent.

##  <a name="isonlastrecord"></a>CRecordView :: IsOnLastRecord

Appelez cette fonction membre pour déterminer si l’enregistrement en cours est le dernier enregistrement de l’objet Recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’enregistrement actif est le dernier enregistrement du Recordset ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations des gestionnaires de mise à jour de commandes par défaut que ClassWizard écrit pour prendre en charge une interface utilisateur pour le déplacement d’un enregistrement à un autre.

> [!CAUTION]
>  Le résultat de cette fonction est fiable, sauf que la vue ne peut pas détecter la fin du Recordset tant que l’utilisateur ne l’a pas déplacée. L’utilisateur doit se déplacer au-delà du dernier enregistrement avant que la vue de l’enregistrement puisse déterminer qu’il doit désactiver les objets d’interface utilisateur pour passer au dernier enregistrement ou à l’enregistrement suivant. Si l’utilisateur passe au-delà du dernier enregistrement, puis revient au dernier enregistrement (ou avant), la vue de l’enregistrement peut suivre la position de l’utilisateur dans le jeu d’enregistrements et désactiver les objets de l’interface utilisateur correctement. `IsOnLastRecord` n’est pas non plus fiable après un appel à la fonction d’implémentation `OnRecordLast`, qui gère la commande ID_RECORD_LAST, ou `CRecordset::MoveLast`.

##  <a name="ongetrecordset"></a>CRecordView :: OnGetRecordset

Retourne un pointeur vers l’objet dérivé de `CRecordset`associé à la vue de l’enregistrement.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet dérivé de `CRecordset`si l’objet a été créé avec succès ; Sinon, un pointeur NULL.

### <a name="remarks"></a>Notes

Vous devez substituer cette fonction membre pour construire ou obtenir un objet Recordset et retourner un pointeur vers celui-ci. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’Assistant écrit une substitution par défaut pour vous. L’implémentation par défaut de ClassWizard retourne le pointeur de Recordset stocké dans la vue d’enregistrement, s’il en existe une. Si ce n’est pas le cas, il construit un objet Recordset du type que vous avez spécifié avec ClassWizard et appelle sa fonction membre `Open` pour ouvrir la table ou exécuter la requête, puis retourne un pointeur vers l’objet.

Pour plus d’informations et d’exemples, consultez l’article [vues des enregistrements : utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>CRecordView :: OnMove

Appelez cette fonction membre pour passer à un autre enregistrement dans le Recordset et afficher ses champs dans les contrôles de la vue de l’enregistrement.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Paramètres

*nIDMoveCommand*<br/>
L’une des valeurs d’ID de commande standard suivantes :

- ID_RECORD_FIRST accédez au premier enregistrement du jeu d’enregistrements.

- ID_RECORD_LAST accédez au dernier enregistrement du jeu d’enregistrements.

- ID_RECORD_NEXT passer à l’enregistrement suivant dans le jeu d’enregistrements.

- ID_RECORD_PREV passer à l’enregistrement précédent dans le jeu d’enregistrements.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si le déplacement a réussi ; Sinon, 0 si la demande de déplacement a été refusée.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle la fonction membre `Move` appropriée de l’objet `CRecordset` associé à la vue de l’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement actif sur la source de données si l’utilisateur l’a modifié dans la vue de l’enregistrement.

L’Assistant application crée une ressource de menu avec les éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option ancrabte de la barre d’outils, l’Assistant application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous déplacez au-delà du dernier enregistrement dans le jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous reculez au-delà du premier enregistrement, la vue de l’enregistrement continue d’afficher le premier enregistrement.

> [!CAUTION]
>  L’appel de `OnMove` lève une exception si le Recordset n’a pas d’enregistrement. Appelez la fonction de gestionnaire de mise à jour d’interface utilisateur appropriée (`OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`ou `OnUpdateRecordPrev`) avant l’opération de déplacement correspondante pour déterminer si le Recordset contient des enregistrements.

## <a name="see-also"></a>Voir aussi

[CFormView, classe](../../mfc/reference/cformview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)
