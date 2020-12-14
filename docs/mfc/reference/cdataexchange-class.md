---
description: 'En savoir plus sur : classe CDataExchange'
title: CDataExchange, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 36d11dc2b74142bd869b0e7b459d8bdb888b2cef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222175"
---
# <a name="cdataexchange-class"></a>CDataExchange, classe

Prend en charge les routines d’échange de données de boîtes de dialogue (DDX) et de validation de données de boîtes de dialogue (DDV) utilisées par les classes MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```
class CDataExchange
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDataExchange :: CDataExchange](#cdataexchange)|Construit un objet `CDataExchange`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDataExchange :: Fail](#fail)|Appelé lorsque la validation échoue. Rétablit le focus sur le contrôle précédent et lève une exception.|
|[CDataExchange ::P repareCtrl](#preparectrl)|Prépare le contrôle spécifié pour l’échange ou la validation de données. Utilisez pour les contrôles non-Edit.|
|[CDataExchange ::P repareEditCtrl](#prepareeditctrl)|Prépare le contrôle d’édition spécifié pour l’échange ou la validation de données.|
|[CDataExchange ::P repareOleCtrl](#prepareolectrl)|Prépare le contrôle OLE spécifié pour l’échange de données ou la validation. Utilisez pour les contrôles non-Edit.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDataExchange :: m_bSaveAndValidate](#m_bsaveandvalidate)|Indicateur de la direction de DDX et DDV.|
|[CDataExchange :: m_pDlgWnd](#m_pdlgwnd)|Boîte de dialogue ou fenêtre dans laquelle l’échange de données a lieu.|

## <a name="remarks"></a>Notes

`CDataExchange` n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour des contrôles ou des types de données personnalisés, ou si vous écrivez vos propres routines de validation de données. Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour obtenir une vue d’ensemble de DDX et DDV, consultez [échange et validation de données](../../mfc/dialog-data-exchange-and-validation.md) [de boîtes de](../../mfc/dialog-boxes.md)dialogue.

Un `CDataExchange` objet fournit les informations de contexte nécessaires pour que le DDX et le DDV soient exécutés. L’indicateur *m_bSaveAndValidate* a la valeur false lorsque DDX est utilisé pour remplir les valeurs initiales des contrôles de boîte de dialogue à partir des données membres. L’indicateur *m_bSaveAndValidate* a la valeur true lorsque DDX est utilisé pour définir les valeurs actuelles des contrôles de boîte de dialogue dans des données membres et lorsque DDV est utilisé pour valider les valeurs de données. Si la validation du DDV échoue, la procédure DDV affiche une boîte de message qui explique l’erreur d’entrée. La procédure DDV appellera ensuite `Fail` pour réinitialiser le focus sur le contrôle incriminé et générer une exception pour arrêter le processus de validation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDataExchange`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a> CDataExchange :: CDataExchange

Appelez cette fonction membre pour construire un `CDataExchange` objet.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Paramètres

*pDlgWnd*<br/>
Pointeur vers la fenêtre parente qui contient le contrôle. Il s’agit généralement d’un objet dérivé de [CDialog](../../mfc/reference/cdialog-class.md).

*bSaveAndValidate*<br/>
Si la valeur est TRUE, cet objet valide les données, puis écrit les données des contrôles dans les membres. Si la valeur est FALSe, cet objet déplace les données des membres vers les contrôles.

### <a name="remarks"></a>Notes

