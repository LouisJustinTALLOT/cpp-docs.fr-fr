---
description: 'En savoir plus sur : classe CHtmlEditCtrl'
title: CHtmlEditCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: d395f0f9f3e8b5ae10ad0ce35b2b1e410633e8d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183995"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl, classe

Fournit les fonctionnalités du contrôle ActiveX WebBrowser dans une fenêtre MFC.

## <a name="syntax"></a>Syntaxe

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Construit un objet `CHtmlEditCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHtmlEditCtrl :: Create](#create)|Crée un contrôle ActiveX WebBrowser et l’attache à l' `CHtmlEditCtrl` objet. Cette fonction met automatiquement le contrôle ActiveX WebBrowser en mode édition.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Récupère l’interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) sur le document actuellement chargé dans le contrôle WebBrowser contenu.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser contenu.|

## <a name="remarks"></a>Notes

Le contrôle WebBrowser hébergé est automatiquement mis en mode édition après sa création.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a> CHtmlEditCtrl::CHtmlEditCtrl

Construit un objet `CHtmlEditCtrl`.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a> CHtmlEditCtrl :: Create

Crée un contrôle ActiveX WebBrowser et l’attache à l' `CHtmlEditCtrl` objet. Le contrôle ActiveX WebBrowser accède automatiquement à un document par défaut, puis est placé en mode édition par cette fonction.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszWindowName*<br/>
Ce paramètre est inutilisé.

*dwStyle*<br/>
Ce paramètre est inutilisé.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle.

*pContext*<br/>
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a> CHtmlEditCtrl::GetDHtmlDocument

Récupère l’interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) sur le document actuellement chargé dans le contrôle WebBrowser contenu

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
Interface de document.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a> CHtmlEditCtrl::GetStartDocument

Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser contenu.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
