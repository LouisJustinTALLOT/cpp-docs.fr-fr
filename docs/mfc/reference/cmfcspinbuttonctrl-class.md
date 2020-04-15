---
title: CMFCSpinButtonCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376179"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl, classe

La `CMFCSpinButtonCtrl` classe prend en charge un gestionnaire visuel qui dessine un contrôle de bouton de spin.

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
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Repeinte le contrôle actuel du bouton de rotation.|

## <a name="remarks"></a>Notes

Pour utiliser un gestionnaire visuel pour dessiner un contrôle de `CSpinButtonCtrl` bouton de `CMFCSpinButtonCtrl` spin dans votre application, remplacez tous les instances de la classe par la classe.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer `CMFCSpinButtonCtrl` un objet `Create` de la classe et utiliser sa méthode.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw

Repeinte le contrôle actuel du bouton de rotation.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

### <a name="remarks"></a>Notes

Le cadre `CMFCSpinButtonCtrl::OnPaint` appelle la méthode pour gérer le [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) `CMFCSpinButtonCtrl::OnDraw` message, et cette méthode à son tour appelle cette méthode. Remplacer cette méthode pour personnaliser la façon dont le cadre dessine le contrôle du bouton de rotation.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)