Construisez un `CDataExchange` objet vous-même pour stocker des informations supplémentaires dans l’objet d’échange de données à transmettre à la fonction membre [CWnd ::D odataexchange](../../mfc/reference/cwnd-class.md#dodataexchange) de votre fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a> CDataExchange :: Fail

L’infrastructure appelle cette fonction membre lorsqu’une opération de validation de données de boîte de dialogue (DDV) échoue.

```cpp
void Fail();
```

### <a name="remarks"></a>Notes

`Fail` restaure le focus et la sélection dans le contrôle dont la validation a échoué (s’il existe un contrôle à restaurer). `Fail` lève ensuite une exception de type [CUserException](../../mfc/reference/cuserexception-class.md) pour arrêter le processus de validation. L’exception entraîne l’affichage d’une boîte de message expliquant l’erreur à afficher. Après l’échec de la validation de DDV, l’utilisateur peut entrer à nouveau les données dans le contrôle incriminé.

Les implémenteurs de routines DDV personnalisées peuvent appeler `Fail` à partir de leurs routines en cas d’échec d’une validation.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a> CDataExchange :: m_bSaveAndValidate

Cet indicateur indique le sens d’une opération DDX (Dialog Data Exchange).

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Notes

L’indicateur est différent de zéro si l' `CDataExchange` objet est utilisé pour déplacer des données des contrôles de boîte de dialogue vers des membres de données de classe de boîte de dialogue une fois que l’utilisateur a modifié les contrôles. L’indicateur est égal à zéro si l’objet est utilisé pour initialiser des contrôles de boîte de dialogue à partir de membres de données de classe de boîte de dialogue.

L’indicateur est également différent de zéro pendant la validation des données de boîte de dialogue (DDV).

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a> CDataExchange :: m_pDlgWnd

Contient un pointeur vers l’objet [CWnd](../../mfc/reference/cwnd-class.md) pour lequel l’échange de données de boîtes de dialogue (DDX) ou la validation (DDV) a lieu.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Notes

Cet objet est généralement un objet [CDialog](../../mfc/reference/cdialog-class.md) . Les implémenteurs de routines DDX ou DDV personnalisées peuvent utiliser ce pointeur pour obtenir l’accès à la fenêtre de boîte de dialogue qui contient les contrôles sur lesquels ils opèrent.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a> CDataExchange ::P repareCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle spécifié pour l’échange de données de boîtes de dialogue (DDX) et la validation (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
ID du contrôle à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur renvoyée

HWND du contrôle en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) à la place pour les contrôles d’édition ; Utilisez cette fonction membre pour tous les autres contrôles.

La préparation consiste à stocker le HWND du contrôle dans la `CDataExchange` classe. L’infrastructure utilise ce handle pour restaurer le focus sur le contrôle précédemment ciblé dans l’éventualité d’un échec DDX ou DDV.

Les implémenteurs de routines DDX ou DDV personnalisées doivent appeler `PrepareCtrl` pour tous les contrôles non Edit pour lesquels ils échangent des données via DDX ou la validation des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a> CDataExchange ::P repareEditCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle d’édition spécifié pour l’échange de données de boîtes de dialogue (DDX) et la validation (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
ID du contrôle d’édition à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur renvoyée

HWND du contrôle d’édition en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareCtrl](#preparectrl) à la place pour tous les contrôles non-Edit.

La préparation est constituée de deux choses. Tout d’abord, `PrepareEditCtrl` stocke le HWND du contrôle dans la `CDataExchange` classe. L’infrastructure utilise ce handle pour restaurer le focus sur le contrôle précédemment ciblé dans l’éventualité d’un échec DDX ou DDV. Ensuite, `PrepareEditCtrl` définit un indicateur dans la `CDataExchange` classe pour indiquer que le contrôle dont les données sont échangées ou validées est un contrôle d’édition.

Les implémenteurs de routines DDX ou DDV personnalisées doivent appeler `PrepareEditCtrl` pour tous les contrôles d’édition pour lesquels ils échangent des données via DDX ou la validation des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a> CDataExchange ::P repareOleCtrl

L’infrastructure appelle cette fonction membre pour préparer le contrôle OLE spécifié pour l’échange de données de boîtes de dialogue (DDX) et la validation (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC*<br/>
ID du contrôle OLE à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le site de contrôle OLE.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) à la place pour les contrôles d’édition ou [PrepareCtrl](#preparectrl) pour tous les autres contrôles non-OLE.

Les implémenteurs de routines DDX ou DDV personnalisées doivent appeler `PrepareOleCtrl` pour tous les contrôles OLE pour lesquels ils échangent des données via DDX ou pour valider des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, consultez [Technical note 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour une vue d’ensemble de DDX et DDV, consultez [rubriques relatives](../../mfc/dialog-boxes.md)à l' [échange de données de boîtes](../../mfc/dialog-data-exchange-and-validation.md) de dialogue et à la validation et à la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Exemple MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
