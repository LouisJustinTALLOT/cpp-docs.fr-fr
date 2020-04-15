---
title: CMultiDocTemplate, classe
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319743"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate, classe

Définit un modèle de document qui implémente l'interface multidocument (MDI).

## <a name="syntax"></a>Syntaxe

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Construit un objet `CMultiDocTemplate`.|

## <a name="remarks"></a>Notes

Une application MDI utilise la fenêtre principale du cadre comme espace de travail dans lequel l’utilisateur peut ouvrir zéro ou plus de fenêtres de cadre de document, chacune d’entre elles affiche un document. Pour une description plus détaillée du MDI, voir *Windows Interface Guidelines for Software Design*.

Un modèle de document définit les relations entre trois types de classes :

- Une classe de documents, que vous dérivez de [CDocument](../../mfc/reference/cdocument-class.md).

- Une classe de vue, qui affiche les données de la classe de documents énumérés ci-dessus. Vous pouvez tirer cette classe `CScrollView` `CFormView`de `CEditView` [CView](../../mfc/reference/cview-class.md), , , ou . (Vous pouvez `CEditView` également utiliser directement.)

- Un cours de fenêtre de cadre, qui contient la vue. Pour un modèle de document MDI, `CMDIChildWnd`vous pouvez tirer cette classe de , ou, si vous n’avez pas besoin de personnaliser le comportement des fenêtres de cadre de document, vous pouvez utiliser [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directement sans dériger votre propre classe.

Une application MDI peut prendre en charge plus d’un type de document, et les documents de différents types peuvent être ouverts en même temps. Votre application a un modèle de document pour chaque type de document qu’elle prend en charge. Par exemple, si votre application MDI prend en charge à `CMultiDocTemplate` la fois les feuilles de calcul et les documents texte, l’application comporte deux objets.

L’application utilise le modèle de document lorsque l’utilisateur crée un nouveau document. Si l’application prend en charge plus d’un type de document, alors le cadre obtient les noms des types de documents pris en charge à partir des modèles de documents et les affiche dans une liste dans la boîte de dialogue Fichier Nouveau. Une fois que l’utilisateur a sélectionné un type de document, l’application crée un objet de classe de document, un objet de fenêtre de cadre, et un objet de vue et les attache les uns aux autres.

Vous n’avez pas besoin d’appeler les fonctions des membres, `CMultiDocTemplate` sauf le constructeur. Le cadre `CMultiDocTemplate` gère les objets en interne.

Pour plus `CMultiDocTemplate`d’informations sur , voir [Modèles de documents et le processus de création de documents/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

Construit un objet `CMultiDocTemplate`.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource (en)*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Cela peut inclure le menu, l’icône, la table d’accélérateur, et les ressources de chaîne.

La ressource de chaîne se compose d’un plus grand 7 sous-cordes séparés par le caractère 'n' (le caractère 'n' est nécessaire en tant que support de lieu si un sous-réseau n’est pas inclus; cependant, les caractères de fuite 'n' ne sont pas nécessaires); ces sous-cordes décrivent le type de document. Pour plus d’informations sur les sous-cordes, voir [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Notez que la chaîne commence par un caractère 'n'; c’est parce que le premier sous-corde n’est pas utilisé pour les applications MDI et n’est donc pas inclus. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de cordes; la chaîne entière apparaît comme une seule entrée dans l’éditeur de cordes, pas comme sept entrées distinctes.

Pour plus d’informations sur ces types de ressources, voir [Resource Editors](../../windows/resource-editors.md).

*classe pDoc*<br/>
Indique l’objet `CRuntimeClass` de la classe de documents. Cette classe `CDocument`est une classe dérivée que vous définissez pour représenter vos documents.

*pFrameClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de fenêtre de cadre. Cette classe peut `CMDIChildWnd`être une classe dérivée, ou elle peut être `CMDIChildWnd` elle-même si vous voulez un comportement par défaut pour vos fenêtres de cadre de document.

*pViewClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de vue. Cette classe `CView`est une classe dérivée que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Répartir dynamiquement `CMultiDocTemplate` un objet pour chaque type de document `CWinApp::AddDocTemplate` que `InitInstance` votre application prend en charge et transmette chacun à partir de la fonction membre de votre classe d’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Voici un deuxième exemple.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate, classe](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp, classe](../../mfc/reference/cwinapp-class.md)
