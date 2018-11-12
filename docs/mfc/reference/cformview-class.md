---
title: CFormView, classe
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 37ae7ca2efeb579cba388e22cf0fe450a068e721
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651956"
---
# <a name="cformview-class"></a>CFormView, classe

Classe de base utilisée pour les modes formulaire.

## <a name="syntax"></a>Syntaxe

```
class CFormView : public CScrollView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Construit un objet `CFormView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Utilisé pour la synchronisation pendant l’initialisation.|

## <a name="remarks"></a>Notes

En substance, me mode Formulaire est une vue qui contient des contrôles. La disposition de ces contrôles est basée sur une ressource de modèle de boîte de dialogue. Utilisez `CFormView` si vous voulez des formulaires dans votre application. Ces vues prennent en charge le défilement, en fonction des besoins, à l’aide de la [CScrollView](../../mfc/reference/cscrollview-class.md) fonctionnalité.

Lorsque vous êtes [création d’une Application basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md), vous pouvez baser sa classe de vue sur `CFormView`, rendant une application basée sur les formulaires.

Vous pouvez également insérer de nouvelles [rubriques relatives aux formulaires](../../mfc/form-views-mfc.md) dans des applications basée sur la vue de document. Même si, au départ, votre application ne prend pas en charge les formulaires, Visual C++ ajoute cette prise en charge du moment que vous insérez un nouveau formulaire.

L'Assistant Application MFC et la commande Ajouter une classe sont les méthodes recommandées pour créer des applications basées sur les formulaires. Si vous avez besoin créer une application basée sur les formulaires sans utiliser ces méthodes, consultez [création d’une Application basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

Construit un objet `CFormView`.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet d’un type dérivé `CFormView`, appeler un des constructeurs pour créer l’objet de vue et d’identifier la ressource de boîte de dialogue sur laquelle repose la vue. Vous pouvez identifier la ressource par son nom (passez une chaîne comme argument au constructeur) ou par son ID (pass un entier non signé comme argument).

Les contrôles de fenêtre et enfant en mode formulaire ne sont pas créés tant que `CWnd::Create` est appelée. `CWnd::Create` est appelé par l’infrastructure en tant que partie du document et la vue processus de création, qui est déterminé par le modèle de document.

> [!NOTE]
>  Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, appelez le constructeur, `CFormView::CFormView`, avec le nom de la ressource ou l’ID en tant qu’argument comme indiqué dans la vue d’ensemble de classe précédentes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

Utilisé par MFC pour faire en sorte que l'initialisation se termine avant que d'autres opérations soient entreprises.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Valeur de retour

True si la fonction d'initialisation de cette boîte de dialogue a abouti.

## <a name="see-also"></a>Voir aussi

[Exemple MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[Exemple MFC VIEWEX](../../visual-cpp-samples.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)
