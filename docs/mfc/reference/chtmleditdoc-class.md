---
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
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352171"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc, classe

Avec [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), fournit la fonctionnalité de la plate-forme d’édition WebBrowser dans le cadre de l’architecture de vision des documents MFC.

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
|[CHtmlEditDoc::GetView](#getview)|Récupère l’objet `CHtmlEditView` attaché à ce document.|
|[CHtmlEditDoc::IsModified](#ismodified)|Indique si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.|
|[CHtmlEditDoc::OpenURL](#openurl)|Ouvre une URL.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Spécifications

**En-tête :** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc

Construit un objet `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView

Récupère l’objet [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) joint à ce document.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie un pointeur `CHtmlEditView` à l’objet du document.

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc::IsModified

Indique si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL

Ouvre une URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
URL à ouvrir.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="see-also"></a>Voir aussi

[Échantillon HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
