---
description: 'En savoir plus sur : classe CSingleDocTemplate'
title: CSingleDocTemplate, classe
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 611cada1c90fa776bafb78f0856658cd1bd0a8e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264620"
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
|[CSingleDocTemplate :: CSingleDocTemplate](#csingledoctemplate)|Construit un objet `CSingleDocTemplate`.|

## <a name="remarks"></a>Notes

Une application SDI utilise la fenêtre frame principale pour afficher un document. un seul document peut être ouvert à la fois.

Un modèle de document définit la relation entre trois types de classes :

- Classe de document à partir de laquelle vous dérivez `CDocument` .

- Une classe d’affichage, qui affiche les données de la classe de document indiquée ci-dessus. Vous pouvez dériver cette classe à partir de `CView` ,, `CScrollView` `CFormView` ou `CEditView` . (Vous pouvez également utiliser `CEditView` directement.)

- Classe de fenêtre frame, qui contient la vue. Pour un modèle de document SDI, vous pouvez dériver cette classe de `CFrameWnd` ; si vous n’avez pas besoin de personnaliser le comportement de la fenêtre frame principale, vous pouvez utiliser `CFrameWnd` directement sans dériver votre propre classe.

Une application SDI prend généralement en charge un type de document, de sorte qu’elle n’a qu’un seul `CSingleDocTemplate` objet. Un seul document peut être ouvert à la fois.

Vous n’avez pas besoin d’appeler de fonctions membres de `CSingleDocTemplate` , à l’exception du constructeur. Le Framework gère les `CSingleDocTemplate` objets en interne.

Pour plus d’informations sur l’utilisation de `CSingleDocTemplate` , consultez [modèles de document et processus de création de document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a> CSingleDocTemplate :: CSingleDocTemplate

Construit un objet `CSingleDocTemplate`.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Il peut s’agir d’un menu, d’une icône, d’une table d’accélérateurs et de ressources de type chaîne.

La ressource de type chaîne se compose de sept sous-chaînes séparées par le caractère « \n » (le caractère « \n » est requis en tant qu’espace réservé si aucune sous-chaîne n’est incluse ; Toutefois, les caractères « \n » de fin ne sont pas nécessaires); ces sous-chaînes décrivent le type de document. Pour plus d’informations sur les sous-chaînes, consultez [CDocTemplate :: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Vous pouvez modifier cette chaîne à l’aide de l’éditeur de chaînes. la chaîne entière apparaît sous la forme d’une entrée unique dans l’éditeur de chaînes, et non pas sous la forme de sept entrées distinctes.

Pour plus d’informations sur ces types de ressources, consultez l' [éditeur de chaînes](../../windows/string-editor.md).

*pDocClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de document. Cette classe est une `CDocument` classe dérivée de que vous définissez pour représenter vos documents.

*pFrameClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de fenêtre frame. Cette classe peut être une `CFrameWnd` classe dérivée de, ou elle peut être `CFrameWnd` elle-même si vous souhaitez utiliser le comportement par défaut pour votre fenêtre frame principale.

*pViewClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de vue. Cette classe est une `CView` classe dérivée de que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Allouez dynamiquement un `CSingleDocTemplate` objet et transmettez- `CWinApp::AddDocTemplate` le à partir de la `InitInstance` fonction membre de votre classe d’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate, classe](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CWinApp (classe)](../../mfc/reference/cwinapp-class.md)
