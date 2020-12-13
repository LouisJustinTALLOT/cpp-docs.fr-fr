---
description: 'En savoir plus sur : classe CMultiPageDHtmlDialog'
title: CMultiPageDHtmlDialog, classe
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 1f7f8c2081687c71a98e427bb5396cfa47a73deb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331536"
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
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construit un objet de boîte de dialogue DHTML (de style Assistant).|
|[CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|Détruit un objet de boîte de dialogue DHTML multipage.|

## <a name="remarks"></a>Notes

Le mécanisme permettant d’y parvenir est un [mappage d’événements DHTML et URL](dhtml-event-maps.md), qui contient des tables d’événements incorporées pour chaque page.

## <a name="example"></a>Exemple

Cette boîte de dialogue multipage suppose trois ressources HTML qui définissent des fonctionnalités simples de type assistant. La première page a un bouton **suivant** , le deuxième bouton **précédent** et **suivant** et le troisième bouton **précédent** . Quand l’un des boutons est enfoncé, une fonction de gestionnaire appelle [CDHtmlDialog :: LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) pour charger la nouvelle page appropriée.

Les parties pertinentes de la déclaration de classe (dans CMyMultiPageDlg. h) :

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Les parties pertinentes de l’implémentation de la classe (dans CMyMultipageDlg. cpp) :

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

**En-tête :** afxdhtml. h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a> CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Construit un objet de boîte de dialogue DHTML (de style Assistant).

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
Chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*szHtmlResID*<br/>
Chaîne terminée par le caractère null qui est le nom d’une ressource HTML.

*pParentWnd*<br/>
Pointeur vers l’objet de fenêtre parent ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel l’objet de boîte de dialogue appartient. Si la valeur est NULL, la fenêtre parente de l’objet Dialog est définie sur la fenêtre d’application principale.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

*nHtmlResID*<br/>
Contient le numéro d’identification d’une ressource HTML.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a> CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog

Détruit un objet de boîte de dialogue DHTML multipage.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
