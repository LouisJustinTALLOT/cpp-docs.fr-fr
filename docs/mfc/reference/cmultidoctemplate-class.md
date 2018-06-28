---
title: Classe de CMultiDocTemplate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c09234cbf41201df14aec4993174e6313c6a7d1
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040832"
---
# <a name="cmultidoctemplate-class"></a>Classe de CMultiDocTemplate
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
 Une application MDI utilise la fenêtre frame principale comme un espace de travail dans lequel l’utilisateur peut ouvrir des fenêtres frame de document zéro ou plusieurs, chacun d’eux affiche un document. Pour obtenir une description plus détaillée de l’interface MDI, consultez *indications de l’Interface Windows pour la conception de logiciels*.  
  
 Un modèle de document définit les relations entre les trois types de classes :  
  
-   Une classe de document, vous dérivez de [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Une classe d’affichage, qui affiche des données à partir de la classe de document répertoriée ci-dessus. Vous pouvez dériver de cette classe à partir de [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, ou `CEditView`. (Vous pouvez également utiliser `CEditView` directement.)  
  
-   Une classe de fenêtre frame, qui contient la vue. Pour un modèle de document MDI, vous pouvez dériver de cette classe à partir de `CMDIChildWnd`, ou, si vous n’avez pas besoin de personnaliser le comportement des fenêtres de frame de document, vous pouvez utiliser [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directement sans dériver votre propre classe.  
  
 Une application MDI peut prendre en charge plusieurs types de document et les documents de types différents peuvent être ouverts en même temps. Votre application dispose d’un modèle de document pour chaque type de document pris en charge. Par exemple, si votre application MDI prend en charge les feuilles de calcul et de documents texte, l’application possède deux `CMultiDocTemplate` objets.  
  
 L’application utilise les modèles de document lorsque l’utilisateur crée un nouveau document. Si l’application prend en charge plusieurs types de document, le framework Obtient les noms des types de document pris en charge dans les modèles de document et les affiche dans une liste dans la boîte de dialogue Nouveau fichier. Une fois que l’utilisateur a sélectionné un type de document, l’application crée un objet de classe de document, un objet fenêtre frame et un objet de vue et attache les uns aux autres.  
  
 Vous n’avez pas besoin d’appeler des fonctions de n’importe quel membre `CMultiDocTemplate` sauf le constructeur. Les descripteurs de framework `CMultiDocTemplate` objets en interne.  
  
 Pour plus d’informations sur `CMultiDocTemplate`, consultez [modèles de Document et le processus de création de Document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate  
 Construit un objet `CMultiDocTemplate`.  
  
```  
CMultiDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDResource*  
 Spécifie l’ID des ressources utilisées avec le type de document. Cela peut inclure le menu, icône, table d’accélérateurs et ressources de type chaîne.  
  
 La ressource de chaîne se compose de sous-chaînes jusqu'à sept séparés par le caractère « \n » (le caractère « \n » est nécessaire comme espace réservé, si une sous-chaîne n’est pas incluse ; Toutefois, les caractères de fin '\n' ne sont pas nécessaires) ; Ces sous-chaînes décrivent le type de document. Pour plus d’informations sur les sous-chaînes, consultez [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Exemple :  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Notez que la chaîne commence par un caractère '\n' ; Il s’agit, car la première sous-chaîne n’est pas utilisée pour les applications MDI et par conséquent, n’est pas incluse. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de chaînes ; la chaîne entière apparaît comme une seule entrée dans l’éditeur de chaînes, pas comme des entrées séparées sept.  
  
 Pour plus d’informations sur ces types de ressources, consultez [éditeurs de ressources](../../windows/resource-editors.md).  
  
 *pDocClass*  
 Pointe vers le `CRuntimeClass` objet de la classe de document. Cette classe est un `CDocument`-dérivée la classe que vous définissez pour représenter vos documents.  
  
 *pFrameClass*  
 Pointe vers le `CRuntimeClass` objet de la classe de fenêtre frame. Cette classe peut être un `CMDIChildWnd`-classe dérivée, ou il peut être `CMDIChildWnd` elle-même si vous souhaitez le comportement par défaut pour vos fenêtres frame de document.  
  
 *pViewClass*  
 Pointe vers le `CRuntimeClass` objet de la classe d’affichage. Cette classe est un `CView`-dérivée la classe que vous définissez pour afficher vos documents.  
  
### <a name="remarks"></a>Notes  
 Allouer dynamiquement un `CMultiDocTemplate` objet pour chaque type de document que votre application prend en charge et passer à `CWinApp::AddDocTemplate` à partir de la `InitInstance` fonction membre de classe de votre application.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Voici un autre exemple.  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [Classe CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp, classe](../../mfc/reference/cwinapp-class.md)
