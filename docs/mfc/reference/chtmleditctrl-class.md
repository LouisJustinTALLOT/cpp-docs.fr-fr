---
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
ms.openlocfilehash: 6f5c465a8ec9c8f54af5545e66fb849a08d241af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389409"
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
|[CHtmlEditCtrl::Create](#create)|Crée un contrôle WebBrowser ActiveX et l’attache à la `CHtmlEditCtrl` objet. Cette fonction place automatiquement le contrôle WebBrowser ActiveX en mode édition.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Récupère le [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interface sur le document actuellement chargé dans le contrôle WebBrowser relation contenant-contenu.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser relation contenant-contenu.|

## <a name="remarks"></a>Notes

Mode d’édition WebBrowser hébergé contrôle est automatiquement placé dans après sa création.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxhtml.h

##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl

Construit un objet `CHtmlEditCtrl`.

```
CHtmlEditCtrl();
```

##  <a name="create"></a>  CHtmlEditCtrl::Create

Crée un contrôle WebBrowser ActiveX et l’attache à la `CHtmlEditCtrl` objet. Le WebBrowser ActiveX contrôle navigue automatiquement vers un document par défaut et est placé dans le mode édition par cette fonction.

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

*rect*<br/>
Spécifie la taille et la position du contrôle.

*pParentWnd*<br/>
Spécifie la fenêtre du contrôle parent. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle

*pContext*<br/>
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument

Récupère le [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interface sur le document actuellement chargé dans le contrôle WebBrowser relation contenant-contenu

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
L’interface de document.

##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument

Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser relation contenant-contenu.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
