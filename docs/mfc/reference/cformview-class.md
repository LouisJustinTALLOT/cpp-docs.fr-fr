---
title: Classe CFormView
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
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373799"
---
# <a name="cformview-class"></a>Classe CFormView

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

En substance, me mode Formulaire est une vue qui contient des contrôles. La disposition de ces contrôles est basée sur une ressource de modèle de boîte de dialogue. Utilisez `CFormView` si vous voulez des formulaires dans votre application. Ces vues prennent en charge le défilement, au besoin, en utilisant la fonctionnalité [CScrollView.](../../mfc/reference/cscrollview-class.md)

Lorsque vous [créez une application basée sur les formulaires,](../../mfc/reference/creating-a-forms-based-mfc-application.md)vous pouvez baser sa classe de vue sur, `CFormView`ce qui en fait une application basée sur des formulaires.

Vous pouvez également insérer de nouveaux [sujets de formulaire](../../mfc/form-views-mfc.md) dans des applications basées sur des documents. Même si, au départ, votre application ne prend pas en charge les formulaires, Visual C++ ajoute cette prise en charge du moment que vous insérez un nouveau formulaire.

L'Assistant Application MFC et la commande Ajouter une classe sont les méthodes recommandées pour créer des applications basées sur les formulaires. Si vous avez besoin de créer une application basée sur des formulaires sans utiliser ces méthodes, voir [Créer une application basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView

Construit un objet `CFormView`.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de dialogue-modèle.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de dialogue.

### <a name="remarks"></a>Notes

Lorsque vous créez un objet `CFormView`d’un type dérivé de , invoquez l’un des constructeurs pour créer l’objet de vue et identifier la ressource de dialogue sur laquelle la vue est basée. Vous pouvez identifier la ressource soit par son nom (passez une chaîne comme argument au constructeur) ou par sa pièce d’identité (passez un insignable non signé comme argument).

La fenêtre de vue de forme `CWnd::Create` et les contrôles d’enfant ne sont pas créés jusqu’à ce qu’on l’appelle. `CWnd::Create`est appelé par le cadre dans le cadre du processus de création du document et de la vue, qui est piloté par le modèle de document.

> [!NOTE]
> Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, invoquez le constructeur, `CFormView::CFormView`avec le nom de ressource ou d’identification comme argument tel que indiqué dans l’aperçu de classe précédent.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted

Utilisé par MFC pour faire en sorte que l'initialisation se termine avant que d'autres opérations soient entreprises.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Valeur de retour

True si la fonction d'initialisation de cette boîte de dialogue a abouti.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)
