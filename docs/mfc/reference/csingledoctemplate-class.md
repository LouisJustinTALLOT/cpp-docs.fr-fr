---
title: CSingleDocTemplate, classe
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318350"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate, classe

Définit un modèle de document qui implémente l'interface monodocument (SDI).

## <a name="syntax"></a>Syntaxe

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Construit un objet `CSingleDocTemplate`.|

## <a name="remarks"></a>Notes

Une application SDI utilise la fenêtre du cadre principal pour afficher un document; un seul document peut être ouvert à la fois.

Un modèle de document définit la relation entre trois types de classes :

- Une classe de documents, `CDocument`dont vous dérivez .

- Une classe de vue, qui affiche les données de la classe de documents énumérés ci-dessus. Vous pouvez tirer `CView`cette `CScrollView` `CFormView`classe `CEditView`de , , , ou . (Vous pouvez `CEditView` également utiliser directement.)

- Un cours de fenêtre de cadre, qui contient la vue. Pour un modèle de document SDI, `CFrameWnd`vous pouvez tirer cette classe de ; si vous n’avez pas besoin de personnaliser le comportement `CFrameWnd` de la fenêtre de cadre principale, vous pouvez utiliser directement sans dérivant votre propre classe.

Une application SDI prend généralement en charge un `CSingleDocTemplate` type de document, de sorte qu’il n’a qu’un seul objet. Un seul document peut être ouvert à la fois.

Vous n’avez pas besoin d’appeler les fonctions des membres, `CSingleDocTemplate` sauf le constructeur. Le cadre `CSingleDocTemplate` gère les objets en interne.

Pour plus d’informations sur l’utilisation `CSingleDocTemplate`, voir les modèles de documents et le processus de création de [documents/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate

Construit un objet `CSingleDocTemplate`.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource (en)*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Cela peut inclure le menu, l’icône, la table d’accélérateur, et les ressources de chaîne.

La ressource de chaîne se compose d’un plus grand 7 sous-cordes séparés par le caractère 'n' (le caractère 'n' est nécessaire en tant que placeholder si un sous-réseau n’est pas inclus; cependant, les caractères de fuite 'n' ne sont pas nécessaires); ces sous-cordes décrivent le type de document. Pour plus d’informations sur les sous-cordes, voir [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Vous pouvez modifier cette chaîne à l’aide de l’éditeur de cordes; la chaîne entière apparaît comme une seule entrée dans l’éditeur de cordes, pas comme sept entrées distinctes.

Pour plus d’informations sur ces types de ressources, voir [l’éditeur à cordes](../../windows/string-editor.md).

*classe pDoc*<br/>
Indique l’objet `CRuntimeClass` de la classe de documents. Cette classe `CDocument`est une classe dérivée que vous définissez pour représenter vos documents.

*pFrameClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de fenêtre de cadre. Cette classe peut `CFrameWnd`être une classe dérivée, ou elle peut être `CFrameWnd` elle-même si vous voulez un comportement par défaut pour votre fenêtre cadre principale.

*pViewClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de vue. Cette classe `CView`est une classe dérivée que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Répartir dynamiquement `CSingleDocTemplate` un objet et `CWinApp::AddDocTemplate` le `InitInstance` transmettre à partir de la fonction membre de votre classe d’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate, classe](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[CWinApp, classe](../../mfc/reference/cwinapp-class.md)
