---
title: CDocTemplate (classe)
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
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855490"
---
# <a name="cdoctemplate-class"></a>CDocTemplate (classe)

Classe de base abstraite qui définit les fonctionnalités de base des modèles de document.

## <a name="syntax"></a>Syntaxe

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs prot&#233;g&#233;s

|Name|Description|
|----------|-----------------|
|[CDocTemplate :: CDocTemplate](#cdoctemplate)|Construit un objet `CDocTemplate`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDocTemplate :: AddDocument](#adddocument)|Ajoute un document à un modèle.|
|[CDocTemplate :: CloseAllDocuments](#closealldocuments)|Ferme tous les documents associés à ce modèle.|
|[CDocTemplate :: CreateNewDocument](#createnewdocument)|Crée un nouveau document.|
|[CDocTemplate :: CreateNewFrame](#createnewframe)|Crée une nouvelle fenêtre frame contenant un document et une vue.|
|[CDocTemplate :: CreateOleFrame](#createoleframe)|Crée une fenêtre frame OLE.|
|[CDocTemplate :: CreatePreviewFrame](#createpreviewframe)|Crée un Frame enfant utilisé pour la version préliminaire complète.|
|[CDocTemplate :: GetDocString](#getdocstring)|Récupère une chaîne associée au type de document.|
|[CDocTemplate :: GetFirstDocPosition](#getfirstdocposition)|Récupère la position du premier document associé à ce modèle.|
|[CDocTemplate :: GetNextDoc](#getnextdoc)|Récupère un document et la position de l’autre.|
|[CDocTemplate :: InitialUpdateFrame](#initialupdateframe)|Initialise la fenêtre frame et, éventuellement, la rend visible.|
|[CDocTemplate :: LoadTemplate](#loadtemplate)|Charge les ressources pour une `CDocTemplate` ou une classe dérivée donnée.|
|[CDocTemplate :: MatchDocType](#matchdoctype)|Détermine le degré de confiance de la correspondance entre un type de document et ce modèle.|
|[CDocTemplate :: OpenDocumentFile](#opendocumentfile)|Ouvre un fichier spécifié par un nom de chemin d’accès.|
|[CDocTemplate :: RemoveDocument](#removedocument)|Supprime un document d’un modèle.|
|[CDocTemplate :: SaveAllModified](#saveallmodified)|Enregistre tous les documents associés à ce modèle qui ont été modifiés.|
|[CDocTemplate :: SetContainerInfo](#setcontainerinfo)|Détermine les ressources pour les conteneurs OLE lors de la modification d’un élément OLE sur place.|
|[CDocTemplate :: SetDefaultTitle](#setdefaulttitle)|Affiche le titre par défaut dans la barre de titre de la fenêtre de document.|
|[CDocTemplate :: SetPreviewInfo](#setpreviewinfo)|Configuration du gestionnaire d’aperçus hors processus.|
|[CDocTemplate :: SetServerInfo](#setserverinfo)|Détermine les ressources et les classes lorsque le document serveur est incorporé ou modifié sur place.|

## <a name="remarks"></a>Notes

En général, vous créez un ou plusieurs modèles de document dans l’implémentation de la fonction `InitInstance` de votre application. Un modèle de document définit les relations entre trois types de classes :

- Classe de document, que vous dérivez de `CDocument`.

- Une classe d’affichage, qui affiche les données de la classe de document indiquée ci-dessus. Vous pouvez dériver cette classe de `CView`, `CScrollView`, `CFormView`ou `CEditView`. (Vous pouvez également utiliser `CEditView` directement.)

- Classe de fenêtre frame, qui contient la vue. Pour une application SDI (single document interface), vous dérivez cette classe de `CFrameWnd`. Pour une application d’interface multidocument (MDI, multiple document interface), vous dérivez cette classe de `CMDIChildWnd`. Si vous n’avez pas besoin de personnaliser le comportement de la fenêtre frame, vous pouvez utiliser `CFrameWnd` ou `CMDIChildWnd` directement sans dériver votre propre classe.

Votre application possède un modèle de document pour chaque type de document qu’elle prend en charge. Par exemple, si votre application prend en charge les feuilles de calcul et les documents texte, l’application dispose de deux objets de modèle de document. Chaque modèle de document est responsable de la création et de la gestion de tous les documents de son type.

Le modèle de document stocke des pointeurs vers les objets `CRuntimeClass` pour les classes document, vue et fenêtre frame. Ces objets `CRuntimeClass` sont spécifiés lors de la construction d’un modèle de document.

Le modèle de document contient l’ID des ressources utilisées avec le type de document (par exemple, menu, icône ou ressources de table d’accélérateurs). Le modèle de document comporte également des chaînes contenant des informations supplémentaires sur son type de document. Celles-ci incluent le nom du type de document (par exemple, « feuille de calcul ») et l’extension de fichier (par exemple, « . xls »). Il peut éventuellement contenir d’autres chaînes utilisées par l’interface utilisateur de l’application, le gestionnaire de fichiers Windows et la prise en charge de la liaison et de l’incorporation d’objets (OLE).

Si votre application est un conteneur OLE et/ou un serveur, le modèle de document définit également l’ID du menu utilisé pendant l’activation sur place. Si votre application est un serveur OLE, le modèle de document définit l’ID de la barre d’outils et du menu utilisés pendant l’activation sur place. Vous spécifiez ces ressources OLE supplémentaires en appelant `SetContainerInfo` et `SetServerInfo`.

Étant donné que `CDocTemplate` est une classe abstraite, vous ne pouvez pas utiliser la classe directement. Une application classique utilise l’une des deux classes dérivées de `CDocTemplate`fournies par le bibliothèque MFC (Microsoft Foundation Class) : `CSingleDocTemplate`, qui implémente SDI et `CMultiDocTemplate`, qui implémente MDI. Pour plus d’informations sur l’utilisation des modèles de document, consultez ces classes.

Si votre application nécessite un paradigme d’interface utilisateur fondamentalement différent de SDI ou MDI, vous pouvez dériver votre propre classe de `CDocTemplate`.

Pour plus d’informations sur les `CDocTemplate`, consultez [modèles de document et processus de création de document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="adddocument"></a>CDocTemplate :: AddDocument

Utilisez cette fonction pour ajouter un document à un modèle.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Pointeur vers le document à ajouter.

### <a name="remarks"></a>Notes

Les classes dérivées [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) et [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) substituent cette fonction. Si vous dérivez votre propre classe de modèle de document à partir de `CDocTemplate`, votre classe dérivée doit substituer cette fonction.

##  <a name="cdoctemplate"></a>CDocTemplate :: CDocTemplate

Construit un objet `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Paramètres

*nIDResource*<br/>
Spécifie l’ID des ressources utilisées avec le type de document. Il peut s’agir d’un menu, d’une icône, d’une table d’accélérateurs et de ressources de type chaîne.

La ressource de type chaîne se compose de sept sous-chaînes séparées par le caractère « \n » (le caractère « \n » est requis comme espace réservé si une sous-chaîne n’est pas incluse ; Toutefois, les caractères « \n » de fin ne sont pas nécessaires); ces sous-chaînes décrivent le type de document. Pour plus d’informations sur les sous-chaînes, consultez [GetDocString](#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Par exemple :

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Notez que la chaîne commence par un caractère « \n »; en effet, la première sous-chaîne n’est pas utilisée pour les applications MDI et n’est donc pas incluse. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de chaînes. la chaîne entière apparaît sous la forme d’une entrée unique dans l’éditeur de chaînes, et non pas sous la forme de sept entrées distinctes.

*pDocClass*<br/>
Pointe vers l’objet `CRuntimeClass` de la classe de document. Cette classe est une classe dérivée de `CDocument`que vous définissez pour représenter vos documents.

*pFrameClass*<br/>
Pointe vers l’objet `CRuntimeClass` de la classe de fenêtre frame. Cette classe peut être une classe dérivée de `CFrameWnd`, ou elle peut être `CFrameWnd` elle-même si vous souhaitez utiliser le comportement par défaut pour votre fenêtre frame principale.

*pViewClass*<br/>
Pointe vers l’objet `CRuntimeClass` de la classe de vue. Cette classe est une classe dérivée de `CView`que vous définissez pour afficher vos documents.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre pour construire un objet `CDocTemplate`. Allouez dynamiquement un objet `CDocTemplate` et transmettez-le à [CWinApp :: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) à partir de la fonction membre `InitInstance` de votre classe d’application.

##  <a name="closealldocuments"></a>CDocTemplate :: CloseAllDocuments

Appelez cette fonction membre pour fermer tous les documents ouverts.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Paramètres

*bEndSession*<br/>
Non utilisé.

### <a name="remarks"></a>Notes

Cette fonction membre est généralement utilisée dans le cadre de la commande file Exit. L’implémentation par défaut de cette fonction appelle la fonction membre [CDocument ::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) pour supprimer les données du document, puis ferme les fenêtres Frame pour tous les affichages attachés au document.

Remplacez cette fonction si vous souhaitez obliger l’utilisateur à effectuer un traitement de nettoyage spécial avant la fermeture du document. Par exemple, si le document représente un enregistrement dans une base de données, vous pouvez remplacer cette fonction pour fermer la base de données.

##  <a name="createnewdocument"></a>CDocTemplate :: CreateNewDocument

Appelez cette fonction membre pour créer un document du type associé à ce modèle de document.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le document qui vient d’être créé, ou NULL si une erreur se produit.

##  <a name="createnewframe"></a>CDocTemplate :: CreateNewFrame

Crée une nouvelle fenêtre frame contenant un document et une vue.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Document auquel la nouvelle fenêtre frame doit faire référence. Sa valeur peut être NULL.

*pOther*<br/>
Fenêtre frame sur laquelle la nouvelle fenêtre frame doit reposer. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre frame nouvellement créée, ou NULL si une erreur se produit.

### <a name="remarks"></a>Notes

`CreateNewFrame` utilise les objets `CRuntimeClass` passés au constructeur pour créer une nouvelle fenêtre frame avec une vue et un document attachés. Si le paramètre *pdoc* est null, le Framework génère un message de trace.

Le paramètre *pOther* est utilisé pour implémenter la commande New Window. Il fournit une fenêtre frame sur laquelle modéliser la nouvelle fenêtre frame. La nouvelle fenêtre frame est généralement créée invisible. Appelez cette fonction pour créer des fenêtres frame en dehors de l’implémentation de l’infrastructure standard du fichier New et du fichier ouvert.

##  <a name="createoleframe"></a>CDocTemplate :: CreateOleFrame

Crée une fenêtre frame OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente du frame.

*pDoc*<br/>
Pointeur vers le document auquel la nouvelle fenêtre frame OLE doit faire référence.

*bCreateView*<br/>
Détermine si une vue est créée avec le frame.

### <a name="return-value"></a>Valeur de retour

Pointeur vers une fenêtre frame en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Si *bCreateView* est égal à zéro, un frame vide est créé.

##  <a name="getdocstring"></a>CDocTemplate :: GetDocString

Récupère une chaîne associée au type de document.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Référence à un objet `CString` qui contiendra la chaîne quand la fonction est retournée.

*index*<br/>
Index de la sous-chaîne Récupérée à partir de la chaîne qui décrit le type de document. Ce paramètre peut prendre l'une des valeurs suivantes :

- `CDocTemplate::windowTitle` nom qui s’affiche dans la barre de titre de la fenêtre de l’application (par exemple, « Microsoft Excel »). Présent uniquement dans le modèle de document pour les applications SDI.

- `CDocTemplate::docName` racine pour le nom de document par défaut (par exemple, « Sheet »). Cette racine, plus un nombre, est utilisée pour le nom par défaut d’un nouveau document de ce type chaque fois que l’utilisateur choisit la commande nouveau dans le menu fichier (par exemple, « Feuil1 » ou « Feuil2 »). S’il n’est pas spécifié, « sans titre » est utilisé comme valeur par défaut.

- `CDocTemplate::fileNewName` nom de ce type de document. Si l’application prend en charge plusieurs types de document, cette chaîne est affichée dans la boîte de dialogue fichier nouveau (par exemple, « feuille de calcul »). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande fichier nouveau.

- `CDocTemplate::filterName` Description du type de document et un filtre de caractères génériques correspondant aux documents de ce type. Cette chaîne est affichée dans la liste déroulante liste des types de fichiers de la boîte de dialogue Ouvrir un fichier (par exemple, "feuilles de calcul (*. xls)"). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande fichier ouvrir.

- Extension de `CDocTemplate::filterExt` pour les documents de ce type (par exemple, « . xls »). S’il n’est pas spécifié, le type de document est inaccessible à l’aide de la commande fichier ouvrir.

- `CDocTemplate::regFileTypeId` identificateur du type de document à stocker dans la base de données d’inscription gérée par Windows. Cette chaîne est destinée à un usage interne uniquement (par exemple, « ExcelWorksheet »). S’il n’est pas spécifié, le type de document ne peut pas être inscrit auprès du gestionnaire de fichiers Windows.

- `CDocTemplate::regFileTypeName` nom du type de document à stocker dans la base de données d’inscription. Cette chaîne peut être affichée dans les boîtes de dialogue des applications qui accèdent à la base de données d’inscription (par exemple, « feuille de calcul Microsoft Excel »).

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la sous-chaîne spécifiée a été trouvée ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer une sous-chaîne spécifique décrivant le type de document. La chaîne contenant ces sous-chaînes est stockée dans le modèle de document et est dérivée d’une chaîne dans le fichier de ressources de l’application. L’infrastructure appelle cette fonction pour obtenir les chaînes dont elle a besoin pour l’interface utilisateur de l’application. Si vous avez spécifié une extension de nom de fichier pour les documents de votre application, le Framework appelle également cette fonction lors de l’ajout d’une entrée à la base de données d’inscription de Windows ; Cela permet d’ouvrir des documents à partir du gestionnaire de fichiers Windows.

Appelez cette fonction uniquement si vous dérivez votre propre classe de `CDocTemplate`.

##  <a name="getfirstdocposition"></a>CDocTemplate :: GetFirstDocPosition

Récupère la position du premier document associé à ce modèle.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour itérer au sein de la liste des documents associés à ce modèle de document ; ou NULL si la liste est vide.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la position du premier document dans la liste des documents associés à ce modèle. Utilisez la valeur POSITION comme argument de [CDocTemplate :: GetNextDoc](#getnextdoc) pour itérer au sein de la liste des documents associés au modèle.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) et [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) remplacent tous deux cette fonction virtuelle pure. Toute classe que vous dérivez de `CDocTemplate` doit également remplacer cette fonction.

##  <a name="getnextdoc"></a>CDocTemplate :: GetNextDoc

Récupère l’élément de liste identifié par les *RPO*, puis définit les *RPO* sur la valeur de position de l’entrée suivante dans la liste.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le document suivant dans la liste des documents associés à ce modèle.

### <a name="parameters"></a>Paramètres

*RPO*<br/>
Référence à une valeur de POSITION retournée par un appel précédent à [GetFirstDocPosition](#getfirstdocposition) ou `GetNextDoc`.

### <a name="remarks"></a>Notes

Si l’élément récupéré est le dernier de la liste, la nouvelle valeur de *RPO* est définie sur null.

Vous pouvez utiliser `GetNextDoc` dans une boucle d’itération directe si vous établissez la position initiale avec un appel à [GetFirstDocPosition](#getfirstdocposition).

Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. S’il n’est pas valide, la version de débogage du bibliothèque MFC (Microsoft Foundation Class) Assert.

##  <a name="initialupdateframe"></a>CDocTemplate :: InitialUpdateFrame

Initialise la fenêtre frame et, éventuellement, la rend visible.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Paramètres

*pFrame*<br/>
Fenêtre frame qui requiert la mise à jour initiale.

*pDoc*<br/>
Document auquel le cadre est associé. Sa valeur peut être NULL.

*bMakeVisible*<br/>
Indique si le frame doit devenir visible et actif.

### <a name="remarks"></a>Notes

Appelez `IntitialUpdateFrame` après avoir créé un nouveau Frame avec `CreateNewFrame`. L’appel de cette fonction amène les vues dans cette fenêtre frame à recevoir leurs appels `OnInitialUpdate`. En outre, s’il n’y avait pas précédemment une vue active, la vue principale de la fenêtre frame est rendue active ; la vue principale est une vue avec un ID enfant de AFX_IDW_PANE_FIRST. Enfin, la fenêtre frame est rendue visible si *bMakeVisible* est différent de zéro. Si *bMakeVisible* est égal à zéro, le focus actuel et l’état visible de la fenêtre frame restent inchangés.

Il n’est pas nécessaire d’appeler cette fonction lors de l’utilisation de l’implémentation du fichier New et du fichier ouvert de l’infrastructure.

##  <a name="loadtemplate"></a>CDocTemplate :: LoadTemplate

Charge les ressources pour une `CDocTemplate` ou une classe dérivée donnée.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour charger les ressources pour une `CDocTemplate` ou une classe dérivée donnée. Normalement, il est appelé pendant la construction, sauf quand le modèle est construit globalement. Dans ce cas, l’appel à `LoadTemplate` est retardé jusqu’à ce que [CWinApp :: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) soit appelé.

##  <a name="matchdoctype"></a>CDocTemplate :: MatchDocType

Détermine le degré de confiance de la correspondance entre un type de document et ce modèle.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Nom du fichier dont le type doit être déterminé.

*rpDocMatch*<br/>
Pointeur vers un document auquel est assigné le document correspondant, si le fichier spécifié par *lpszPathName* est déjà ouvert.

### <a name="return-value"></a>Valeur de retour

Valeur de l’énumération **confidence** , qui est définie comme suit :

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

Utilisez cette fonction pour déterminer le type de modèle de document à utiliser pour l’ouverture d’un fichier. Par exemple, si votre application prend en charge plusieurs types de fichiers, vous pouvez utiliser cette fonction pour déterminer les modèles de document disponibles qui conviennent à un fichier donné en appelant `MatchDocType` pour chaque modèle, et en choisissant un modèle en fonction de la valeur de confiance renvoyée.

Si le fichier spécifié par *lpszPathName* est déjà ouvert, cette fonction retourne `CDocTemplate::yesAlreadyOpen` et copie l’objet `CDocument` du fichier dans l’objet sur *rpDocMatch*.

Si le fichier n’est pas ouvert, mais que l’extension dans *lpszPathName* correspond à l’extension spécifiée par `CDocTemplate::filterExt`, cette fonction retourne `CDocTemplate::yesAttemptNative` et affecte à *rpDocMatch* la valeur null. Pour plus d’informations sur `CDocTemplate::filterExt`, consultez [CDocTemplate :: GetDocString](#getdocstring).

Si aucun de ces cas n’a la valeur true, la fonction retourne `CDocTemplate::yesAttemptForeign`.

L’implémentation par défaut ne retourne pas `CDocTemplate::maybeAttemptForeign` ou `CDocTemplate::maybeAttemptNative`. Substituez cette fonction pour implémenter une logique de correspondance de type appropriée à votre application, en utilisant peut-être ces deux valeurs de l’énumération **confidence** .

##  <a name="opendocumentfile"></a>CDocTemplate :: OpenDocumentFile

Ouvre un fichier spécifié par un chemin d’accès.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
dans Pointeur vers le chemin d’accès du fichier qui contient le document à ouvrir.

*bAddToMRU*<br/>
dans TRUE indique que le document est l’un des fichiers les plus récents ; FALSe indique que le document ne fait pas partie des fichiers les plus récents.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le document dont le nom de fichier est nommé par *lpszPathName*; NULL en cas d’échec.

### <a name="remarks"></a>Notes

Ouvre le fichier dont le chemin d’accès est spécifié par *lpszPathName*. Si *lpszPathName* a la valeur null, un nouveau fichier qui contient un document du type associé à ce modèle est créé.

##  <a name="removedocument"></a>CDocTemplate :: RemoveDocument

Supprime le document pointé par *pdoc* dans la liste des documents associés à ce modèle.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pDoc*<br/>
Pointeur vers le document à supprimer.

### <a name="remarks"></a>Notes

Les classes dérivées `CMultiDocTemplate` et `CSingleDocTemplate` substituent cette fonction. Si vous dérivez votre propre classe de modèle de document à partir de `CDocTemplate`, votre classe dérivée doit substituer cette fonction.

##  <a name="saveallmodified"></a>CDocTemplate :: SaveAllModified

Enregistre tous les documents qui ont été modifiés.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; Sinon, 0.

##  <a name="setcontainerinfo"></a>CDocTemplate :: SetContainerInfo

Détermine les ressources pour les conteneurs OLE lors de la modification d’un élément OLE sur place.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Paramètres

*nIDOleInPlaceContainer*<br/>
ID des ressources utilisées lorsqu’un objet incorporé est activé.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir les ressources à utiliser lorsqu’un objet OLE est activé sur place. Ces ressources peuvent inclure des menus et des tables d’accélérateurs. Cette fonction est généralement appelée dans la fonction [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de votre application.

Le menu associé à *nIDOleInPlaceContainer* contient des séparateurs qui permettent de fusionner le menu de l’élément sur place activé avec le menu de l’application conteneur. Pour plus d’informations sur la fusion des menus du serveur et des conteneurs, consultez les [menus et les ressources de l’article (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>CDocTemplate :: SetDefaultTitle

Appelez cette fonction pour charger le titre par défaut du document et l’afficher dans la barre de titre du document.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Paramètres

*pDocument*<br/>
Pointeur vers le document dont le titre doit être défini.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le titre par défaut, consultez la description de `CDocTemplate::docName` dans [CDocTemplate :: GetDocString](#getdocstring).

##  <a name="setserverinfo"></a>CDocTemplate :: SetServerInfo

Détermine les ressources et les classes lorsque le document serveur est incorporé ou modifié sur place.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDOleEmbedding*<br/>
ID des ressources utilisées lorsqu’un objet incorporé est ouvert dans une fenêtre séparée.

*nIDOleInPlaceServer*<br/>
ID des ressources utilisées lorsqu’un objet incorporé est activé sur place.

*pOleFrameClass*<br/>
Pointeur vers une structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) contenant les informations de classe pour l’objet de fenêtre frame créé lorsque l’activation sur place se produit.

*pOleViewClass*<br/>
Pointeur vers une structure `CRuntimeClass` contenant des informations de classe pour l’objet de vue créé lorsque l’activation sur place se produit.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour identifier les ressources qui seront utilisées par l’application serveur lorsque l’utilisateur demandera l’activation d’un objet incorporé. Ces ressources sont constituées de menus et de tables d’accélérateurs. Cette fonction est généralement appelée dans le `InitInstance` de votre application.

Le menu associé à *nIDOleInPlaceServer* contient des séparateurs qui permettent au menu serveur de fusionner avec le menu du conteneur. Pour plus d’informations sur la fusion des menus du serveur et des conteneurs, consultez les [menus et les ressources de l’article (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>CDocTemplate :: CreatePreviewFrame

Crée un Frame enfant utilisé pour la version préliminaire complète.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers une fenêtre parente (généralement fourni par l’interpréteur de commandes).

*pDoc*<br/>
Pointeur vers un objet document dont le contenu sera affiché en aperçu.

### <a name="return-value"></a>Valeur de retour

Pointeur valide vers un objet `CFrameWnd`, ou NULL en cas d’échec de la création.

### <a name="remarks"></a>Notes

##  <a name="setpreviewinfo"></a>CDocTemplate :: SetPreviewInfo

Configure le gestionnaire d’aperçus hors processus.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Paramètres

*nIDPreviewFrame*<br/>
Spécifie un ID de ressource du frame d’aperçu.

*pPreviewFrameClass*<br/>
Spécifie un pointeur vers une structure d’informations de classe d’exécution du frame d’aperçu.

*pPreviewViewClass*<br/>
Spécifie un pointeur vers une structure d’informations de classe Runtime de la vue aperçu.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate, classe](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate, classe](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CScrollView, classe](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView, classe](../../mfc/reference/ceditview-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
