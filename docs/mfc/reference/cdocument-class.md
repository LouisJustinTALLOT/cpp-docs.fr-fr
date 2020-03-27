---
title: CDocument, classe
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418698"
---
# <a name="cdocument-class"></a>CDocument, classe

Fournit les fonctionnalités de base pour les classes de documents définies par l'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Construit un objet `CDocument`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocument::AddView](#addview)|Joint une vue au document.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Initialise la lecture du bloc.|
|[CDocument::CanCloseFrame](#cancloseframe)|Overridable avancé ; appelé avant de fermer une fenêtre frame affichant ce document.|
|[CDocument::ClearChunkList](#clearchunklist)|Efface la liste de blocs.|
|[CDocument::ClearPathName](#clearpathname)|Efface le chemin d’accès de l’objet document.|
|[CDocument::DeleteContents](#deletecontents)|Appelée pour effectuer le nettoyage du document.|
|[CDocument::FindChunk](#findchunk)|Recherche un segment avec le GUID spécifié.|
|[CDocument::GetAdapter](#getadapter)|Retourne un pointeur vers un objet qui implémente `IDocument` interface.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Retourne un pointeur vers le modèle de document qui décrit le type du document.|
|[CDocument::GetFile](#getfile)|Retourne un pointeur vers l’objet `CFile` souhaité.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Retourne la position du premier dans la liste des vues ; utilisé pour commencer l’itération.|
|[CDocument::GetNextView](#getnextview)|Itère au sein de la liste des affichages associés au document.|
|[CDocument::GetPathName](#getpathname)|Retourne le chemin d’accès du fichier de données du document.|
|[CDocument::GetThumbnail](#getthumbnail)|Appelé pour créer une image bitmap qui sera utilisée par le fournisseur de miniatures pour afficher la miniature.|
|[CDocument::GetTitle](#gettitle)|Retourne le titre du document.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Appelé pour initialiser le contenu de recherche pour le gestionnaire de recherche.|
|[CDocument::IsModified](#ismodified)|Indique si le document a été modifié depuis son dernier enregistrement.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indique si cette instance de `CDocument` objet a été créée pour la recherche & gestionnaire d’organiser.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Appelé pour charger les données de document à partir du flux.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Appelé avant la modification de la police d’aperçu enrichi.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Appelé après qu’une vue a été ajoutée ou supprimée du document.|
|[CDocument::OnCloseDocument](#onclosedocument)|Appelé pour fermer le document.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Appelée par le Framework quand il doit créer un frame d’aperçu pour l’aperçu riche.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Appelée par l’infrastructure en réponse à un événement de document.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Substituez cette méthode dans une classe dérivée pour dessiner le contenu de la miniature.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Appelée par le Framework lorsqu’il doit charger les données de document à partir du flux.|
|[CDocument::OnNewDocument](#onnewdocument)|Appelé pour créer un nouveau document.|
|[CDocument::OnOpenDocument](#onopendocument)|Appelé pour ouvrir un document existant.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Indique au gestionnaire d’aperçu de retourner le HWND à partir de l’appel de la fonction GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Indique au gestionnaire d’aperçus de gérer une séquence de touches passée à partir de la pompe de messages du processus dans lequel le gestionnaire d’aperçus s’exécute.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Appelé lorsque la couleur d’arrière-plan d’aperçu riche a changé.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Appelé lorsque la police de l’aperçu enrichi a changé.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Appelé lorsque le site d’aperçu enrichi a changé.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Appelé lorsque la couleur du texte d’aperçu enrichi a changé.|
|[CDocument::OnSaveDocument](#onsavedocument)|Appelé pour enregistrer le document sur le disque.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Appelé par le Framework lorsque le gestionnaire d’aperçus est déchargé.|
|[CDocument::PreCloseFrame](#precloseframe)|Appelé avant la fermeture de la fenêtre frame.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lit la valeur de segment suivante.|
|[CDocument::ReleaseFile](#releasefile)|Libère un fichier afin de le rendre disponible pour une utilisation par d’autres applications.|
|[CDocument::RemoveChunk](#removechunk)|Supprime un segment avec le GUID spécifié.|
|[CDocument::RemoveView](#removeview)|Détache une vue du document.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Overridable avancé ; appelé lorsqu’une opération d’ouverture ou d’enregistrement ne peut pas être effectuée en raison d’une exception.|
|[CDocument::SaveModified](#savemodified)|Overridable avancé ; appelée pour demander à l’utilisateur si le document doit être enregistré.|
|[CDocument::SetChunkValue](#setchunkvalue)|Définit une valeur de segment.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Définit un indicateur qui spécifie que vous avez modifié le document depuis son dernier enregistrement.|
|[CDocument::SetPathName](#setpathname)|Définit le chemin d’accès du fichier de données utilisé par le document.|
|[CDocument::SetTitle](#settitle)|Définit le titre du document.|
|[CDocument::UpdateAllViews](#updateallviews)|Avertit toutes les vues que le document a été modifié.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Envoie un message électronique avec le document joint.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Active la commande Envoyer un message si la prise en charge de la messagerie est présente.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Spécifie que `CDocument` objet a été créé par Dllhost pour les miniatures. Doit être archivé `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Spécifie que `CDocument` objet a été créé par prevhost pour `Rich Preview`. Doit être archivé `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Spécifie que `CDocument` objet a été créé par l’indexeur ou une autre application de recherche.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Spécifie la couleur d’arrière-plan de la fenêtre d’aperçu enrichie. Cette couleur est définie par l’hôte.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Spécifie la couleur de premier plan de la fenêtre d’aperçu enrichie. Cette couleur est définie par l’hôte.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Spécifie la police du texte pour la fenêtre d’aperçu enrichie. Ces informations de police sont définies par l’hôte.|

## <a name="remarks"></a>Remarques

Un document représente l’unité de données que l’utilisateur ouvre généralement à l’aide de la commande fichier ouvrir et enregistre à l’aide de la commande fichier enregistrer.

`CDocument` prend en charge les opérations standard, telles que la création d’un document, son chargement et son enregistrement. L’infrastructure manipule les documents à l’aide de l’interface définie par `CDocument`.

Une application peut prendre en charge plusieurs types de document ; par exemple, une application peut prendre en charge à la fois les feuilles de calcul et les documents texte. Chaque type de document est associé à un modèle de document ; le modèle de document spécifie quelles ressources (par exemple, menu, icône ou table d’accélérateur) sont utilisées pour ce type de document. Chaque document contient un pointeur vers son objet `CDocTemplate` associé.

Les utilisateurs interagissent avec un document via le ou les objets [CView](../../mfc/reference/cview-class.md) qui lui sont associés. Une vue affiche une image du document dans une fenêtre frame et interprète les entrées utilisateur comme des opérations sur le document. Plusieurs vues peuvent être associées à un document. Lorsque l’utilisateur ouvre une fenêtre sur un document, le Framework crée une vue et l’attache au document. Le modèle de document spécifie le type de vue et la fenêtre frame utilisées pour afficher chaque type de document.

Les documents font partie du routage des commandes standard du Framework et, par conséquent, reçoivent des commandes à partir de composants d’interface utilisateur standard (tels que l’élément de menu fichier enregistrer). Un document reçoit les commandes transférées par la vue active. Si le document ne gère pas une commande donnée, il transfère la commande au modèle de document qui le gère.

Lorsque les données d’un document sont modifiées, chacune de ses vues doit refléter ces modifications. `CDocument` fournit la fonction membre [UpdateAllViews](#updateallviews) pour notifier les vues de telles modifications, afin que les vues puissent se repeindre si nécessaire. Le Framework invite également l’utilisateur à enregistrer un fichier modifié avant de le fermer.

Pour implémenter des documents dans une application classique, vous devez effectuer les opérations suivantes :

- Dérivez une classe de `CDocument` pour chaque type de document.

- Ajoutez des variables membres pour stocker les données de chaque document.

- Implémentez des fonctions membres pour la lecture et la modification des données du document. Les vues du document sont les utilisateurs les plus importants de ces fonctions membres.

- Substituez la fonction membre [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) dans votre classe de document pour écrire et lire les données du document vers et depuis le disque.

`CDocument` prend en charge l’envoi de votre document par courrier électronique si la prise en charge de la messagerie (MAPI) est présente. Consultez les articles [MAPI](../../mfc/mapi.md) et [Prise en charge de MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).

Pour plus d’informations sur la `CDocument`, consultez rubriques relatives à [la sérialisation](../../mfc/serialization-in-mfc.md), à l' [architecture document/vue](../../mfc/document-view-architecture.md)et à la [création de document/vue](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cdocumentaddview"></a><a name="addview"></a>  CDocument::AddView

Appelez cette fonction pour attacher une vue au document.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView*<br/>
Pointe vers la vue ajoutée.

### <a name="remarks"></a>Remarques

Cette fonction ajoute la vue spécifiée à la liste des affichages associés au document. la fonction définit également le pointeur de document de la vue sur ce document. L’infrastructure appelle cette fonction lors de l’attachement d’un objet de vue nouvellement créé à un document. Cela se produit en réponse à une nouvelle commande de fichier, d’ouverture de fichier ou de nouvelle fenêtre ou lorsqu’une fenêtre fractionnée est fractionnée.

Appelez cette fonction uniquement si vous créez et attachez manuellement une vue. En règle générale, vous permettez à l’infrastructure de connecter des documents et des vues en définissant un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour associer une classe de document, une classe de vue et une classe de fenêtre frame.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>  CDocument::BeginReadChunks

Initialise la lecture du bloc.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>  CDocument::CanCloseFrame

Appelé par le Framework avant la fermeture d’une fenêtre frame affichant le document.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Paramètres

*pFrame*<br/>
Pointe vers la fenêtre frame d’une vue attachée au document.

### <a name="return-value"></a>Valeur de retour

Différent de zéro s’il est possible de fermer la fenêtre frame en toute sécurité ; Sinon, 0.

### <a name="remarks"></a>Remarques

L’implémentation par défaut vérifie si d’autres fenêtres Frame affichent le document. Si la fenêtre frame spécifiée est la dernière qui affiche le document, la fonction invite l’utilisateur à enregistrer le document s’il a été modifié. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de la fermeture d’une fenêtre frame. Il s’agit d’un substituable avancé.

##  <a name="cdocumentcdocument"></a><a name="cdocument"></a>  CDocument::CDocument

Construit un objet `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Remarques

Le Framework gère la création de documents pour vous. Substituez la fonction membre [OnNewDocument](#onnewdocument) pour effectuer l’initialisation pour chaque document. Cela est particulièrement important dans les applications SDI (single document interface).

##  <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>  CDocument::ClearChunkList

Efface la liste de blocs.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>  CDocument::ClearPathName

Efface le chemin d’accès de l’objet document.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Remarques

Si vous désactivez le chemin d’un objet `CDocument`, l’application invite l’utilisateur à la prochaine fois que le document est enregistré. Cela fait qu’une commande **Save** se comporte comme une commande **Enregistrer sous** .

##  <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>  CDocument::DeleteContents

Appelée par l’infrastructure pour supprimer les données du document sans détruire l’objet `CDocument` lui-même.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Remarques

Elle est appelée juste avant que le document ne soit détruit. Elle est également appelée pour s’assurer qu’un document est vide avant d’être réutilisé. Ceci est particulièrement important pour une application SDI, qui n’utilise qu’un seul document ; le document est réutilisé chaque fois que l’utilisateur crée ou ouvre un autre document. Appelez cette fonction pour implémenter un « Edit Clear All » ou une commande similaire qui supprime toutes les données du document. L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour supprimer les données de votre document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="cdocumentfindchunk"></a><a name="findchunk"></a>  CDocument::FindChunk

Recherche un segment avec un GUID spécifié.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Paramètres

*guid*<br/>
Spécifie le GUID d’un segment à rechercher.

*pid*<br/>
Spécifie le PID d’un segment à rechercher.

### <a name="return-value"></a>Valeur de retour

Position dans la liste de blocs interne en cas de réussite. Sinon, NULL.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentgetadapter"></a><a name="getadapter"></a>  CDocument::GetAdapter

Retourne un pointeur vers un objet qui implémente l’interface `IDocument`.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet qui implémente l’interface `IDocument`.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>  CDocument::GetDocTemplate

Appelez cette fonction pour obtenir un pointeur vers le modèle de document pour ce type de document.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le modèle de document pour ce type de document, ou NULL si le document n’est pas géré par un modèle de document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="cdocumentgetfile"></a><a name="getfile"></a>  CDocument::GetFile

Appelez cette fonction membre pour obtenir un pointeur vers un objet `CFile`.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu.

*pError*<br/>
Pointeur vers un objet d’exception de fichier existant qui indique l’état d’achèvement de l’opération.

*nOpenFlags*<br/>
Mode de partage et d’accès. Spécifie l’action à exécuter lors de l’ouverture du fichier. Vous pouvez combiner des options listées dans le constructeur CFile [CFile :: CFile](../../mfc/reference/cfile-class.md#cfile) à l’aide de l'&#124;opérateur de bits or (). Une autorisation d’accès et une option de partage sont requises. les modes `modeCreate` et `modeNoInherit` sont facultatifs.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CFile` .

##  <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

Appelez cette fonction pour obtenir la position du premier affichage dans la liste des vues associées au document.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour l’itération avec la fonction membre [GetNextView](#getnextview) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="cdocumentgetnextview"></a><a name="getnextview"></a>  CDocument::GetNextView

Appelez cette fonction pour itérer au sein de toutes les vues du document.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Référence à une valeur de POSITION retournée par un appel précédent aux fonctions membres `GetNextView` ou [GetFirstViewPosition](#getfirstviewposition) . Cette valeur ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la vue identifiée par *rPosition*.

### <a name="remarks"></a>Remarques

La fonction retourne la vue identifiée par *rPosition* , puis définit *rPosition* sur la valeur de position de la vue suivante dans la liste. Si la vue Récupérée est la dernière de la liste, *rPosition* a la valeur null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="cdocumentgetpathname"></a><a name="getpathname"></a>  CDocument::GetPathName

Appelez cette fonction pour récupérer le chemin d’accès complet du fichier disque du document.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès qualifié complet du document. Cette chaîne est vide si le document n’a pas été enregistré ou n’est pas associé à un fichier de disque.

##  <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>  CDocument::GetThumbnail

Crée une image bitmap que le fournisseur de miniatures doit utiliser pour afficher la miniature.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Paramètres

*cx*<br/>
Spécifie la largeur et la hauteur de la bitmap.

*phbmp*<br/>
Contient un handle vers une bitmap, lorsque la fonction est correctement retournée.

*pdwAlpha*<br/>
Contient une valeur DWORD spécifiant la valeur du canal alpha, lorsque la fonction est correctement retournée.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si un bitmap pour la miniature a été créé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentgettitle"></a><a name="gettitle"></a>  CDocument::GetTitle

Appelez cette fonction pour récupérer le titre du document, qui est généralement dérivé du nom de fichier du document.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Titre du document.

##  <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

Appelé pour initialiser le contenu de recherche pour le gestionnaire de recherche.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Remarques

Substituez cette méthode dans une classe dérivée pour initialiser le contenu de la recherche. Le contenu doit être une chaîne avec des parties délimitées par « ; ». Par exemple, «point ; Rectangle élément OLE».

##  <a name="cdocumentismodified"></a><a name="ismodified"></a>  CDocument::IsModified

Appelez cette fonction pour déterminer si le document a été modifié depuis son dernier enregistrement.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document a été modifié depuis son dernier enregistrement ; Sinon, 0.

##  <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

Indique si cette instance de `CDocument` a été créée pour le gestionnaire de recherche & organiser.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si cette instance de `CDocument` a été créée pour le gestionnaire de recherche & organiser.

### <a name="remarks"></a>Remarques

Actuellement, cette fonction retourne TRUE uniquement pour les gestionnaires d’aperçus élaborés implémentés sur un serveur hors processus. Vous pouvez définir les indicateurs appropriés (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) au niveau de votre application pour que cette fonction retourne la valeur TRUE.

##  <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

Appelé pour charger des données de document à partir d’un flux.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
Pointeur vers un flux. Ce flux est fourni par l’interpréteur de commandes.

*dwGrfMode*<br/>
Accès au mode dans le flux.

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération de chargement est réussie, sinon HRESULT avec un code d’erreur.

### <a name="remarks"></a>Remarques

Vous pouvez substituer cette méthode dans une classe dérivée pour personnaliser le mode de chargement des données à partir du flux.

##  <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

Spécifie que l’objet `CDocument` a été créé par Dllhost pour les miniatures. Doit être archivé `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Remarques

`TRUE` indique que le document a été créé par Dllhost pour les miniatures.

##  <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

Spécifie que l’objet `CDocument` a été créé par prevhost pour l’aperçu détaillé. Doit être archivé `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Remarques

La valeur TRUE indique que le document a été créé par prevhost pour l’aperçu détaillé.

##  <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

Spécifie que l’objet `CDocument` a été créé par l’indexeur ou par une autre application de recherche.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Remarques

`TRUE` indique que le document a été créé par l’indexeur ou par une autre application de recherche.

##  <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

Spécifie la couleur d’arrière-plan de la fenêtre d’aperçu enrichie. Cette couleur est définie par l’hôte.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

Spécifie la couleur de premier plan de la fenêtre d’aperçu enrichie. Cette couleur est définie par l’hôte.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

Spécifie la police du texte pour la fenêtre d’aperçu riche. Ces informations de police sont définies par l’hôte.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

Appelé avant la modification de la police d’aperçu enrichi.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

Appelée par l’infrastructure après qu’une vue a été ajoutée ou supprimée dans le document.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction vérifie si la dernière vue est supprimée et, le cas échéant, supprime le document. Substituez cette fonction si vous souhaitez effectuer un traitement spécial lorsque l’infrastructure ajoute ou supprime une vue. Par exemple, si vous souhaitez qu’un document reste ouvert même si aucune vue n’y est attachée, substituez cette fonction.

##  <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>  CDocument::OnCloseDocument

Appelée par l’infrastructure lorsque le document est fermé, en général dans le cadre de la commande file Close.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction détruit tous les frames utilisés pour afficher le document, ferme la vue, nettoie le contenu du document, puis appelle la fonction membre [DeleteContents](#deletecontents) pour supprimer les données du document.

Substituez cette fonction si vous souhaitez effectuer un traitement de nettoyage spécial lorsque l’infrastructure ferme un document. Par exemple, si le document représente un enregistrement dans une base de données, vous pouvez remplacer cette fonction pour fermer la base de données. Vous devez appeler la version de la classe de base de cette fonction à partir de votre remplacement.

##  <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

Appelée par le Framework quand il doit créer un frame d’aperçu pour l’aperçu riche.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le frame est créé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

Appelée par l’infrastructure en réponse à un événement de document.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Paramètres

*deEvent*<br/>
dans Type de données énuméré qui décrit le type d’événement.

### <a name="remarks"></a>Remarques

Les événements de document peuvent affecter plusieurs classes. Cette méthode est chargée de gérer les événements de document qui affectent des classes autres que la [classe CDocument](../../mfc/reference/cdocument-class.md). Actuellement, la seule classe qui doit répondre aux événements de document est la [classe CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). La classe `CDocument` a d’autres méthodes substituables responsables de la gestion de l’effet sur l' `CDocument`.

Le tableau suivant répertorie les valeurs possibles pour *deeventt et les* événements auxquels elles correspondent.

|Value|Événement correspondant|
|-----------|-------------------------|
|`onAfterNewDocument`|Un nouveau document a été créé.|
|`onAfterOpenDocument`|Un nouveau document a été ouvert.|
|`onAfterSaveDocument`|Le document a été enregistré.|
|`onAfterCloseDocument`|Le document a été fermé.|

##  <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

Substituez cette méthode dans une classe dérivée pour dessiner la miniature.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Paramètres

*dc*<br/>
Référence à un contexte de périphérique (Device Context).

*lprcBounds*<br/>
Spécifie un rectangle englobant de la zone dans laquelle la miniature doit être dessinée.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>  CDocument::OnFileSendMail

Envoie un message via l’hôte de messagerie résident (le cas échéant) avec le document en tant que pièce jointe.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Remarques

`OnFileSendMail` appelle [OnSaveDocument](#onsavedocument) pour sérialiser (enregistrer) les documents sans titre et modifiés dans un fichier temporaire, qui est ensuite envoyé par courrier électronique. Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire. l’original est envoyé. `OnFileSendMail` charge MAPI32. DLL s’il n’a pas déjà été chargé.

Une implémentation spéciale de `OnFileSendMail` pour [COleDocument](../../mfc/reference/coledocument-class.md) gère correctement les fichiers composés.

`CDocument` prend en charge l’envoi de votre document par courrier électronique si la prise en charge de la messagerie (MAPI) est présente. Consultez les articles [MAPI rubriques](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

Appelée par le Framework lorsqu’il doit charger les données de document à partir d’un flux.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
Pointeur vers un flux entrant.

*grfMode*<br/>
Accès au mode dans le flux.

### <a name="return-value"></a>Valeur de retour

S_OK si la charge est réussie ; Sinon, code d’erreur.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>  CDocument::OnNewDocument

Appelée par l’infrastructure dans le cadre de la commande fichier nouveau.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document a été initialisé avec succès ; Sinon, 0.

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction appelle la fonction membre [DeleteContents](#deletecontents) pour s’assurer que le document est vide, puis marque le nouveau document comme propre. Substituez cette fonction pour initialiser la structure de données pour un nouveau document. Vous devez appeler la version de la classe de base de cette fonction à partir de votre remplacement.

Si l’utilisateur choisit la commande fichier nouveau dans une application SDI, le Framework utilise cette fonction pour réinitialiser le document existant, au lieu d’en créer un nouveau. Si l’utilisateur choisit fichier dans une application d’interface multidocument (MDI), l’infrastructure crée un nouveau document à chaque fois, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction plutôt que dans le constructeur pour que la commande fichier nouveau soit efficace dans les applications SDI.

Notez que dans certains cas, `OnNewDocument` est appelé deux fois. Cela se produit lorsque le document est incorporé en tant que serveur de documents ActiveX. La fonction est d’abord appelée par la méthode `CreateInstance` (exposée par la classe dérivée de `COleObjectFactory`) et une deuxième fois par la méthode `InitNew` (exposée par la classe dérivée de `COleServerDoc`).

### <a name="example"></a>Exemple

Les exemples suivants illustrent d’autres méthodes d’initialisation d’un objet document.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>  CDocument::OnOpenDocument

Appelée par l’infrastructure dans le cadre de la commande fichier ouvrir.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Pointe vers le chemin d’accès du document à ouvrir.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document a été chargé avec succès ; Sinon, 0.

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction ouvre le fichier spécifié, appelle la fonction membre [DeleteContents](#deletecontents) pour vérifier que le document est vide, appelle [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) pour lire le contenu du fichier, puis marque le document comme propre. Remplacez cette fonction si vous voulez utiliser autre chose que le mécanisme d’archivage ou le mécanisme de fichier. Par exemple, vous pouvez écrire une application dans laquelle les documents représentent des enregistrements dans une base de données plutôt que des fichiers séparés.

Si l’utilisateur choisit la commande fichier ouvrir dans une application SDI, le Framework utilise cette fonction pour réinitialiser l’objet `CDocument` existant, au lieu d’en créer un nouveau. Si l’utilisateur choisit fichier ouvrir dans une application MDI, le Framework construit à chaque fois un nouvel objet `CDocument`, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction plutôt que dans le constructeur pour que la commande fichier ouvrir soit efficace dans les applications SDI.

### <a name="example"></a>Exemple

Les exemples suivants illustrent d’autres méthodes d’initialisation d’un objet document.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

Indique au gestionnaire d’aperçu de retourner le HWND récupéré à partir de l’appel de la fonction `GetFocus`.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Paramètres

*phwnd*<br/>
à Lorsque cette méthode est retournée, contient un pointeur vers le HWND retourné par l’appel de la fonction `GetFocus` à partir du thread de premier plan du gestionnaire d’aperçus.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ; ou une valeur d’erreur dans le cas contraire.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

Indique au gestionnaire d’aperçus de gérer une séquence de touches passée à partir de la pompe de messages du processus dans lequel le gestionnaire d’aperçus s’exécute.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Paramètres

*pmsg*<br/>
dans Pointeur vers un message de fenêtre.

### <a name="return-value"></a>Valeur de retour

Si le message de frappe de touche peut être traité par le gestionnaire d’aperçus, le gestionnaire le traite et retourne S_OK. Si le gestionnaire d’aperçus ne peut pas traiter le message de frappe, il l’offre à l’hôte via `IPreviewHandlerFrame::TranslateAccelerator`. Si l’hôte traite le message, cette méthode retourne S_OK. Si l’hôte ne traite pas le message, cette méthode retourne S_FALSE.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

Appelé lorsque la couleur d’arrière-plan de l’aperçu enrichi a changé.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

Appelé lorsque la police de l’aperçu enrichi a changé.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

Appelé lorsque le site d’aperçu enrichi a changé.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

Appelé lorsque la couleur du texte d’aperçu enrichi a changé.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>  CDocument::OnSaveDocument

Appelée par l’infrastructure dans le cadre de la commande fichier enregistrer ou enregistrer sous.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Pointe vers le chemin d’accès complet vers lequel le fichier doit être enregistré.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document a été enregistré avec succès ; Sinon, 0.

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction ouvre le fichier spécifié, appelle [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) pour écrire les données du document dans le fichier, puis marque le document comme propre. Substituez cette fonction si vous souhaitez effectuer un traitement spécial lorsque l’infrastructure enregistre un document. Par exemple, vous pouvez écrire une application dans laquelle les documents représentent des enregistrements dans une base de données plutôt que des fichiers séparés.

##  <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

Appelé par le Framework lorsque le gestionnaire d’aperçus est déchargé.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Remarques

##  <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

Active la commande ID_FILE_SEND_MAIL si la prise en charge de la messagerie (MAPI) est présente.

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers l’objet [CCmdUI](../../mfc/reference/ccmdui-class.md) associé à la commande ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Remarques

Dans le cas contraire, la fonction supprime la commande ID_FILE_SEND_MAIL du menu, y compris les séparateurs situés au-dessus ou en dessous de l’élément de menu, le cas échéant. MAPI est activé si MAPI32. DLL est présent dans le chemin d’accès et, dans la section [mail] du fichier WIN. Fichier INI, MAPI = 1. La plupart des applications placent cette commande dans le menu fichier.

`CDocument` prend en charge l’envoi de votre document par courrier électronique si la prise en charge de la messagerie (MAPI) est présente. Consultez les articles [MAPI rubriques](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>  CDocument::PreCloseFrame

Cette fonction membre est appelée par le Framework avant la destruction de la fenêtre frame.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Paramètres

*pFrame*<br/>
Pointeur vers le [CFrameWnd](../../mfc/reference/cframewnd-class.md) qui contient l’objet `CDocument` associé.

### <a name="remarks"></a>Remarques

Il peut être substitué pour fournir un nettoyage personnalisé, mais veillez à appeler également la classe de base.

La valeur par défaut de `PreCloseFrame` ne fait rien dans `CDocument`. Les classes dérivées de `CDocument`[COleDocument](../../mfc/reference/coledocument-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilisent cette fonction membre.

##  <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

Lit la valeur de segment suivante.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Paramètres

*ppValue*<br/>
à Quand la fonction retourne, *ppValue* contient la valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentreleasefile"></a><a name="releasefile"></a>  CDocument::ReleaseFile

Cette fonction membre est appelée par l’infrastructure pour libérer un fichier, ce qui la rend disponible pour une utilisation par d’autres applications.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Paramètres

*pFile*<br/>
Pointeur vers l’objet CFile à libérer.

*bAbort*<br/>
Spécifie si le fichier doit être libéré à l’aide de `CFile::Close` ou `CFile::Abort`. FALSe si le fichier doit être libéré à l’aide de [CFile :: Close](../../mfc/reference/cfile-class.md#close); TRUE si le fichier doit être libéré à l’aide de [CFile :: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Remarques

Si *bAbort* a la valeur TRUE, `ReleaseFile` appelle `CFile::Abort`et le fichier est libéré. `CFile::Abort` ne lèvera pas d’exception.

Si *bAbort* a la valeur false, `ReleaseFile` appelle `CFile::Close` et le fichier est libéré.

Substituez cette fonction membre pour exiger une action de l’utilisateur avant que le fichier ne soit libéré.

##  <a name="cdocumentremovechunk"></a><a name="removechunk"></a>  CDocument::RemoveChunk

Supprime un segment avec le GUID spécifié.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Paramètres

*Guid*<br/>
Spécifie le GUID d’un bloc à supprimer.

*Pid*<br/>
Spécifie le PID d’un segment à supprimer.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentremoveview"></a><a name="removeview"></a>  CDocument::RemoveView

Appelez cette fonction pour détacher une vue d’un document.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView*<br/>
Pointe vers la vue en cours de suppression.

### <a name="remarks"></a>Remarques

Cette fonction supprime la vue spécifiée de la liste des affichages associés au document. Il définit également le pointeur de document de la vue sur NULL. Cette fonction est appelée par le Framework lorsqu’une fenêtre frame est fermée ou lorsqu’un volet d’une fenêtre fractionnée est fermé.

Appelez cette fonction uniquement si vous détachez manuellement une vue. En général, vous permettez à l’infrastructure de détacher des documents et des vues en définissant un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour associer une classe de document, une classe de vue et une classe de fenêtre frame.

Consultez l’exemple de [AddView](#addview) pour obtenir un exemple d’implémentation.

##  <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

Appelé si une exception est levée (généralement [CFileException](../../mfc/reference/cfileexception-class.md) ou [CArchiveException](../../mfc/reference/carchiveexception-class.md)) lors de l’enregistrement ou du chargement du document.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Pointe vers le nom du document qui a été enregistré ou chargé.

*e*<br/>
Pointe vers l’exception qui a été levée. Peut être NULL.

*bSaving*<br/>
Indicateur qui spécifie l’opération en cours ; différent de zéro si le document était en cours d’enregistrement, 0 si le document était en cours de chargement.

*nIDPDefault*<br/>
Identificateur du message d’erreur à afficher si la fonction ne spécifie pas une valeur plus spécifique.

### <a name="remarks"></a>Remarques

L’implémentation par défaut examine l’objet exception et recherche un message d’erreur qui décrit la cause de manière spécifique. Si un message spécifique est introuvable ou si *e* est null, le message général spécifié par le paramètre *nIDPDefault* est utilisé. La fonction affiche ensuite une boîte de message contenant le message d’erreur. Remplacez cette fonction si vous souhaitez fournir des messages d’échec personnalisés supplémentaires. Il s’agit d’un substituable avancé.

##  <a name="cdocumentsavemodified"></a><a name="savemodified"></a>  CDocument::SaveModified

Appelé par le Framework avant la fermeture d’un document modifié.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro s’il est possible de continuer et de fermer le document. 0 si le document ne doit pas être fermé.

### <a name="remarks"></a>Remarques

L’implémentation par défaut de cette fonction affiche une boîte de message demandant à l’utilisateur s’il souhaite enregistrer les modifications apportées au document, le cas échéant. Remplacez cette fonction si votre programme requiert une autre procédure d’invite. Il s’agit d’un substituable avancé.

##  <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>  CDocument::SetChunkValue

Définit une valeur de segment.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Spécifie une valeur de segment à définir.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Remarques

##  <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

Appelez cette fonction après avoir apporté des modifications au document.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModified*<br/>
Indicateur précisant si le document a été modifié.

### <a name="remarks"></a>Remarques

En appelant cette fonction de manière cohérente, vous vous assurez que l’infrastructure invite l’utilisateur à enregistrer les modifications avant de fermer un document. En général, vous devez utiliser la valeur par défaut TRUE pour le paramètre *bModified* . Pour marquer un document comme étant propre (non modifié), appelez cette fonction avec la valeur FALSe.

##  <a name="cdocumentsetpathname"></a><a name="setpathname"></a>  CDocument::SetPathName

Appelez cette fonction pour spécifier le chemin d’accès complet du fichier disque du document.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Pointe vers la chaîne à utiliser comme chemin d’accès du document.

*bAddToMRU*<br/>
Détermine si le nom de fichier est ajouté à la liste des derniers fichiers utilisés (MRU). Si la valeur est TRUE, le nom de fichier est ajouté ; Si la valeur est FALSe, il n’est pas ajouté.

### <a name="remarks"></a>Remarques

Selon la valeur de *bAddToMRU* , le chemin d’accès est ajouté, ou n’est pas ajouté, à la liste MRU gérée par l’application. Notez que certains documents ne sont pas associés à un fichier sur disque. Appelez cette fonction uniquement si vous substituez l’implémentation par défaut pour ouvrir et enregistrer des fichiers utilisés par le Framework.

##  <a name="cdocumentsettitle"></a><a name="settitle"></a>  CDocument::SetTitle

Appelez cette fonction pour spécifier le titre du document (la chaîne affichée dans la barre de titre d’une fenêtre frame).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Paramètres

*lpszTitle*<br/>
Pointe vers la chaîne à utiliser comme titre du document.

### <a name="remarks"></a>Remarques

L’appel de cette fonction met à jour les titres de toutes les fenêtres frame qui affichent le document.

##  <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>  CDocument::UpdateAllViews

Appelez cette fonction après la modification du document.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Pointe vers la vue qui a modifié le document, ou NULL si toutes les vues doivent être mises à jour.

*lHint*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Pointe vers un objet qui stocke des informations sur la modification.

### <a name="remarks"></a>Remarques

Vous devez appeler cette fonction après avoir appelé la fonction membre [SetModifiedFlag](#setmodifiedflag) . Cette fonction informe chaque vue attachée au document, à l’exception de la vue spécifiée par *pSender*, que le document a été modifié. En général, vous appelez cette fonction à partir de votre classe d’affichage une fois que l’utilisateur a modifié le document par le biais d’une vue.

Cette fonction appelle la fonction membre [CView :: OnUpdate](../../mfc/reference/cview-class.md#onupdate) pour chacune des vues du document, à l’exception de la vue envoi, en passant *pHint* et *lHint*. Utilisez ces paramètres pour transmettre des informations aux vues concernant les modifications apportées au document. Vous pouvez encoder des informations à l’aide de *lHint* et/ou vous pouvez définir une classe dérivée de [CObject](../../mfc/reference/cobject-class.md)pour stocker des informations sur les modifications et passer un objet de cette classe à l’aide de *pHint*. Remplacez la fonction membre `CView::OnUpdate` dans votre classe dérivée de [CView](../../mfc/reference/cview-class.md)pour optimiser la mise à jour de l’affichage de la vue en fonction des informations passées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Exemple de NPP MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)
