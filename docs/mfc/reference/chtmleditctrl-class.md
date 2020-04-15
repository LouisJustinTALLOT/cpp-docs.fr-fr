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
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366839"
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
|[CHtmlEditCtrl::Créer](#create)|Crée un contrôle WebBrowser ActiveX et `CHtmlEditCtrl` le fixe à l’objet. Cette fonction met automatiquement le contrôle WebBrowser ActiveX en mode d’édition.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Récupère l’interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) sur le document actuellement chargé dans le contrôle WebBrowser contenu.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Récupère l’URL à un document par défaut pour charger dans le contrôle WebBrowser contenu.|

## <a name="remarks"></a>Notes

Le contrôle WebBrowser hébergé est automatiquement mis en mode d’édition après sa création.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

Construit un objet `CHtmlEditCtrl`.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Créer

Crée un contrôle WebBrowser ActiveX et `CHtmlEditCtrl` le fixe à l’objet. Le contrôle WebBrowser ActiveX navigue automatiquement vers un document par défaut, puis est placé en mode d’édition par cette fonction.

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

*lpszWindowName (en)*<br/>
Ce paramètre est inutilisé.

*dwStyle (en)*<br/>
Ce paramètre est inutilisé.

*Rect*<br/>
Spécifie la taille et la position du contrôle.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle.

*pContext*<br/>
Ce paramètre est inutilisé.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument

Récupère l’interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) sur le document actuellement chargé dans le contrôle WebBrowser contenu

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Paramètres

*ppDocument*<br/>
L’interface de document.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument

Récupère l’URL à un document par défaut pour charger dans le contrôle WebBrowser contenu.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
