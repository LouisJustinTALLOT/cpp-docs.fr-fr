---
title: CDocTemplate, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbdb880c7165f314c004a7cbcad44dd3b76fd36
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709837"
---
# <a name="cdoctemplate-class"></a>CDocTemplate (classe)
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
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Crée un nouveau document.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Crée une nouvelle fenêtre frame contenant un document et la vue.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Crée une fenêtre frame prenant en charge OLE.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Crée un frame enfant utilisé pour l’aperçu riche.|  
|[CDocTemplate::GetDocString](#getdocstring)|Récupère une chaîne associée au type de document.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Récupère la position du premier document associé à ce modèle.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Récupère un document et la position de l’exercice suivant.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Initialise la fenêtre frame et éventuellement rend visible.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Charge les ressources pour une donnée `CDocTemplate` ou de la classe dérivée.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Détermine le degré de confiance dans la correspondance entre un type de document et de ce modèle.|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Ouvre un fichier spécifié par un chemin d’accès.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Supprime un document à partir d’un modèle.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Enregistre tous les documents associés à ce modèle et qui ont été modifiés.|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Détermine les ressources pour les conteneurs OLE lors de la modification d’un élément d’OLE sur place.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Affiche le titre par défaut dans la barre de titre de la fenêtre de document.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Gestionnaire d’aperçus de paramétrages en dehors du processus.|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|Détermine les ressources et les classes lorsque le document serveur incorporé ou modifié sur place.|  
  
## <a name="remarks"></a>Notes  
 Vous créez généralement un ou plusieurs modèles de document dans l’implémentation de votre application `InitInstance` (fonction). Un modèle de document définit les relations entre les trois types de classes :  
  
-   Une classe de document, vous dérivez de `CDocument`.  
  
-   Une classe d’affichage, qui affiche des données à partir de la classe de document répertoriée ci-dessus. Vous pouvez dériver de cette classe à partir de `CView`, `CScrollView`, `CFormView`, ou `CEditView`. (Vous pouvez également utiliser `CEditView` directement.)  
  
-   Une classe de fenêtre frame, qui contient la vue. Pour une application SDI (interface) de document unique, vous dérivez cette classe à partir de `CFrameWnd`. Pour une application d’interface (multidocument MDI) document, vous dérivez cette classe à partir de `CMDIChildWnd`. Si vous n’avez pas besoin de personnaliser le comportement de la fenêtre frame, vous pouvez utiliser `CFrameWnd` ou `CMDIChildWnd` directement sans dériver votre propre classe.  
  
 Votre application a un modèle de document pour chaque type de document pris en charge. Par exemple, si votre application prend en charge les feuilles de calcul et de documents texte, l’application a deux objets de modèle de document. Chaque modèle de document est responsable de la création et la gestion de tous les documents de son type.  
  
 Le modèle de document stocke des pointeurs vers les `CRuntimeClass` objets pour le document, vue et classes de fenêtre frame. Ces `CRuntimeClass` objets sont spécifiés lors de la construction d’un modèle de document.  
  
 Le modèle de document contient l’ID des ressources utilisées avec le type de document (par exemple, menu, icône ou de ressources de table d’accélérateurs). Le modèle de document a également les chaînes contenant des informations supplémentaires sur le type de document. Citons notamment le nom du type de document (par exemple, « feuille ») et l’extension de fichier (par exemple, « .xls »). Si vous le souhaitez, il peut contenir d’autres chaînes utilisées par l’interface utilisateur de l’application, le Gestionnaire de fichiers Windows et liaison d’objets et prise en charge l’incorporation (OLE).  
  
 Si votre application est un conteneur OLE et/ou le serveur, le modèle de document définit également l’ID du menu utilisé pendant l’activation sur place. Si votre application est un serveur OLE, le modèle de document définit l’ID de la barre d’outils et le menu utilisé pendant l’activation sur place. Vous spécifiez ces ressources OLE supplémentaires en appelant `SetContainerInfo` et `SetServerInfo`.  
  
 Étant donné que `CDocTemplate` est une classe abstraite, vous ne pouvez pas utiliser directement la classe. Une application classique utilise l’une des deux `CDocTemplate`-dérivées des classes fournies par la bibliothèque Microsoft Foundation Class : `CSingleDocTemplate`, qui implémente le SDI, et `CMultiDocTemplate`, qui implémente MDI. Consultez ces classes pour plus d’informations sur l’utilisation de modèles de document.  
  
 Si votre application nécessite un modèle d’interface utilisateur qui est fondamentalement différent de SDI ou MDI, vous pouvez dériver votre propre classe de `CDocTemplate`.  
  
 Pour plus d’informations sur `CDocTemplate`, consultez [modèles de Document et le processus de création de Document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 Cette fonction permet d’ajouter un document à un modèle.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDoc*  
 Pointeur vers le document à ajouter.  
  
### <a name="remarks"></a>Notes  
 Les classes dérivées [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) et [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) remplacent cette fonction. Si vous dérivez votre propre classe de modèle de document de `CDocTemplate`, votre classe dérivée doit remplacer cette fonction.  
  
##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate  
 Construit un objet `CDocTemplate`.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDResource*  
 Spécifie l’ID des ressources utilisées avec le type de document. Cela peut inclure le menu, icône, table d’accélérateurs et ressources de type chaîne.  
  
 La ressource de chaîne se compose de sous-chaînes jusqu'à sept séparés par le caractère « \n » (le caractère « \n » est nécessaire en tant qu’un espace réservé si une sous-chaîne n’est pas incluse ; Toutefois, les caractères de fin '\n' ne sont pas nécessaires) ; Ces sous-chaînes décrivent le type de document. Pour plus d’informations sur les sous-chaînes, consultez [GetDocString](#getdocstring). Cette ressource de chaîne se trouve dans le fichier de ressources de l’application. Exemple :  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Notez que la chaîne commence par un caractère « \n » ; Il s’agit, car la première sous-chaîne n’est pas utilisée pour les applications MDI et par conséquent, n’est pas incluse. Vous pouvez modifier cette chaîne à l’aide de l’éditeur de chaînes ; la chaîne entière apparaît comme une entrée unique dans l’éditeur de chaîne, pas comme sept entrées distinctes.  
  
 *pDocClass*  
 Pointe vers le `CRuntimeClass` objet de la classe de document. Cette classe est un `CDocument`-dérivée la classe que vous définissez pour représenter vos documents.  
  
 *pFrameClass*  
 Pointe vers le `CRuntimeClass` objet de la classe de fenêtre frame. Cette classe peut être un `CFrameWnd`-classe dérivée, ou il peut être `CFrameWnd` elle-même si vous préférez le comportement par défaut pour votre fenêtre frame principale.  
  
 *pViewClass*  
 Pointe vers le `CRuntimeClass` objet de la classe d’affichage. Cette classe est un `CView`-dérivée la classe que vous définissez pour afficher vos documents.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre pour construire un `CDocTemplate` objet. Allouer dynamiquement un `CDocTemplate` de l’objet et transmettez-le à [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) à partir de la `InitInstance` fonction membre de classe de votre application.  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 Appelez cette fonction membre pour fermer tous les documents ouverts.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEndSession*  
 Non utilisé.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est généralement utilisée en tant que partie de la commande de sortie de fichier. L’implémentation par défaut de cette fonction appelle le [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) fonction membre à supprimer du document données, puis se ferme les fenêtres frame pour toutes les vues attachés au document.  
  
 Remplacez cette fonction si vous souhaitez demander à l’utilisateur d’effectuer des traitements de nettoyage spécial avant la fermeture du document. Par exemple, si le document représente un enregistrement dans une base de données, vous souhaiterez substituer cette fonction pour fermer la base de données.  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 Appelez cette fonction membre pour créer un document de type associé à ce modèle de document.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le document qui vient d’être créé, ou NULL si une erreur se produit.  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 Crée une nouvelle fenêtre frame contenant un document et la vue.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDoc*  
 Le document auquel la nouvel objet fenêtre frame doit faire référence. Peut être NULL.  
  
 *pOther*  
 La fenêtre frame sur lesquels la nouvelle fenêtre de frame doit être basée. Peut être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la fenêtre frame nouvellement créée, ou NULL si une erreur se produit.  
  
### <a name="remarks"></a>Notes  
 `CreateNewFrame` utilise le `CRuntimeClass` objets passés au constructeur pour créer une nouvelle fenêtre frame avec une vue et le document joint. Si le *pDoc* paramètre est NULL, le framework génère un message TRACE.  
  
 Le *pOther* paramètre est utilisé pour implémenter la commande nouvelle fenêtre. Il fournit une fenêtre frame sur lequel modéliser la nouvelle fenêtre frame. La nouvelle fenêtre frame est généralement créée invisible. Appelez cette fonction pour créer des fenêtres frame en dehors de l’implémentation du framework standard du nouveau fichier et ouvrir le fichier.  
  
##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame  
 Crée une fenêtre de frame OLE.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 Pointeur vers la fenêtre du cadre parent.  
  
 *pDoc*  
 Pointeur vers le document à laquelle la nouvelle fenêtre de frame OLE doit faire référence.  
  
 *bCreateView*  
 Détermine si une vue est créée, ainsi que le frame.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une fenêtre frame en cas de réussite ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Si *bCreateView* est égal à zéro, un cadre vide est créé.  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 Récupère une chaîne associée au type de document.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rString*  
 Une référence à un `CString` objet qui contient la chaîne au retour de fonction.  
  
 *index*  
 Un index de la sous-chaîne récupérée à partir de la chaîne qui décrit le type de document. Ce paramètre peut prendre l'une des valeurs suivantes :  
  
- `CDocTemplate::windowTitle` Nom qui apparaît dans le titre de la fenêtre de l’application de la barre (par exemple, « Microsoft Excel »). Présents uniquement dans le modèle de document pour les applications SDI.  
  
- `CDocTemplate::docName` Racine pour le nom de document par défaut (par exemple, « Feuille »). Cette racine, ainsi qu’un nombre, est utilisé pour le nom par défaut d’un nouveau document de ce type chaque fois que l’utilisateur sélectionne la commande Nouveau dans le menu fichier (par exemple, « Feuille1 » ou « Sheet2 »). Si non spécifié, sans « titre » est utilisé en tant que la valeur par défaut.  
  
- `CDocTemplate::fileNewName` Nom de ce type de document. Si l’application prend en charge plusieurs types de document, cette chaîne est affichée dans la boîte de dialogue Nouveau fichier (par exemple, « feuille »). Si non spécifié, le type de document est inaccessible à l’aide de la commande fichier nouveau.  
  
- `CDocTemplate::filterName` Description de type de document et un correspondance des documents de ce type de filtre de caractères génériques. Cette chaîne est affichée dans la liste déroulante Type de fichiers dans la boîte de dialogue Ouvrir le fichier (par exemple, « feuilles de calcul (*.xls) »). Si non spécifié, le type de document est inaccessible à l’aide de la commande fichier ouvrir.  
  
- `CDocTemplate::filterExt` Extension pour les documents de ce type (par exemple, « .xls »). Si non spécifié, le type de document est inaccessible à l’aide de la commande fichier ouvrir.  
  
- `CDocTemplate::regFileTypeId` Identificateur pour le type de document à stocker dans la base de données d’inscription gérée par Windows. Cette chaîne est à usage interne uniquement (par exemple, « ExcelWorksheet »). Si non spécifié, le type de document ne peut pas être enregistré avec le Gestionnaire de fichiers Windows.  
  
- `CDocTemplate::regFileTypeName` Nom du type de document à stocker dans la base de données d’inscription. Cette chaîne peut s’afficher dans les boîtes de dialogue des applications qui accèdent à la base de données d’inscription (par exemple, « classeur Excel »).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la sous-chaîne spécifiée a été trouvée ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour extraire une sous-chaîne spécifique qui décrit le type de document. La chaîne qui contient ces sous-chaînes est stockée dans le modèle de document et est dérivée d’une chaîne dans le fichier de ressources pour l’application. L’infrastructure appelle cette fonction pour obtenir les chaînes dont il a besoin pour l’interface utilisateur de l’application. Si vous avez spécifié une extension de nom de fichier pour les documents de votre application, le framework appelle également cette fonction lorsque vous ajoutez une entrée à la base de données d’inscription de Windows ; Cela permet aux documents à ouvrir à partir du Gestionnaire de fichiers Windows.  
  
 Appelez cette fonction uniquement si vous dérivez votre propre classe de `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 Récupère la position du premier document associé à ce modèle.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur POSITION qui peut être utilisée pour effectuer une itération dans la liste des documents associés à ce modèle de document ; ou NULL si la liste est vide.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction pour obtenir la position du premier document dans la liste des documents associés à ce modèle. Utilisez la valeur POSITION en tant qu’argument à [CDocTemplate::GetNextDoc](#getnextdoc) pour effectuer une itération dans la liste des documents associés au modèle.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) et [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) substituent tous deux cette fonction virtuelle pure. Toute classe que vous dérivez de `CDocTemplate` doit également remplacer cette fonction.  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 Récupère l’élément de liste identifié par *RPO*, puis définit *RPO* à la valeur de la POSITION de l’entrée suivante dans la liste.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le document suivant dans la liste des documents associés à ce modèle.  
  
### <a name="parameters"></a>Paramètres  
 *RPO*  
 Une référence à une valeur POSITION retournée par un appel précédent à [GetFirstDocPosition](#getfirstdocposition) ou `GetNextDoc`.  
  
### <a name="remarks"></a>Notes  
 Si l’élément récupéré est le dernier dans la liste, puis la nouvelle valeur de *RPO* est définie sur NULL.  
  
 Vous pouvez utiliser `GetNextDoc` dans une boucle d’itération en avant si vous établissez la position initiale avec un appel à [GetFirstDocPosition](#getfirstdocposition).  
  
 Vous devez vous assurer que votre valeur POSITION représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 Initialise la fenêtre frame et éventuellement rend visible.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFrame*  
 La fenêtre frame qui nécessite la mise à jour initiale.  
  
 *pDoc*  
 Le document auquel le frame est associé. Peut être NULL.  
  
 *bMakeVisible*  
 Indique si le frame doit devenir visible et actif.  
  
### <a name="remarks"></a>Notes  
 Appelez `IntitialUpdateFrame` après avoir créé un nouveau frame avec `CreateNewFrame`. Appel de cette fonction provoque les vues dans cette fenêtre frame pour recevoir leur `OnInitialUpdate` appels. En outre, s’il n'existait pas précédemment une vue active, la vue de la fenêtre frame principale devient active ; la vue principale est une vue avec un ID de AFX_IDW_PANE_FIRST enfant. Enfin, la fenêtre frame est rendue visible si *bMakeVisible* est différente de zéro. Si *bMakeVisible* est égal à zéro, le focus actuel et l’état visible de la fenêtre frame restent inchangée.  
  
 Il n’est pas nécessaire d’appeler cette fonction lorsque vous utilisez l’implémentation de l’infrastructure du nouveau fichier et ouvrir le fichier.  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 Charge les ressources pour une donnée `CDocTemplate` ou de la classe dérivée.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour charger les ressources pour une donnée `CDocTemplate` ou de la classe dérivée. Normalement il est appelé pendant la construction, sauf lorsque le modèle est en cours de construction dans le monde entier. Dans ce cas, l’appel à `LoadTemplate` est différée jusqu’au [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) est appelée.  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 Détermine le degré de confiance dans la correspondance entre un type de document et de ce modèle.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPathName*  
 Chemin d’accès du fichier dont le type doit être déterminée.  
  
 *rpDocMatch*  
 Pointeur vers un document qui est affecté le document correspondant, si le fichier spécifié par *lpszPathName* est déjà ouvert.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur comprise entre le **confiance** énumération, qui est définie comme suit :  
  
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
 Utilisez cette fonction pour déterminer le type de modèle de document à utiliser pour l’ouverture d’un fichier. Si votre application prend en charge plusieurs types de fichiers, par exemple, vous pouvez utiliser cette fonction pour déterminer lequel des modèles de document disponibles est approprié pour un fichier donné en appelant `MatchDocType` pour chaque modèle dans la tour et en choisissant un modèle en fonction de la valeur de confiance est retournée.  
  
 Si le fichier spécifié par *lpszPathName* est déjà ouvert, cette fonction retourne `CDocTemplate::yesAlreadyOpen` et copie le fichier `CDocument` objet dans l’objet à *rpDocMatch*.  
  
 Si le fichier n’est pas ouvert, mais l’extension dans *lpszPathName* correspond à l’extension spécifiée par `CDocTemplate::filterExt`, cette fonction retourne `CDocTemplate::yesAttemptNative` et définit *rpDocMatch* avec la valeur NULL. Pour plus d’informations sur `CDocTemplate::filterExt`, consultez [CDocTemplate::GetDocString](#getdocstring).  
  
 Si aucun cas s’applique, la fonction retourne `CDocTemplate::yesAttemptForeign`.  
  
 L’implémentation par défaut ne retourne pas `CDocTemplate::maybeAttemptForeign` ou `CDocTemplate::maybeAttemptNative`. Remplacez cette fonction pour implémenter la logique de mise en correspondance de type appropriée à votre application, par exemple à l’aide de ces deux valeurs à partir de la **confiance** énumération.  
  
##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile  
 Ouvre un fichier spécifié par un chemin d’accès.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
*lpszPathName*<br/>
[in] Pointeur vers le chemin d’accès du fichier qui contient le document à ouvrir.  
  
*bAddToMRU*<br/>
[in] TRUE indique que le document est un des fichiers plus récents ; La valeur FALSE indique que le document n’est pas un des fichiers plus récents.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le document dont le fichier est nommé par *lpszPathName*; Valeur NULL en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Ouvre le fichier dont le chemin est spécifié par *lpszPathName*. Si *lpszPathName* est NULL, un nouveau fichier qui contient un document de type associé à ce modèle est créé.  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 Supprime le document vers lequel pointé *pDoc* dans la liste des documents associés à ce modèle.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDoc*  
 Pointeur vers le document à supprimer.  
  
### <a name="remarks"></a>Notes  
 Les classes dérivées `CMultiDocTemplate` et `CSingleDocTemplate` se substitue à cette fonction. Si vous dérivez votre propre classe de modèle de document de `CDocTemplate`, votre classe dérivée doit remplacer cette fonction.  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 Enregistre tous les documents qui ont été modifiées.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon 0.  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo  
 Détermine les ressources pour les conteneurs OLE lors de la modification d’un élément d’OLE sur place.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDOleInPlaceContainer*  
 L’ID des ressources utilisées lorsqu’un objet incorporé est activé.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour définir les ressources à utiliser lors de l’objet OLE est activé sur place. Ces ressources peuvent inclure des menus et des tables d’accélérateurs. Cette fonction est généralement appelée le [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) fonction de votre application.  
  
 Le menu associé *nIDOleInPlaceContainer* contient des séparateurs qui permettent le menu de l’élément de place activé à fusionner avec le menu de l’application de conteneur. Pour plus d’informations sur la fusion de menus de serveur et un conteneur, consultez l’article [Menus et ressources (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 Appelez cette fonction pour charger le titre du document par défaut et l’afficher dans la barre de titre du document.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pDocument*  
 Pointeur vers le document dont le titre doit être défini.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur le titre par défaut, consultez la description de `CDocTemplate::docName` dans [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo  
 Détermine les ressources et les classes lorsque le document serveur incorporé ou modifié sur place.  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDOleEmbedding*  
 L’ID des ressources utilisées lorsqu’un objet incorporé est ouvert dans une fenêtre distincte.  
  
 *nIDOleInPlaceServer*  
 L’ID de ressources utilisées lors d’un objet incorporé est activé sur place.  
  
 *pOleFrameClass*  
 Pointeur vers un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure contenant des informations de classe pour l’objet de fenêtre frame créée au moment de l’activation en place.  
  
 *pOleViewClass*  
 Pointeur vers un `CRuntimeClass` structure contenant des informations de classe pour l’objet de vue créée au moment de l’activation en place.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour identifier les ressources qui seront utilisés par l’application serveur lorsque l’utilisateur demande l’activation d’un objet incorporé. Ces ressources sont constituées des menus et des tables d’accélérateurs. Cette fonction est généralement appelée le `InitInstance` de votre application.  
  
 Le menu associé *nIDOleInPlaceServer* contient des séparateurs qui permettent le menu du serveur à fusionner avec le menu du conteneur. Pour plus d’informations sur la fusion de menus de serveur et un conteneur, consultez l’article [Menus et ressources (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 Crée un frame enfant utilisé pour l’aperçu riche.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 Pointeur vers une fenêtre parente (généralement fournie par l’interpréteur de commandes).  
  
 *pDoc*  
 Pointeur vers un objet de document, dont le contenu sera visualisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur valide vers un `CFrameWnd` de l’objet, ou NULL si la création échoue.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 Configure le Gestionnaire d’aperçus de processus à l’emploi.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDPreviewFrame*  
 Spécifie un ID de ressource de l’image d’aperçu.  
  
 *pPreviewFrameClass*  
 Spécifie un pointeur vers une structure d’informations de classe runtime de l’image d’aperçu.  
  
 *pPreviewViewClass*  
 Spécifie un pointeur vers une structure d’informations de classe runtime de la vue de la version préliminaire.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate, classe](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate, classe](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument (classe)](../../mfc/reference/cdocument-class.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CScrollView, classe](../../mfc/reference/cscrollview-class.md)   
 [CEditView, classe](../../mfc/reference/ceditview-class.md)   
 [CFormView, classe](../../mfc/reference/cformview-class.md)   
 [CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd, classe](../../mfc/reference/cmdichildwnd-class.md)
