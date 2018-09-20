---
title: Cmfcspinbuttonctrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 756cdffc8f9f726e63b129f5f87a19eec01cd429
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440015"
---
# <a name="cmfcspinbuttonctrl-class"></a>Cmfcspinbuttonctrl, classe

Le `CMFCSpinButtonCtrl` classe prend en charge un gestionnaire visuel qui dessine un contrôle de bouton toupie (spin).

## <a name="syntax"></a>Syntaxe

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Constructeur par défaut.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Redessine le contrôle de bouton toupie (spin) actuel.|

## <a name="remarks"></a>Notes

Pour utiliser un gestionnaire visuel pour dessiner un contrôle de bouton toupie (spin) dans votre application, remplacez toutes les instances de la `CSpinButtonCtrl` classe avec la `CMFCSpinButtonCtrl` classe.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un objet de la `CMFCSpinButtonCtrl` classe et utiliser ses `Create` (méthode).

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

Redessine le contrôle de bouton toupie (spin) actuel.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
[in] Pointeur vers un contexte de périphérique.

### <a name="remarks"></a>Notes

Le framework appelle la `CMFCSpinButtonCtrl::OnPaint` méthode pour gérer la [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) message et que méthode appelle à son tour cette `CMFCSpinButtonCtrl::OnDraw` (méthode). Substituez cette méthode pour personnaliser la façon dont le framework Dessine le contrôle de bouton toupie (spin).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager, classe](../../mfc/reference/cmfcvisualmanager-class.md)
