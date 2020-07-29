---
title: CDaoRecordView, classe
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: 95ed9207d0047287e373401da52f05235a817999
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223133"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView, classe

Vue qui affiche des enregistrements de base de données dans des contrôles.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CDaoRecordView :: CDaoRecordView](#cdaorecordview)|Construit un objet `CDaoRecordView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoRecordView :: IsOnFirstRecord](#isonfirstrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le premier enregistrement dans le jeu d’enregistrements associé.|
|[CDaoRecordView :: IsOnLastRecord](#isonlastrecord)|Retourne une valeur différente de zéro si l’enregistrement actif est le dernier enregistrement du Recordset associé.|
|[CDaoRecordView :: OnGetRecordset](#ongetrecordset)|Retourne un pointeur vers un objet d’une classe dérivée de `CDaoRecordset` . ClassWizard remplace cette fonction pour vous et crée le Recordset si nécessaire.|
|[CDaoRecordView :: OnMove](#onmove)|Si l’enregistrement en cours a changé, le met à jour sur la source de données, puis se déplace vers l’enregistrement spécifié (suivant, précédent, premier ou dernier).|

## <a name="remarks"></a>Notes

La vue est une vue de formulaire directement connectée à un `CDaoRecordset` objet. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de l' `CDaoRecordset` objet dans les contrôles du modèle de boîte de dialogue. L' `CDaoRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et l’échange de champs d’enregistrements DAO (DFX) pour automatiser le déplacement des données entre les contrôles du formulaire et les champs de l’ensemble d’enregistrements. `CDaoRecordView`fournit également une implémentation par défaut pour passer au premier enregistrement, suivant, précédent ou dernier et une interface pour mettre à jour l’enregistrement actuellement affiché.

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. les classes DAO offrent généralement des fonctionnalités supérieures, car elles utilisent le moteur de base de données Microsoft Jet.

La méthode la plus courante pour créer votre vue d’enregistrement consiste à utiliser l’Assistant Application. L’Assistant application crée la classe de vue d’enregistrement et sa classe de Recordset associée dans le cadre de votre application de démarrage squelette.

Si vous avez simplement besoin d’un formulaire unique, l’approche de l’Assistant application est plus facile. ClassWizard vous permet de décider d’utiliser une vue d’enregistrement plus tard dans le processus de développement. Si vous ne créez pas la classe d’affichage d’enregistrement avec l’Assistant Application, vous pouvez la créer ultérieurement avec ClassWizard. L’utilisation de ClassWizard pour créer une vue d’enregistrement et un Recordset séparément, puis les connecter est l’approche la plus souple, car elle vous donne davantage de contrôle sur l’affectation de noms à la classe Recordset et à son. H/. Fichiers CPP. Cette approche vous permet également d’avoir plusieurs vues d’enregistrement sur la même classe Recordset.

Pour permettre aux utilisateurs finaux de passer facilement d’un enregistrement à l’autre dans la vue d’enregistrement, l’Assistant application crée des ressources menu (et éventuellement des barres d’outils) pour passer au premier enregistrement, suivant, précédent ou dernier. Si vous créez une classe d’affichage d’enregistrement avec ClassWizard, vous devez créer vous-même ces ressources avec les éditeurs de menu et bitmap.

Pour plus d’informations sur l’implémentation par défaut pour le déplacement d’un enregistrement à un autre, consultez `IsOnFirstRecord` et `IsOnLastRecord` et l’article [à l’aide d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md)qui s’applique à la fois à `CRecordView` et à `CDaoRecordView` .

`CDaoRecordView`effectue le suivi de la position de l’utilisateur dans le Recordset afin que la vue d’enregistrement puisse mettre à jour l’interface utilisateur. Lorsque l’utilisateur passe à l’une des extrémités de l’ensemble d’enregistrements, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou les boutons de barre d’outils, pour se déplacer dans la même direction.

Pour plus d’informations sur la déclaration et l’utilisation de vos classes d’affichage des enregistrements et de jeux d’enregistrements, consultez « conception et création d’une vue d’enregistrement » dans l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur le fonctionnement des vues d’enregistrement et leur utilisation, consultez l’article [utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md). Tous les articles mentionnés ci-dessus s’appliquent à `CRecordView` et à `CDaoRecordView` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView :: CDaoRecordView

Quand vous créez un objet d’un type dérivé de `CDaoRecordView` , appelez l’une ou l’autre forme du constructeur pour initialiser l’objet de vue et identifier la ressource de boîte de dialogue sur laquelle la vue est basée.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Vous pouvez identifier la ressource par son nom (passer une chaîne en tant qu’argument au constructeur) ou par son ID (passer un entier non signé comme argument). L’utilisation d’un ID de ressource est recommandée.

> [!NOTE]
> Votre classe dérivée doit fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CDaoRecordView::CDaoRecordView` avec le nom ou l’ID de la ressource en tant qu’argument.

`CDaoRecordView::OnInitialUpdate`appelle `CWnd::UpdateData` , qui appelle `CWnd::DoDataExchange` . Cet appel initial à `DoDataExchange` connecte `CDaoRecordView` les contrôles (indirectement) aux `CDaoRecordset` membres de données de champ créés par ClassWizard. Ces membres de données ne peuvent pas être utilisés tant que vous n’avez pas appelé la fonction membre de la classe de base `CFormView::OnInitialUpdate` .

> [!NOTE]
> Si vous utilisez ClassWizard, l’Assistant définit une **`enum`** valeur `CDaoRecordView::IDD` dans la déclaration de classe et l’utilise dans la liste d’initialisation des membres pour le constructeur.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView :: IsOnFirstRecord

Appelez cette fonction membre pour déterminer si l’enregistrement en cours est le premier enregistrement de l’objet Recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’enregistrement actif est le premier enregistrement dans le Recordset ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations des gestionnaires de mise à jour de commandes par défaut écrits par ClassWizard.

Si l’utilisateur passe au premier enregistrement, l’infrastructure désactive tous les objets d’interface utilisateur (par exemple, les éléments de menu ou les boutons de barre d’outils) dont vous disposez pour déplacer vers le premier ou l’enregistrement précédent.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView :: IsOnLastRecord

Appelez cette fonction membre pour déterminer si l’enregistrement en cours est le dernier enregistrement de l’objet Recordset associé à cette vue de l’enregistrement.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’enregistrement actif est le dernier enregistrement du Recordset ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utile pour écrire vos propres implémentations des gestionnaires de mise à jour de commandes par défaut que ClassWizard écrit pour prendre en charge une interface utilisateur pour le déplacement d’un enregistrement à un autre.

> [!CAUTION]
> Le résultat de cette fonction est fiable, sauf que la vue peut ne pas être en mesure de détecter la fin du Recordset tant que l’utilisateur ne l’a pas déplacée. L’utilisateur devra peut-être se déplacer au-delà du dernier enregistrement pour que la vue de l’enregistrement puisse déterminer qu’il doit désactiver les objets d’interface utilisateur pour passer au dernier enregistrement ou suivant. Si l’utilisateur passe au-delà du dernier enregistrement, puis revient au dernier enregistrement (ou avant), la vue de l’enregistrement peut suivre la position de l’utilisateur dans le jeu d’enregistrements et désactiver les objets de l’interface utilisateur correctement.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView :: OnGetRecordset

Retourne un pointeur vers l' `CDaoRecordset` objet dérivé de associé à la vue de l’enregistrement.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CDaoRecordset` objet dérivé de si l’objet a été créé avec succès ; sinon, un pointeur null.

### <a name="remarks"></a>Notes

Vous devez substituer cette fonction membre pour construire ou obtenir un objet Recordset et retourner un pointeur vers celui-ci. Si vous déclarez votre classe de vue d’enregistrement avec ClassWizard, l’Assistant écrit une substitution par défaut pour vous. L’implémentation par défaut de ClassWizard retourne le pointeur de Recordset stocké dans la vue d’enregistrement, s’il en existe une. Si ce n’est pas le cas, il construit un objet Recordset du type que vous avez spécifié avec ClassWizard et appelle la `Open` fonction membre pour ouvrir la table ou exécuter la requête, puis retourne un pointeur vers l’objet.

Pour plus d’informations et d’exemples, consultez l’article [vues des enregistrements : utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView :: OnMove

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

L’implémentation par défaut appelle la fonction membre Move appropriée de l' `CDaoRecordset` objet associé à la vue de l’enregistrement.

Par défaut, `OnMove` met à jour l’enregistrement actif sur la source de données si l’utilisateur l’a modifié dans la vue de l’enregistrement.

L’Assistant application crée une ressource de menu avec les éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option initiale de la barre d’outils, l’Assistant application crée également une barre d’outils avec des boutons correspondant à ces commandes.

Si vous déplacez au-delà du dernier enregistrement dans le jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous reculez au-delà du premier enregistrement, la vue de l’enregistrement continue d’afficher le premier enregistrement.

> [!CAUTION]
> `OnMove`L’appel de lève une exception si le Recordset n’a pas d’enregistrement. Appelez la fonction de gestionnaire de mise à jour d’interface utilisateur appropriée,,, `OnUpdateRecordFirst` `OnUpdateRecordLast` ou, `OnUpdateRecordNext` `OnUpdateRecordPrev` avant l’opération de déplacement correspondante pour déterminer si le Recordset contient des enregistrements.

## <a name="see-also"></a>Voir aussi

[CFormView, classe](../../mfc/reference/cformview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset (classe)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (classe)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Classe CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace (classe)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)
