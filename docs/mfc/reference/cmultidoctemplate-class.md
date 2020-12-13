---
description: 'En savoir plus sur : CMultiDocTemplate, classe'
title: CMultiDocTemplate, classe
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 70b77c04fed41da3b5f025f6a600b9ecfd4bc89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331563"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate, classe

Définit un modèle de document qui implémente l'interface multidocument (MDI).

## <a name="syntax"></a>Syntaxe

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Membres

Les fonctions membres de cette classe sont virtuelles. Consultez [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) et [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) pour obtenir de la documentation.

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMultiDocTemplate :: CMultiDocTemplate](#cmultidoctemplate)|Construit un objet `CMultiDocTemplate`.|

## <a name="remarks"></a>Notes

Une application MDI utilise la fenêtre frame principale comme un espace de travail dans lequel l’utilisateur peut ouvrir zéro, une ou plusieurs fenêtres frame de document, chacune affichant un document. Pour obtenir une description plus détaillée de l’interface MDI, consultez *instructions relatives à l’interface Windows pour la conception de logiciels*.

Un modèle de document définit les relations entre trois types de classes :

- Classe de document, que vous dérivez de [CDocument](../../mfc/reference/cdocument-class.md).

- Une classe d’affichage, qui affiche les données de la classe de document indiquée ci-dessus. Vous pouvez dériver cette classe de [CView](../../mfc/reference/cview-class.md),, `CScrollView` `CFormView` ou `CEditView` . (Vous pouvez également utiliser `CEditView` directement.)

- Classe de fenêtre frame, qui contient la vue. Pour un modèle de document MDI, vous pouvez dériver cette classe de `CMDIChildWnd` , ou, si vous n’avez pas besoin de personnaliser le comportement des fenêtres frame de document, vous pouvez utiliser [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directement sans dériver votre propre classe.

Une application MDI peut prendre en charge plusieurs types de documents, et les documents de types différents peuvent être ouverts en même temps. Votre application possède un modèle de document pour chaque type de document qu’elle prend en charge. Par exemple, si votre application MDI prend en charge à la fois les feuilles de calcul et les documents texte, l’application a deux `CMultiDocTemplate` objets.

L’application utilise le ou les modèles de document lorsque l’utilisateur crée un nouveau document. Si l’application prend en charge plusieurs types de document, l’infrastructure obtient les noms des types de documents pris en charge à partir des modèles de document et les affiche dans une liste de la boîte de dialogue fichier nouveau. Une fois que l’utilisateur a sélectionné un type de document, l’application crée un objet de classe de document, un objet de fenêtre frame et un objet de vue et les attache l’un à l’autre.

Vous n’avez pas besoin d’appeler de fonctions membres de `CMultiDocTemplate` , à l’exception du constructeur. Le Framework gère les `CMultiDocTemplate` objets en interne.

Pour plus d’informations sur `CMultiDocTemplate` , consultez [modèles de document et processus de création de document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a> CMultiDocTemplate :: CMultiDocTemplate

Construit un objet `CMultiDocTemplate`.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Il peut s’agir d’un menu, d’une icône, d’une table d’accélérateurs et de ressources de type chaîne.

La ressource de type chaîne se compose de sept sous-chaînes séparées par le caractère « \n » (le caractère « \n » est requis comme espace réservé si une sous-chaîne n’est pas incluse ; Toutefois, les caractères « \n » de fin ne sont pas nécessaires); ces sous-chaînes décrivent le type de document. Pour plus d’informations sur les sous-chaînes, consultez [CDocTemplate :: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

La chaîne commence par un caractère « \n », car la première sous-chaîne n’est pas utilisée pour les applications MDI et n’est donc pas incluse. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de chaînes. la chaîne entière apparaît sous la forme d’une entrée unique dans l’éditeur de chaînes, et non pas sous la forme de sept entrées distinctes.

Pour plus d’informations sur ces types de ressources, consultez [éditeurs de ressources](../../windows/resource-editors.md).

*pDocClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de document. Cette classe est une `CDocument` classe dérivée de que vous définissez pour représenter vos documents.

*pFrameClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de fenêtre frame. Cette classe peut être une `CMDIChildWnd` classe dérivée de, ou elle peut être `CMDIChildWnd` elle-même si vous souhaitez utiliser le comportement par défaut pour vos fenêtres frame de document.

*pViewClass*<br/>
Pointe vers l' `CRuntimeClass` objet de la classe de vue. Cette classe est une `CView` classe dérivée de que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Allouez dynamiquement un `CMultiDocTemplate` objet pour chaque type de document pris en charge par votre application et transmettez- `CWinApp::AddDocTemplate` le à partir de la `InitInstance` fonction membre de votre classe d’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Voici un deuxième exemple.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate, classe](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp (classe)](../../mfc/reference/cwinapp-class.md)
