---
description: 'En savoir plus sur : classe CMFCSpinButtonCtrl'
title: CMFCSpinButtonCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 87e9abc94247416704ab801beeaa1953c4cceb46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339631"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl, classe

La `CMFCSpinButtonCtrl` classe prend en charge un gestionnaire visuel qui dessine un contrôle de bouton toupie.

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
|[CMFCSpinButtonCtrl :: OnDraw](#ondraw)|Repeint le contrôle de bouton toupie actuel.|

## <a name="remarks"></a>Notes

Pour utiliser un gestionnaire visuel pour dessiner un contrôle de bouton toupie dans votre application, remplacez toutes les instances de la `CSpinButtonCtrl` classe par la `CMFCSpinButtonCtrl` classe.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un objet de la `CMFCSpinButtonCtrl` classe et utiliser sa `Create` méthode.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxspinbuttonctrl. h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a> CMFCSpinButtonCtrl :: OnDraw

Repeint le contrôle de bouton toupie actuel.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

### <a name="remarks"></a>Notes

L’infrastructure appelle la `CMFCSpinButtonCtrl::OnPaint` méthode pour gérer le message [CWnd :: OnPaint](../../mfc/reference/cwnd-class.md#onpaint) , et cette méthode appelle à son tour cette `CMFCSpinButtonCtrl::OnDraw` méthode. Substituez cette méthode pour personnaliser la façon dont l’infrastructure dessine le contrôle spin Button.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager, classe](../../mfc/reference/cmfcvisualmanager-class.md)
