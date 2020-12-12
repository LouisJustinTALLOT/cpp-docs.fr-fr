---
description: 'En savoir plus sur : CFormView, classe'
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
ms.openlocfilehash: ec37a3819f299830fef96bfdf93c0170b2969c66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184307"
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
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Utilisé pour la synchronisation pendant l'initialisation.|

## <a name="remarks"></a>Notes

En substance, me mode Formulaire est une vue qui contient des contrôles. La disposition de ces contrôles est basée sur une ressource de modèle de boîte de dialogue. Utilisez `CFormView` si vous voulez des formulaires dans votre application. Ces vues prennent en charge le défilement, si nécessaire, à l’aide de la fonctionnalité [CScrollView](../../mfc/reference/cscrollview-class.md) .

Lorsque vous [créez une application Forms-Based](../../mfc/reference/creating-a-forms-based-mfc-application.md), vous pouvez baser sa classe d’affichage sur `CFormView` , en faisant de celle-ci une application basée sur des formulaires.

Vous pouvez également insérer de nouvelles [rubriques de formulaire](../../mfc/form-views-mfc.md) dans des applications basées sur des documents. Même si, au départ, votre application ne prend pas en charge les formulaires, Visual C++ ajoute cette prise en charge du moment que vous insérez un nouveau formulaire.

L'Assistant Application MFC et la commande Ajouter une classe sont les méthodes recommandées pour créer des applications basées sur les formulaires. Si vous avez besoin de créer une application basée sur des formulaires sans utiliser ces méthodes, consultez [création d’une application Forms-Based](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cformviewcformview"></a><a name="cformview"></a> CFormView :: CFormView

Construit un objet `CFormView`.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle de boîte de dialogue.

*nIDTemplate*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

### <a name="remarks"></a>Notes

Quand vous créez un objet d’un type dérivé de `CFormView` , appelez l’un des constructeurs pour créer l’objet de vue et identifier la ressource de boîte de dialogue sur laquelle la vue est basée. Vous pouvez identifier la ressource par son nom (passer une chaîne en tant qu’argument au constructeur) ou par son ID (passer un entier non signé comme argument).

La fenêtre de vue de formulaire et les contrôles enfants ne sont pas créés tant que `CWnd::Create` n’est pas appelé. `CWnd::Create` est appelé par l’infrastructure dans le cadre du processus de création de document et de vue, piloté par le modèle de document.

> [!NOTE]
> Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, appelez le constructeur, `CFormView::CFormView` , avec le nom de la ressource ou l’ID comme argument, comme indiqué dans la vue d’ensemble de la classe précédente.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a> CFormView :: IsInitDlgCompleted

Utilisé par MFC pour faire en sorte que l'initialisation se termine avant que d'autres opérations soient entreprises.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Valeur renvoyée

True si la fonction d'initialisation de cette boîte de dialogue a abouti.

## <a name="see-also"></a>Voir aussi

[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView (classe)](../../mfc/reference/cscrollview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDialog (classe)](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView (classe)](../../mfc/reference/cscrollview-class.md)
