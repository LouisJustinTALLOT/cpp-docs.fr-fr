---
title: CMultiPageDHtmlDialog, classe
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319663"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog, classe

Une boîte de dialogue multipage affiche plusieurs pages HTML de manière séquentielle et gère les événements de chaque page.

## <a name="syntax"></a>Syntaxe

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construit un objet de dialogue DHTML à plusieurs pages (de style sorcier).|
|[CMultiPageDHtmlDialog: :-CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|Détruit un objet de dialogue DHTML à plusieurs pages.|

## <a name="remarks"></a>Notes

Le mécanisme pour ce faire est une [carte d’événement DHTML et URL](dhtml-event-maps.md), qui contient des cartes d’événements intégrées pour chaque page.

## <a name="example"></a>Exemple

Ce dialogue multipage suppose trois ressources HTML qui définissent la fonctionnalité simple de sorcier. La première page a un bouton **Suivant,** la seconde un bouton **Prev** et **Suivant,** et la troisième un bouton **Prev.** Lorsque l’un des boutons est pressé, une fonction de gestionnaire appelle [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) pour charger la nouvelle page appropriée.

Les parties pertinentes de la déclaration de classe (dans CMyMultiPageDlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Les parties pertinentes de la mise en œuvre de la classe (dans CMyMultipageDlg.cpp) :

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Construit un objet de dialogue DHTML à plusieurs pages (de style sorcier).

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
La chaîne non terminée qui est le nom d’une ressource de modèle de boîte de dialogue.

*szHtmlResID*<br/>
La chaîne non terminée qui est le nom d’une ressource HTML.

*pParentWnd*<br/>
Un pointeur vers l’objet de fenêtre du parent ou du propriétaire (du type [CWnd)](../../mfc/reference/cwnd-class.md)auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

*nHtmlResID (en anglais)*<br/>
Contient le numéro d’identification d’une ressource HTML.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog: :-CMultiPageDHtmlDialog

Détruit un objet de dialogue DHTML à plusieurs pages.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
