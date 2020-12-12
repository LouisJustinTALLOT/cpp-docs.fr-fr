---
description: 'En savoir plus sur : classe CHtmlEditDoc'
title: CHtmlEditDoc, classe
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: 5fb8187ff7925efc5bdfa6a0079a8ec4b186ae63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115311"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc, classe

Avec [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), fournit les fonctionnalités de la plateforme d’édition WebBrowser dans le contexte de l’architecture document/vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Construit un objet `CHtmlEditDoc`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHtmlEditDoc :: GetView](#getview)|Récupère l' `CHtmlEditView` objet joint à ce document.|
|[CHtmlEditDoc::IsModified](#ismodified)|Retourne une valeur indiquant si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.|
|[CHtmlEditDoc :: OpenURL](#openurl)|Ouvre une URL.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Spécifications

**En-tête :** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a> CHtmlEditDoc::CHtmlEditDoc

Construit un objet `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a> CHtmlEditDoc :: GetView

Récupère l’objet [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) joint à ce document.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l’objet du document `CHtmlEditView` .

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a> CHtmlEditDoc::IsModified

Retourne une valeur indiquant si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a> CHtmlEditDoc :: OpenURL

Ouvre une URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
URL à ouvrir.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="see-also"></a>Voir aussi

[HTMLEdit, exemple](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
