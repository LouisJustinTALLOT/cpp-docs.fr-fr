---
title: CMultiPageDHtmlDialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8f7c74610916d556c628e35672e5737d780694a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075799"
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
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construit un objet de boîte de dialogue multipage (Assistant-style) DHTML.|
|[CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Détruit un objet de boîte de dialogue multipage DHTML.|

## <a name="remarks"></a>Notes

Le mécanisme pour effectuer cette opération est un [table d’événements DHTML et URL](dhtml-event-maps.md), tables d’événements pour chaque page contenant des images.

## <a name="example"></a>Exemple

Cette boîte de dialogue multipage part du principe que les trois ressources HTML qui définissent des fonctionnalités de type Assistant simples. La première page a un **suivant** bouton, le second une **Prev** et **suivant** bouton et le troisième un **Prev** bouton. Lorsqu’un des boutons est activé, une fonction de gestionnaire appelle [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) pour charger la nouvelle page appropriée.

Les parties pertinentes de la déclaration de classe (CMyMultiPageDlg.h) :

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Les parties pertinentes de l’implémentation de classe (dans CMyMultipageDlg.cpp) :

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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdhtml.h

##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Construit un objet de boîte de dialogue multipage (Assistant-style) DHTML.

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
La chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*szHtmlResID*<br/>
La chaîne se terminant par null qui est le nom d’une ressource HTML.

*pParentWnd*<br/>
Un pointeur vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

*nHtmlResID*<br/>
Contient le numéro d’ID d’une ressource HTML.

##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog

Détruit un objet de boîte de dialogue multipage DHTML.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
