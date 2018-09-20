---
title: CDataExchange, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
dev_langs:
- C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7148863a4689051503827a068cf6b93a88f2e35
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374602"
---
# <a name="cdataexchange-class"></a>CDataExchange (classe)

Prend en charge les routines d’échange de données de boîtes de dialogue (DDX) et de validation de données de boîtes de dialogue (DDV) utilisées par les classes MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```
class CDataExchange
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Construit un objet `CDataExchange`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|Appelé lorsque la validation échoue. Réinitialise le focus au contrôle précédent et lève une exception.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Prépare le contrôle spécifié pour l’échange de données ou de validation. À utiliser pour les contrôles nonedit.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Prépare le contrôle d’édition spécifié pour l’échange de données ou de validation.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Prépare le contrôle OLE spécifié pour l’échange de données ou de validation. À utiliser pour les contrôles nonedit.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Indicateur pour la direction de DDX et DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|La boîte de dialogue ou la fenêtre dans laquelle l’échange de données a lieu.|

## <a name="remarks"></a>Notes

`CDataExchange` n’a pas d’une classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour les types de données personnalisés ou des contrôles, ou si vous écrivez vos propres routines de validation de données. Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [boîtes de dialogue](../../mfc/dialog-boxes.md).

Un `CDataExchange` objet fournit les informations de contexte nécessaires pour placent de DDX et DDV à prendre. L’indicateur *m_bSaveAndValidate* a la valeur FALSE lorsque DDX est utilisé pour remplir les valeurs initiales des contrôles de boîte de dialogue à partir de membres de données. L’indicateur *m_bSaveAndValidate* a la valeur TRUE lorsque DDX est utilisé pour définir les valeurs actuelles des contrôles de boîte de dialogue dans les membres de données et quand DDV est utilisé pour valider les valeurs de données. Si la validation DDV échoue, la procédure DDV affichera une boîte de message expliquant l’erreur d’entrée. Appelle ensuite la procédure DDV `Fail` pour réinitialiser le focus au contrôle incriminé et lever une exception pour arrêter le processus de validation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDataExchange`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange

Appelez cette fonction membre pour construire un `CDataExchange` objet.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Paramètres

*pDlgWnd*<br/>
Pointeur vers la fenêtre parente qui contient le contrôle. Il s’agit généralement un [CDialog](../../mfc/reference/cdialog-class.md)-objet dérivé.

*bSaveAndValidate*<br/>
Si la valeur est TRUE, cet objet valide les données, puis écrit les données des contrôles aux membres. Si la valeur est FALSE, cet objet sera déplacé les données des membres aux contrôles.

### <a name="remarks"></a>Notes

Construire un `CDataExchange` objet vous-même pour stocker des informations supplémentaires dans l’objet d’échange de données à passer à la fenêtre de votre [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

##  <a name="fail"></a>  CDataExchange::Fail

L’infrastructure appelle cette fonction membre en cas d’échec d’une opération de validation (DDV) de données de boîte de dialogue.

```
void Fail();
```

### <a name="remarks"></a>Notes

`Fail` Restaure le focus et la sélection dans le contrôle dont la validation a échoué (cas d’un contrôle pour restaurer). `Fail` puis lève une exception de type [CUserException](../../mfc/reference/cuserexception-class.md) pour arrêter le processus de validation. L’exception entraîne une boîte de message expliquant l’erreur à afficher. Après l’échec de la validation de DDV, l’utilisateur peut entrer à nouveau les données dans le contrôle incriminé.

Les implémenteurs des routines DDV personnalisées peuvent appeler `Fail` à partir de leurs routines lors de l’échec d’une validation.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate

Cet indicateur indique la direction d’une opération d’échange (DDX) de données boîte de dialogue.

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Notes

L’indicateur est différent de zéro si le `CDataExchange` objet est utilisé pour déplacer des données à partir des contrôles de boîte de dialogue pour les données membres de classe de boîte de dialogue une fois que l’utilisateur modifie les contrôles. L’indicateur est égal à zéro si l’objet est utilisé pour initialiser les contrôles de boîte de dialogue à partir de données membres de classe de boîte de dialogue.

L’indicateur est également différent de zéro pendant la validation de données de boîte de dialogue (DDV).

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd

Contient un pointeur vers le [CWnd](../../mfc/reference/cwnd-class.md) objet pour la boîte de dialogue échange de données (DDX) ou de validation (DDV) est en cours.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Notes

Cet objet est généralement un [CDialog](../../mfc/reference/cdialog-class.md) objet. Les implémenteurs des routines DDX ou DDV personnalisées peuvent utiliser ce pointeur pour obtenir l’accès à la fenêtre de boîte de dialogue qui contient les contrôles qu’ils fonctionnent sur.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle spécifié pour l’échange de données de boîtes de dialogue (DDX) et validation (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
ID du contrôle à être préparé pour DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Le HWND du contrôle en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) à la place pour les contrôles d’édition ; utiliser cette fonction membre pour tous les autres contrôles.

Préparation consistant en stockant le HWND du contrôle dans la `CDataExchange` classe. L’infrastructure utilise ce handle pour restaurer le focus au contrôle en cas de défaillance DDX ou DDV précédemment ayant le focus.

Les implémenteurs des routines DDX ou DDV personnalisées doivent appeler `PrepareCtrl` pour tous les contrôles non modification à laquelle ils sont échanger des données via DDX ou validation des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle d’édition spécifié pour l’échange de données de boîtes de dialogue (DDX) et validation (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
L’ID du contrôle d’édition pour préparer le DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Le HWND du contrôle d’édition en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareCtrl](#preparectrl) au lieu de cela pour tous les contrôles non modifiable.

Préparation comprend deux choses. Tout d’abord, `PrepareEditCtrl` stocke le HWND du contrôle dans la `CDataExchange` classe. L’infrastructure utilise ce handle pour restaurer le focus au contrôle en cas de défaillance DDX ou DDV précédemment ayant le focus. Ensuite, `PrepareEditCtrl` définit un indicateur le `CDataExchange` classe pour indiquer que le contrôle dont les données sont échangées ou validé sont un contrôle d’édition.

Les implémenteurs des routines DDX ou DDV personnalisées doivent appeler `PrepareEditCtrl` pour tous les contrôles pour lesquels ils sont échanger des données via DDX ou validation des données via DDV d’édition.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle OLE spécifié pour l’échange de données de boîtes de dialogue (DDX) et validation (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
L’ID du contrôle OLE pour préparer le DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le site de contrôle OLE.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) à la place pour les contrôles d’édition ou [PrepareCtrl](#preparectrl) pour tous les autres contrôles autres que OLE.

Les implémenteurs des routines DDX ou DDV personnalisées doivent appeler `PrepareOleCtrl` pour tous les contrôles OLE à laquelle ils sont échanger des données via DDX ou validation des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md) et [rubriques boîtes de dialogue](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Voir aussi

[Exemple MFC VIEWEX](../../visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

