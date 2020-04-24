---
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
ms.openlocfilehash: fd1bce7de7ac323dc3099ab4938306768eb95a35
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754624"
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
|[CDataExchange::CDataExchange](#cdataexchange)|Construit un objet `CDataExchange`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDataExchange::Échec](#fail)|Appelé en cas de panne de validation. Réinitialise la mise au point sur le contrôle précédent et lance une exception.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Prépare le contrôle spécifié pour l’échange ou la validation des données. Utilisation pour les contrôles nonedit.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Prépare le contrôle de modification spécifié pour l’échange ou la validation des données.|
|[CDataExchange::PRepareOleCtrl](#prepareolectrl)|Prépare le contrôle OLE spécifié pour l’échange ou la validation des données. Utilisation pour les contrôles nonedit.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Drapeau pour la direction de DDX et DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|La boîte de dialogue ou la fenêtre où l’échange de données a lieu.|

## <a name="remarks"></a>Notes

`CDataExchange`n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données à des types ou à des contrôles de données personnalisés, ou si vous écrivez vos propres routines de validation de données. Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Boxes](../../mfc/dialog-boxes.md).

Un `CDataExchange` objet fournit les informations contextuelles nécessaires pour que DDX et DDV aient lieu. Le drapeau *m_bSaveAndValidate* est FALSE lorsque DDX est utilisé pour remplir les valeurs initiales des contrôles de dialogue des membres des données. Le drapeau *m_bSaveAndValidate* est VRAI lorsque DDX est utilisé pour définir les valeurs actuelles des contrôles de dialogue dans les membres des données et lorsque DDV est utilisé pour valider les valeurs de données. Si la validation DDV échoue, la procédure DDV affichera une boîte de message expliquant l’erreur d’entrée. La procédure DDV `Fail` appellera ensuite à réinitialiser l’accent sur le contrôle incriminé et à faire une exception pour mettre fin au processus de validation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDataExchange`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange

Appelez cette fonction de `CDataExchange` membre pour construire un objet.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Paramètres

*pDlgWnd (en)*<br/>
Un pointeur à la fenêtre parente qui contient le contrôle. Habituellement, il s’agit d’un objet dérivé du [CDialog.](../../mfc/reference/cdialog-class.md)

*bSaveAndValidate*<br/>
Si VRAI, cet objet valide les données, puis écrit les données des contrôles aux membres. Si FALSE, cet objet déplacera les données des membres vers les contrôles.

### <a name="remarks"></a>Notes

Construisez `CDataExchange` un objet vous-même pour stocker des informations supplémentaires dans l’objet d’échange de données pour passer à la fonction de membre [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) de votre fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange::Échec

Le cadre appelle cette fonction de membre lorsqu’une opération de validation des données de dialogue (DDV) échoue.

```cpp
void Fail();
```

### <a name="remarks"></a>Notes

`Fail`restaure la mise au point et la sélection du contrôle dont la validation a échoué (s’il y a un contrôle à restaurer). `Fail`lance ensuite une exception de type [CUserException](../../mfc/reference/cuserexception-class.md) pour arrêter le processus de validation. L’exception provoque l’affichage d’une boîte de messages expliquant l’erreur. Après l’échec de la validation DDV, l’utilisateur peut réintégrer les données dans le contrôle incriminé.

Les implémenteurs de routines `Fail` DDV personnalisées peuvent appeler à partir de leurs routines lorsqu’une validation échoue.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate

Ce drapeau indique la direction d’une opération d’échange de données de dialogue (DDX).

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Notes

Le drapeau n’est `CDataExchange` pas zéro si l’objet est utilisé pour déplacer les données des contrôles de dialogue aux membres des données de classe dialogue après que l’utilisateur a modifié les contrôles. Le drapeau est nul si l’objet est utilisé pour initialiser les contrôles de dialogue des membres des données de classe dialogue.

Le drapeau est également nonzero pendant la validation des données de dialogue (DDV).

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd

Contient un pointeur sur [l’objet CWnd](../../mfc/reference/cwnd-class.md) pour lequel l’échange de données de dialogue (DDX) ou la validation (DDV) a lieu.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Notes

Cet objet est généralement un objet [CDialog.](../../mfc/reference/cdialog-class.md) Les implémenteurs de routines personnalisées DDX ou DDV peuvent utiliser ce pointeur pour obtenir l’accès à la fenêtre de dialogue qui contient les contrôles sur lequel ils fonctionnent.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl

Le cadre appelle cette fonction membre à préparer le contrôle spécifié pour l’échange de données de dialogue (DDX) et la validation (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC (en)*<br/>
L’ID du contrôle à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Le HWND du contrôle en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) plutôt pour modifier les contrôles; utiliser cette fonction de membre pour tous les autres contrôles.

La préparation consiste à stocker le HWND du contrôle dans la `CDataExchange` classe. Le cadre utilise cette poignée pour rétablir l’accent sur le contrôle précédemment concentré en cas de défaillance DDX ou DDV.

Les implémenteurs de routines personnalisées `PrepareCtrl` DDX ou DDV devraient faire appel à tous les contrôles non-édits pour lesquels ils échangent des données via DDX ou valident des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl

Le cadre appelle cette fonction membre pour préparer le contrôle de modification spécifié pour l’échange de données de dialogue (DDX) et la validation (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC (en)*<br/>
L’ID du contrôle de modification à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Le HWND du contrôle d’édition en cours de préparation pour DDX ou DDV.

### <a name="remarks"></a>Notes

Utilisez [PrepareCtrl](#preparectrl) à la place pour tous les contrôles non-édit.

La préparation se compose de deux choses. Tout `PrepareEditCtrl` d’abord, stocke le `CDataExchange` HWND du contrôle dans la classe. Le cadre utilise cette poignée pour rétablir l’accent sur le contrôle précédemment concentré en cas de défaillance DDX ou DDV. Deuxièmement, `PrepareEditCtrl` définit un `CDataExchange` drapeau dans la classe pour indiquer que le contrôle dont les données sont échangées ou validées est un contrôle de modification.

Les implémenteurs de routines personnalisées `PrepareEditCtrl` DDX ou DDV devraient appeler pour tous les contrôles d’édition pour lesquels ils échangent des données via DDX ou valident des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PRepareOleCtrl

Le cadre appelle cette fonction membre à préparer le contrôle OLE spécifié pour l’échange de données de dialogue (DDX) et la validation (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Paramètres

*nIDC (en)*<br/>
L’ID du contrôle OLE à préparer pour DDX ou DDV.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le site de contrôle OLE.

### <a name="remarks"></a>Notes

Utilisez [PrepareEditCtrl](#prepareeditctrl) plutôt pour modifier les contrôles ou [PrepareCtrl](#preparectrl) pour tous les autres contrôles non-OLE.

Les implémenteurs de routines personnalisées `PrepareOleCtrl` DDX ou DDV devraient faire appel à tous les contrôles OLE pour lesquels ils échangent des données via DDX ou valident des données via DDV.

Pour plus d’informations sur l’écriture de vos propres routines DDX et DDV, voir [Note technique 26](../../mfc/tn026-ddx-and-ddv-routines.md). Pour un aperçu de DDX et DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and [Dialog Box Topics](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
