---
title: CHtmlEditDoc, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77219f4cac64faf2604c427a2c4abf3babfd26a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425357"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc, classe

Avec [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), fournit les fonctionnalités de la plateforme d’édition WebBrowser dans le contexte de l’architecture document / vue MFC.

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
|[CHtmlEditDoc::GetView](#getview)|Récupère le `CHtmlEditView` objet attaché à ce document.|
|[CHtmlEditDoc::IsModified](#ismodified)|Indique si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.|
|[CHtmlEditDoc::OpenURL](#openurl)|Ouvre une URL.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

Construit un objet `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

Récupère le [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objet attaché à ce document.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le document `CHtmlEditView` objet.

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

Indique si le contrôle WebBrowser de la vue associée contient un document qui a été modifié par l’utilisateur.

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

Ouvre une URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
L’URL à ouvrir.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

## <a name="see-also"></a>Voir aussi

[Exemple HTMLEdit](../../visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

