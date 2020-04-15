---
title: Classe CDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: 3376b8febe8ae4586ce649f3f83386875acb678f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375511"
---
# <a name="cdoctemplate-class"></a>Classe CDocTemplate

Classe de base abstraite qui définit les fonctionnalités de base des modèles de document.

## <a name="syntax"></a>Syntaxe

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Construit un objet `CDocTemplate`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocTemplate::AddDocument](#adddocument)|Ajoute un document à un modèle.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Ferme tous les documents associés à ce modèle.|
|[CDocTemplate::CréerNewDocument](#createnewdocument)|Crée un nouveau document.|
|[CDocTemplate::CréerNewFrame](#createnewframe)|Crée une nouvelle fenêtre de cadre contenant un document et une vue.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Crée une fenêtre de cadre compatible OLE.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Crée un cadre pour enfant utilisé pour Rich Preview.|
|[CDocTemplate::GetDocString](#getdocstring)|Récupère une chaîne associée au type de document.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Récupère la position du premier document associé à ce modèle.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Récupère un document et la position du prochain.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Initialise la fenêtre de cadre, et le rend possible.|
|[CDocTemplate::LoadTemplate](#loadtemplate)|Charge les ressources pour `CDocTemplate` une classe donnée ou dérivée.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Détermine le degré de confiance dans la correspondance entre un type de document et ce modèle.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Ouvre un fichier spécifié par un nom de chemin.|
|[CDocTemplate::RemoveDocument](#removedocument)|Supprime un document d’un modèle.|
|[CDocTemplate::SaveAllModified](#saveallmodified)|Enregistre tous les documents associés à ce modèle qui ont été modifiés.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Détermine les ressources pour les contenants OLE lors de l’édition d’un article OLE sur place.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Affiche le titre par défaut dans la barre de titre de la fenêtre de document.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Configurations hors gestionnaire de prévisualisation de processus.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Détermine les ressources et les classes lorsque le document serveur est intégré ou modifié sur place.|

## <a name="remarks"></a>Notes

Vous créez habituellement un ou plusieurs modèles de documents `InitInstance` dans la mise en œuvre de la fonction de votre application. Un modèle de document définit les relations entre trois types de classes :

- Une classe de documents, `CDocument`dont vous dérivez .

- Une classe de vue, qui affiche les données de la classe de documents énumérés ci-dessus. Vous pouvez tirer `CView`cette `CScrollView` `CFormView`classe `CEditView`de , , , ou . (Vous pouvez `CEditView` également utiliser directement.)

- Un cours de fenêtre de cadre, qui contient la vue. Pour une seule application d’interface documentaire (SDI), vous dérivez cette classe de `CFrameWnd`. Pour une application d’interface documentaire multiple (MDI), vous dérivez cette classe de `CMDIChildWnd`. Si vous n’avez pas besoin de personnaliser le comportement `CFrameWnd` `CMDIChildWnd` de la fenêtre du cadre, vous pouvez utiliser ou directement sans dérivant votre propre classe.

Votre application a un modèle de document pour chaque type de document qu’elle prend en charge. Par exemple, si votre application prend en charge à la fois les feuilles de calcul et les documents texte, l’application comporte deux modèles de documents. Chaque modèle de document est responsable de la création et de la gestion de tous les documents de son type.

Le modèle de document `CRuntimeClass` stocke des indications sur les objets pour le document, la vue et les classes de fenêtre de cadre. Ces `CRuntimeClass` objets sont spécifiés lors de la construction d’un modèle de document.

Le modèle de document contient l’ID des ressources utilisées avec le type de document (comme le menu, l’icône ou les ressources de table d’accélérateur). Le modèle de document comporte également des chaînes contenant des informations supplémentaires sur son type de document. Il s’agit notamment du nom du type de document (par exemple, "Worksheet") et de l’extension du fichier (par exemple, ".xls"). En option, il peut contenir d’autres chaînes utilisées par l’interface utilisateur de l’application, le gestionnaire de fichiers Windows et le support Object Linking and Embedding (OLE).

Si votre application est un conteneur et/ou un serveur OLE, le modèle de document définit également l’ID du menu utilisé lors de l’activation sur place. Si votre application est un serveur OLE, le modèle de document définit l’ID de la barre d’outils et le menu utilisé lors de l’activation sur place. Vous spécifiez ces `SetContainerInfo` `SetServerInfo`ressources OLE supplémentaires en appelant et .

Parce `CDocTemplate` que c’est une classe abstraite, vous ne pouvez pas utiliser la classe directement. Une application typique utilise `CDocTemplate`l’une des deux classes dérivées fournies par la Bibliothèque de classe Microsoft Foundation: `CSingleDocTemplate`, qui met en œuvre SDI, et `CMultiDocTemplate`, qui met en œuvre MDI. Consultez ces classes pour plus d’informations sur l’utilisation de modèles de documents.

Si votre application nécessite un paradigme d’interface utilisateur qui est fondamentalement différent `CDocTemplate`de SDI ou MDI, vous pouvez tirer votre propre classe de .

Pour plus `CDocTemplate`d’informations sur , voir [Modèles de documents et le processus de création de documents/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate::AddDocument

Utilisez cette fonction pour ajouter un document à un modèle.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Un pointeur sur le document à ajouter.

### <a name="remarks"></a>Notes

Les classes dérivées [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) et [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) remplacent cette fonction. Si vous dérivez votre propre `CDocTemplate`classe de modèle de document, votre classe dérivée doit remplacer cette fonction.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate::CDocTemplate

Construit un objet `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource (en)*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Cela peut inclure le menu, l’icône, la table d’accélérateur, et les ressources de chaîne.

La ressource de chaîne se compose d’un plus grand 7 sous-cordes séparés par le caractère 'n' (le caractère 'n' est nécessaire en tant que support de lieu si un sous-réseau n’est pas inclus; cependant, les caractères de fuite 'n' ne sont pas nécessaires); ces sous-cordes décrivent le type de document. Pour plus d’informations sur les sous-cordes, voir [GetDocString](#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Notez que la chaîne commence par un caractère 'n'; c’est parce que le premier sous-corde n’est pas utilisé pour les applications MDI et n’est donc pas inclus. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de cordes; la chaîne entière apparaît comme une seule entrée dans l’éditeur de cordes, pas comme sept entrées distinctes.

*classe pDoc*<br/>
Indique l’objet `CRuntimeClass` de la classe de documents. Cette classe `CDocument`est une classe dérivée que vous définissez pour représenter vos documents.

*pFrameClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de fenêtre de cadre. Cette classe peut `CFrameWnd`être une classe dérivée, ou elle peut être `CFrameWnd` elle-même si vous voulez un comportement par défaut pour votre fenêtre cadre principale.

*pViewClass (en)*<br/>
Points à `CRuntimeClass` l’objet de la classe de vue. Cette classe `CView`est une classe dérivée que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Utilisez cette fonction de `CDocTemplate` membre pour construire un objet. Répartir dynamiquement `CDocTemplate` un objet et le transmettre à [CWinApp ::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) de la `InitInstance` fonction membre de votre classe d’application.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments

Appelez cette fonction de membre pour fermer tous les documents ouverts.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Paramètres

*bEndSession*<br/>
Non utilisé.

### <a name="remarks"></a>Notes

Cette fonction de membre est généralement utilisée dans le cadre de la commande de sortie de fichier. La mise en œuvre par défaut de cette fonction appelle la fonction membre [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) pour supprimer les données du document, puis ferme les fenêtres de cadre pour toutes les vues jointes au document.

Remplacez cette fonction si vous souhaitez obliger l’utilisateur à effectuer un traitement de nettoyage spécial avant que le document ne soit fermé. Par exemple, si le document représente un enregistrement dans une base de données, vous pouvez remplacer cette fonction pour fermer la base de données.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate::CréerNewDocument

Appelez cette fonction de membre pour créer un nouveau document du type associé à ce modèle de document.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le document nouvellement créé, ou NULL si une erreur se produit.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate::CréerNewFrame

Crée une nouvelle fenêtre de cadre contenant un document et une vue.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Le document auquel la nouvelle fenêtre de cadre doit se référer. Sa valeur peut être NULL.

*pOther*<br/>
La fenêtre de cadre sur laquelle la nouvelle fenêtre de cadre doit être basée. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la fenêtre de cadre nouvellement créée, ou NULL si une erreur se produit.

### <a name="remarks"></a>Notes

`CreateNewFrame`utilise `CRuntimeClass` les objets transmis au constructeur pour créer une nouvelle fenêtre de cadre avec une vue et un document attachés. Si le *paramètre pDoc* est NULL, le cadre produit un message TRACE.

Le *paramètre pOther* est utilisé pour implémenter la nouvelle commande de fenêtre. Il fournit une fenêtre de cadre sur laquelle modéliser la nouvelle fenêtre de cadre. La nouvelle fenêtre de cadre est généralement créée invisible. Appelez cette fonction pour créer des fenêtres de cadre en dehors de la mise en œuvre du cadre standard de File New et File Open.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate::CreateOleFrame

Crée une fenêtre de cadre OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Un pointeur vers la fenêtre parente du cadre.

*pDoc (en)*<br/>
Un pointeur sur le document auquel la nouvelle fenêtre de cadre OLE doit se référer.

*bCreateView (en anglais)*<br/>
Détermine si une vue est créée avec le cadre.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une fenêtre de cadre en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si *bCreateView* est nul, un cadre vide est créé.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate::GetDocString

Récupère une chaîne associée au type de document.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Paramètres

*rString (en)*<br/>
Une référence `CString` à un objet qui contiendra la chaîne lorsque la fonction revient.

*index*<br/>
Un index du sous-corde récupéré à partir de la chaîne qui décrit le type de document. Ce paramètre peut prendre l'une des valeurs suivantes :

- `CDocTemplate::windowTitle`Nom qui apparaît dans la barre de titre de la fenêtre d’application (par exemple, "Microsoft Excel"). Présent uniquement dans le modèle de document pour les applications SDI.

- `CDocTemplate::docName`Racine pour le nom de document par défaut (par exemple, "Sheet"). Cette racine, plus un numéro, est utilisée pour le nom par défaut d’un nouveau document de ce type chaque fois que l’utilisateur choisit la nouvelle commande dans le menu Fichier (par exemple, "Sheet1" ou "Sheet2"). S’il n’est pas précisé, "Untitled" est utilisé comme par défaut.

- `CDocTemplate::fileNewName`Nom de ce type de document. Si l’application prend en charge plus d’un type de document, cette chaîne est affichée dans la boîte de dialogue Fichier Nouveau (par exemple, " Feuille de travail "). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande Fichier Nouveau.

- `CDocTemplate::filterName`Description du type de document et d’un filtre wildcard correspondant à des documents de ce type. Cette chaîne est affichée dans la liste des fichiers de type drop-down dans la boîte de dialogue De File Open (par exemple, "Worksheets (.xls)"). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande File Open.

- `CDocTemplate::filterExt`Extension pour les documents de ce type (par exemple, ".xls"). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande File Open.

- `CDocTemplate::regFileTypeId`Identifiant pour le type de document à stocker dans la base de données d’enregistrement maintenue par Windows. Cette chaîne est pour une utilisation interne seulement (par exemple, "ExcelWorksheet"). S’il n’est pas spécifié, le type de document ne peut pas être enregistré auprès du gestionnaire de fichiers Windows.

- `CDocTemplate::regFileTypeName`Nom du type de document à stocker dans la base de données d’enregistrement. Cette chaîne peut être affichée dans des boîtes de dialogue d’applications qui accèdent à la base de données d’enregistrement (par exemple, "Microsoft Excel Worksheet").

### <a name="return-value"></a>Valeur de retour

Nonzero si le sous-corde spécifié a été trouvé; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer un sous-cordon spécifique décrivant le type de document. La chaîne contenant ces sous-cordes est stockée dans le modèle de document et est dérivée d’une chaîne dans le fichier de ressources pour l’application. Le cadre appelle cette fonction pour obtenir les chaînes dont elle a besoin pour l’interface utilisateur de l’application. Si vous avez spécifié une extension de nom de fichier pour les documents de votre application, le cadre appelle également cette fonction lors de l’ajout d’une entrée à la base de données d’enregistrement Windows; cela permet d’ouvrir des documents à partir du gestionnaire de fichiers Windows.

Appelez cette fonction seulement si vous retirez `CDocTemplate`votre propre classe de .

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition

Récupère la position du premier document associé à ce modèle.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour itérer à travers la liste des documents associés à ce modèle de document; ou NULL si la liste est vide.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour obtenir la position du premier document dans la liste des documents associés à ce modèle. Utilisez la valeur POSITION comme argument à [CDocTemplate::GetNextDoc](#getnextdoc) pour itérer à travers la liste des documents associés au modèle.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) et [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) l’emportent tous les deux sur cette fonction virtuelle pure. Toute classe que `CDocTemplate` vous dérivez doit également remplacer cette fonction.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate::GetNextDoc

Récupère l’élément de liste identifié par *rPos*, puis définit *rPos* à la valeur POSITION de la prochaine entrée dans la liste.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le prochain document dans la liste des documents associés à ce modèle.

### <a name="parameters"></a>Paramètres

*rPos (en)*<br/>
Une référence à une valeur POSITION retournée par un `GetNextDoc`appel précédent à [GetFirstDocPosition](#getfirstdocposition) ou .

### <a name="remarks"></a>Notes

Si l’élément récupéré est le dernier de la liste, alors la nouvelle valeur de *rPos* est définie à NULL.

Vous pouvez `GetNextDoc` utiliser dans une boucle d’itération vers l’avant si vous établissez la position initiale avec un appel à [GetFirstDocPosition](#getfirstdocposition).

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle est invalide, la version Debug de la Microsoft Foundation Class Library affirme.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame

Initialise la fenêtre de cadre, et le rend possible.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Paramètres

*pFrame (en)*<br/>
La fenêtre de cadre qui a besoin de la mise à jour initiale.

*pDoc (en)*<br/>
Le document auquel le cadre est associé. Sa valeur peut être NULL.

*bMakeVisible*<br/>
Indique si le cadre doit devenir visible et actif.

### <a name="remarks"></a>Notes

Appelez `IntitialUpdateFrame` après avoir créé `CreateNewFrame`un nouveau cadre avec . L’appel de cette fonction provoque les `OnInitialUpdate` vues dans cette fenêtre de cadre pour recevoir leurs appels. En outre, s’il n’y avait pas auparavant une vue active, la vue principale de la fenêtre de cadre est rendue active ; la vue principale est une vue avec une pièce d’identité pour enfants de AFX_IDW_PANE_FIRST. Enfin, la fenêtre de cadre est rendue visible si *bMakeVisible* n’est pas zéro. Si *bMakeVisible* est nul, l’accent actuel et l’état visible de la fenêtre du cadre resteront inchangés.

Il n’est pas nécessaire d’appeler cette fonction lors de l’utilisation de la mise en œuvre du cadre de File New et File Open.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate::LoadTemplate

Charge les ressources pour `CDocTemplate` une classe donnée ou dérivée.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le `CDocTemplate` cadre pour charger les ressources pour une classe donnée ou dérivée. Normalement, il est appelé pendant la construction, sauf lorsque le modèle est construit à l’échelle mondiale. Dans ce cas, `LoadTemplate` l’appel est retardé jusqu’à ce que [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) est appelé.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate::MatchDocType

Détermine le degré de confiance dans la correspondance entre un type de document et ce modèle.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
Nom du fichier dont le type doit être déterminé.

*rpDocMatch*<br/>
Pointeur vers un document qui est attribué le document correspondant, si le fichier spécifié par *lpszPathName* est déjà ouvert.

### <a name="return-value"></a>Valeur de retour

Une valeur **Confidence** de l’énumération de confiance, qui est définie comme suit :

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer le type de modèle de document à utiliser pour ouvrir un fichier. Si votre application prend en charge plusieurs types de fichiers, par exemple, vous pouvez utiliser cette `MatchDocType` fonction pour déterminer lequel des modèles de documents disponibles est approprié pour un fichier donné en appelant pour chaque modèle à son tour, et en choisissant un modèle en fonction de la valeur de confiance retournée.

Si le fichier spécifié par *lpszPathName* est `CDocTemplate::yesAlreadyOpen` déjà ouvert, `CDocument` cette fonction renvoie et copie l’objet du fichier dans l’objet à *rpDocMatch*.

Si le fichier n’est pas ouvert mais *que l’extension dans lpszPathName* correspond à l’extension spécifiée `CDocTemplate::filterExt`par , cette fonction renvoie `CDocTemplate::yesAttemptNative` et définit *rpDocMatch* à NULL. Pour plus `CDocTemplate::filterExt`d’informations sur , voir [CDocTemplate::GetDocString](#getdocstring).

Si aucun des deux cas `CDocTemplate::yesAttemptForeign`n’est vrai, la fonction revient .

La mise en `CDocTemplate::maybeAttemptForeign` œuvre par défaut ne revient pas ou `CDocTemplate::maybeAttemptNative`. Remplacer cette fonction pour implémenter une logique de type correspondant **Confidence** appropriée à votre application, peut-être en utilisant ces deux valeurs de l’énumération de confiance.

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile

Ouvre un fichier spécifié par un chemin.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
[dans] Pointeur sur le chemin du fichier qui contient le document à ouvrir.

*bAddToMRU (en anglais seulement)*<br/>
[dans] TRUE indique que le document est l’un des fichiers les plus récents; FALSE indique que le document n’est pas l’un des fichiers les plus récents.

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le document dont le fichier est nommé par *lpszPathName*; NULL si échoué.

### <a name="remarks"></a>Notes

Ouvre le fichier dont le chemin est spécifié par *lpszPathName*. Si *lpszPathName* est NULL, un nouveau fichier qui contient un document du type associé à ce modèle est créé.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate::RemoveDocument

Supprime le document pointé du *pDoc* dans la liste des documents associés à ce modèle.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pDoc (en)*<br/>
Pointeur sur le document à supprimer.

### <a name="remarks"></a>Notes

Les classes `CMultiDocTemplate` `CSingleDocTemplate` dérivées et l’emportent sur cette fonction. Si vous dérivez votre propre `CDocTemplate`classe de modèle de document, votre classe dérivée doit remplacer cette fonction.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate::SaveAllModified

Enregistre tous les documents qui ont été modifiés.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valeur de retour

Non-zéro en cas de succès; sinon 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo

Détermine les ressources pour les contenants OLE lors de l’édition d’un article OLE sur place.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Paramètres

*nIDOleInPlaceContainer (en anglais)*<br/>
L’ID des ressources utilisées lors de l’activation d’un objet intégré.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir les ressources à utiliser lorsqu’un objet OLE est activé. Ces ressources peuvent inclure des menus et des tables d’accélérateur. Cette fonction est généralement appelée dans le [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) fonction de votre application.

Le menu associé à *nIDOleInPlaceContainer* contient des séparateurs qui permettent au menu de l’élément activé en place de fusionner avec le menu de l’application de conteneurs. Pour plus d’informations sur la fusion des menus des serveurs et des conteneurs, consultez l’article [Menus et Ressources (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle

Appelez cette fonction pour charger le titre par défaut du document et l’afficher dans la barre de titre du document.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Paramètres

*pDocument*<br/>
Pointeur vers le document dont le titre doit être défini.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le `CDocTemplate::docName` titre par défaut, voir la description de dans [CDocTemplate::GetDocString](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate::SetServerInfo

Détermine les ressources et les classes lorsque le document serveur est intégré ou modifié sur place.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDOleEmbedding (en anglais)*<br/>
L’ID des ressources utilisées lorsqu’un objet intégré est ouvert dans une fenêtre séparée.

*nIDOleInPlaceServer (en anglais)*<br/>
L’ID des ressources utilisées lorsqu’un objet intégré est activé sur place.

*pOleFrameClass (en anglais)*<br/>
Pointeur vers une structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) contenant des informations de classe pour l’objet de fenêtre de cadre créé lors de l’activation sur place.

*pOleViewClass (en anglais)*<br/>
Pointeur `CRuntimeClass` vers une structure contenant des informations de classe pour l’objet de vue créé lors de l’activation sur place.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour identifier les ressources qui seront utilisées par l’application serveur lorsque l’utilisateur demande l’activation d’un objet intégré. Ces ressources se composent de menus et de tables d’accélérateur. Cette fonction est généralement `InitInstance` appelée dans le de votre application.

Le menu associé à *nIDOleInPlaceServer* contient des séparateurs qui permettent au menu serveur de fusionner avec le menu du conteneur. Pour plus d’informations sur la fusion des menus des serveurs et des conteneurs, consultez l’article [Menus et Ressources (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame

Crée un cadre pour enfant utilisé pour Rich Preview.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Un pointeur à une fenêtre parente (habituellement fournie par la Coquille).

*pDoc (en)*<br/>
Un pointeur d’un objet de document, dont le contenu sera prévisualisé.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFrameWnd` valide à un objet, ou NULL si la création échoue.

### <a name="remarks"></a>Notes

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo

Définit le gestionnaire de prévisualisation hors processus.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDPréviewFrame (en)*<br/>
Spécifie une pièce d’identité de ressource du cadre de prévisualisation.

*pPreviewFrameClass (en)*<br/>
Spécifie un pointeur d’une structure d’information de classe runtime du cadre de prévisualisation.

*classe pPreviewView*<br/>
Spécifie un pointeur d’une structure d’information de classe runtime de la vue d’aperçu.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate, classe](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate, classe](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView, classe](../../mfc/reference/ceditview-class.md)<br/>
[Classe CFormView](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
