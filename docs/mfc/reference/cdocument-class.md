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
ms.openlocfilehash: d356ba6b6134221c2fc9595fc6d78f91961c5b7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753248"
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
|[CDocument::AddView](#addview)|Attache une vue au document.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Initialise la lecture de morceaux.|
|[CDocument::CanCloseFrame](#cancloseframe)|Avancée primordiale; appelé avant de fermer une fenêtre de cadre en regardant ce document.|
|[CDocument::ClearChunkList](#clearchunklist)|Efface la liste des morceaux.|
|[CDocument::ClearPathName](#clearpathname)|Efface le chemin de l’objet du document.|
|[CDocument::DeleteContents](#deletecontents)|Appelé pour effectuer le nettoyage du document.|
|[CDocument::FindChunk](#findchunk)|Recherche un morceau avec GUID spécifié.|
|[CDocument::GetAdapter](#getadapter)|Retourne un pointeur `IDocument` pour objecter l’interface de mise en œuvre.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Renvoie un pointeur au modèle de document qui décrit le type de document.|
|[CDocument::GetFile](#getfile)|Retourne un pointeur `CFile` à l’objet désiré.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Renvoie la position du premier dans la liste des points de vue; utilisé pour commencer l’itération.|
|[CDocument::GetNextView](#getnextview)|Itérations à travers la liste des points de vue associés au document.|
|[CDocument::GetPathName](#getpathname)|Retourne le chemin du fichier de données du document.|
|[CDocument::GetThumbnail](#getthumbnail)|Appelé à créer une bitmap à utiliser par le fournisseur de vignettes pour afficher la vignette.|
|[CDocument::GetTitle](#gettitle)|Retourne le titre du document.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Appelé à initialiser le contenu de recherche pour Search Handler.|
|[CDocument::IsModified](#ismodified)|Indique si le document a été modifié depuis sa dernière économie.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indique si cette `CDocument` instance d’objet a été créée pour Search & Organize handler.|
|[CDocument::LoadDocumentDeStream](#loaddocumentfromstream)|Appelé à charger les données de documents à partir du flux.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Appelé avant la police Rich Preview est changé.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Appelé après qu’une vue soit ajoutée ou supprimée du document.|
|[CDocument::OnCloseDocument](#onclosedocument)|Appelé pour fermer le document.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Appelé par le cadre quand il a besoin de créer un cadre de prévisualisation pour Rich Preview.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Appelé par le cadre en réponse à un événement de document.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Remplacer cette méthode dans une classe dérivée pour dessiner le contenu de la vignette.|
|[CDocument::OnLoadDocumentDeStream](#onloaddocumentfromstream)|Appelé par le cadre quand il a besoin de charger les données de document à partir du flux.|
|[CDocument::OnNewDocument](#onnewdocument)|Appelé à créer un nouveau document.|
|[CDocument::OnOpenDocument](#onopendocument)|Appelé à ouvrir un document existant.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Dirige le gestionnaire de prévisualisation de retourner le HWND d’appeler la fonction GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Dirige le gestionnaire de prévisualisation pour gérer une frappe passée à partir de la pompe de message du processus dans lequel le gestionnaire de prévisualisation est en cours d’exécution.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Appelé lorsque la couleur de fond Rich Preview a changé.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Appelé lorsque la police Rich Preview a changé.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Appelé lorsque le site Rich Preview a changé.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Appelé lorsque la couleur du texte Rich Preview a changé.|
|[CDocument::OnSaveDocument](#onsavedocument)|Appelé pour enregistrer le document sur disque.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Appelé par le cadre lorsque le gestionnaire de prévisualisation est déchargé.|
|[CDocument::PreCloseFrame](#precloseframe)|Appelé avant la fenêtre du cadre est fermé.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lit la valeur suivante de morceau.|
|[CDocument::ReleaseFile](#releasefile)|Publie un fichier pour le rendre disponible pour une utilisation par d’autres applications.|
|[CDocument::RemoveChunk](#removechunk)|Supprime un morceau avec GUID spécifié.|
|[CDocument::RemoveView](#removeview)|Détache une vue du document.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Avancée primordiale; lorsqu’une opération ouverte ou sauve ne peut pas être effectuée en raison d’une exception.|
|[CDocument::SaveModified](#savemodified)|Avancée primordiale; appelé à demander à l’utilisateur si le document doit être enregistré.|
|[CDocument::SetChunkValue](#setchunkvalue)|Définit une valeur de morceau.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Définit un drapeau indiquant que vous avez modifié le document depuis sa dernière économie.|
|[CDocument::SetPathName](#setpathname)|Définit le chemin du fichier de données utilisé par le document.|
|[CDocument::SetTitle](#settitle)|Définit le titre du document.|
|[CDocument::UpdateAllViews](#updateallviews)|Informe tous les points de vue que le document a été modifié.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Envoie un message postal avec le document ci-joint.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Permet la commande Send Mail si le support postal est présent.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Précise que `CDocument` l’objet a été créé par dllhost pour les vignettes. Devrait être `CView::OnDraw`enregistré .|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Précise que `CDocument` l’objet a été créé `Rich Preview`par prevhost pour . Devrait être `CView::OnDraw`enregistré .|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Précise que `CDocument` cet objet a été créé par un indexeur ou une autre application de recherche.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Spécifie la couleur de fond de la fenêtre Rich Preview. Cette couleur est définie par l’hôte.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Spécifie la couleur au premier plan de la fenêtre Rich Preview. Cette couleur est définie par l’hôte.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Spécifie la police de texte pour la fenêtre Rich Preview. Cette information de police est définie par l’hôte.|

## <a name="remarks"></a>Notes

Un document représente l’unité de données que l’utilisateur ouvre généralement avec la commande De Fichier Open et enregistre avec la commande Enregistrement de fichiers.

`CDocument`prend en charge les opérations standard telles que la création d’un document, le chargement et l’économie. Le cadre manipule les `CDocument`documents à l’aide de l’interface définie par .

Une application peut prendre en charge plus d’un type de document; par exemple, une application peut prendre en charge à la fois les feuilles de calcul et les documents texte. Chaque type de document a un modèle de document associé; le modèle de document précise quelles ressources (par exemple, menu, icône ou table d’accélérateur) sont utilisées pour ce type de document. Chaque document contient un `CDocTemplate` pointeur sur son objet associé.

Les utilisateurs interagissent avec un document via l’objet [CView(s)](../../mfc/reference/cview-class.md) qui lui est associé. Une vue rend une image du document dans une fenêtre de cadre et interprète l’entrée de l’utilisateur comme des opérations sur le document. Un document peut avoir plusieurs points de vue qui lui sont associés. Lorsque l’utilisateur ouvre une fenêtre sur un document, le cadre crée une vue et la fixe au document. Le modèle de document précise quel type de vue et de fenêtre de cadre sont utilisés pour afficher chaque type de document.

Les documents font partie du routage de commande standard du cadre et reçoivent par conséquent des commandes à partir de composants standard d’interface utilisateur (tels que l’élément de menu Enregistrement de fichiers). Un document reçoit des commandes transmises par la vue active. Si le document ne gère pas une commande donnée, il transmet la commande au modèle de document qui le gère.

Lorsque les données d’un document sont modifiées, chacune de ses vues doit refléter ces modifications. `CDocument`fournit la fonction de membre [UpdateAllViews](#updateallviews) pour vous d’aviser les vues de ces changements, de sorte que les vues peuvent se repeindre au besoin. Le cadre invite également l’utilisateur à enregistrer un fichier modifié avant de le fermer.

Pour implémenter des documents dans une demande type, vous devez faire ce qui suit :

- Dérivez une `CDocument` classe pour chaque type de document.

- Ajoutez des variables de membre pour stocker les données de chaque document.

- Implémentez les fonctions des membres pour lire et modifier les données du document. Les vues du document sont les utilisateurs les plus importants de ces fonctions de membre.

- Remplacer le [CObject ::Serialize](../../mfc/reference/cobject-class.md#serialize) fonction membre dans votre classe de documents pour écrire et lire les données du document à et en provenance du disque.

`CDocument`prend en charge l’envoi de votre document par la poste si le support postal (MAPI) est présent. Voir les articles [MAPI](../../mfc/mapi.md) et [MAPI Support dans MFC](../../mfc/mapi-support-in-mfc.md).

Pour plus `CDocument`d’informations sur , voir [Serialization](../../mfc/serialization-in-mfc.md), [Document/View Architecture Topics](../../mfc/document-view-architecture.md), et [Document/View Creation](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::AddView

Appelez cette fonction pour joindre une vue au document.

```cpp
void AddView(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView (en)*<br/>
Points de vue ajoutés.

### <a name="remarks"></a>Notes

Cette fonction ajoute la vue spécifiée à la liste des points de vue associés au document; la fonction définit également le pointeur de document de la vue sur ce document. Le cadre appelle cette fonction lors de l’attachement d’un objet de vue nouvellement créé à un document; cela se produit en réponse à une commande De fichier Nouveau, Fichier Ou Nouvelle Fenêtre ou lorsqu’une fenêtre de séparation est divisée.

Appelez cette fonction uniquement si vous créez et attachez manuellement une vue. En règle générale, vous laisserez le cadre connecter les documents et les vues en définissant un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour associer une classe de documents, une classe de vue et une classe de fenêtre de cadre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks

Initialise la lecture de morceaux.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame

Appelé par le cadre avant qu’une fenêtre de cadre affichant le document soit fermée.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Paramètres

*pFrame (en)*<br/>
Points à la fenêtre de cadre d’une vue attachée au document.

### <a name="return-value"></a>Valeur de retour

Nonzero s’il est sécuritaire de fermer la fenêtre du cadre; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut vérifie s’il y a d’autres fenêtres de cadre affichant le document. Si la fenêtre d’image spécifiée est la dernière qui affiche le document, la fonction invite l’utilisateur à enregistrer le document s’il a été modifié. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’une fenêtre de cadre est fermée. C’est un avancé primordial.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument

Construit un objet `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Notes

Le cadre gère la création de documents pour vous. Remplacer la fonction membre [OnNewDocument](#onnewdocument) pour effectuer l’initialisation par document; ceci est particulièrement important dans les applications d’interface de document unique (SDI).

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList

Efface la liste des morceaux.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName

Efface le chemin de l’objet du document.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Notes

Le dégagement du `CDocument` chemin d’un objet provoque l’application d’inciter l’utilisateur lorsque le document est ensuite enregistré. Cela fait une commande **Save** se comporter comme un **Save As** commande.

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents

Appelé par le cadre pour supprimer les données `CDocument` du document sans détruire l’objet lui-même.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Notes

Il est appelé juste avant que le document soit détruit. Il est également appelé à s’assurer qu’un document est vide avant qu’il ne soit réutilisé. Ceci est particulièrement important pour une application SDI, qui n’utilise qu’un seul document; le document est réutilisé chaque fois que l’utilisateur crée ou ouvre un autre document. Appelez cette fonction pour implémenter un "Modifier Clear All" ou une commande similaire qui supprime toutes les données du document. L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour supprimer les données de votre document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk

Recherche un morceau avec un GUID spécifié.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Paramètres

*guid*<br/>
Spécifie le GUID d’un morceau à trouver.

*Pid*<br/>
Spécifie une MIP d’un morceau à trouver.

### <a name="return-value"></a>Valeur de retour

Position dans la liste interne de morceau en cas de succès. Sinon NULL.

### <a name="remarks"></a>Notes

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter

Retourne un pointeur à `IDocument` un objet implémentant l’interface.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un `IDocument` objet implémentant l’interface.

### <a name="remarks"></a>Notes

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate

Appelez cette fonction pour obtenir un pointeur sur le modèle de document pour ce type de document.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le modèle de document pour ce type de document, ou NULL si le document n’est pas géré par un modèle de document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile

Appelez cette fonction de membre `CFile` pour obtenir un pointeur à un objet.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Une chaîne qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu.

*Perror*<br/>
Pointeur d’un objet existant d’exception de fichier qui indique l’état d’achèvement de l’opération.

*nOpenFlags*<br/>
Mode de partage et d’accès. Spécifie les mesures à prendre lors de l’ouverture du fichier. Vous pouvez combiner les options répertoriées dans le constructeur [CFile CFile::CFile](../../mfc/reference/cfile-class.md#cfile) en utilisant l’opérateur bitwise OU (&#124;). Une autorisation d’accès et une option d’action sont requises; les `modeCreate` `modeNoInherit` modes et les modes sont facultatifs.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CFile`.

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition

Appelez cette fonction pour obtenir la position de la première vue dans la liste des vues associées au document.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour l’itération avec la fonction membre [GetNextView.](#getnextview)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView

Appelez cette fonction à itérer à travers toutes les vues du document.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Paramètres

*rPosition*<br/>
Une référence à une valeur POSITION retournée `GetNextView` par un appel précédent aux fonctions des membres [ou GetFirstViewPosition.](#getfirstviewposition) Cette valeur ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la vue identifiée par *rPosition*.

### <a name="remarks"></a>Notes

La fonction renvoie la vue identifiée par *rPosition,* puis définit *rPosition* à la valeur POSITION de la vue suivante dans la liste. Si la vue récupérée est la dernière de la liste, puis *rPosition* est réglé sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName

Appelez cette fonction pour obtenir le chemin entièrement qualifié du fichier disque du document.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Valeur de retour

La voie du document est entièrement qualifiée. Cette chaîne est vide si le document n’a pas été enregistré ou n’a pas de fichier disque associé à celui-ci.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail

Crée une bitmap à utiliser par le fournisseur de vignettes pour afficher la vignette.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Paramètres

*Cx*<br/>
Spécifie la largeur et la hauteur de la bitmap.

*phbmp*<br/>
Contient une poignée à un bitmap, lorsque la fonction revient avec succès.

*pdwAlpha*<br/>
Contient un DWORD spécifiant la valeur du canal alpha, lorsque la fonction revient avec succès.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si un bitmap pour la vignette a été créé avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle

Appelez cette fonction pour obtenir le titre du document, qui est généralement dérivé du nom de fichier du document.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Le titre du document.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent

Appelé à initialiser le contenu de recherche pour le gestionnaire de recherche.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour initialiser le contenu de recherche. Le contenu doit être une chaîne avec des pièces délimitées par ";". Par exemple, "point; rectangle; ole article".

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument::IsModified

Appelez cette fonction pour déterminer si le document a été modifié depuis sa dernière économie.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a été modifié depuis sa dernière économie; sinon 0.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler

Indique si cette `CDocument` instance a été créée pour le gestionnaire d’organiser de recherche &.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si `CDocument` cette instance a été créée pour le gestionnaire De recherche & Organiser.

### <a name="remarks"></a>Notes

Actuellement, cette fonction retourne TRUE uniquement pour les gestionnaires Rich Preview mis en œuvre dans un serveur hors processus. Vous pouvez définir les drapeaux appropriés (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) au niveau de votre application pour rendre cette fonction de retour VRAI.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentDeStream

Appelé à charger les données de documents à partir d’un flux.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
Un pointeur à un ruisseau. Ce flux est fourni par la Shell.

*dwGrfMode dwGrfMode*<br/>
Mode d’accès au flux.

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération de charge réussit, sinon HRESULT avec un code d’erreur.

### <a name="remarks"></a>Notes

Vous pouvez remplacer cette méthode dans une classe dérivée pour personnaliser la façon de charger les données à partir du flux.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

Précise que l’objet `CDocument` a été créé par dllhost pour les vignettes. Devrait être `CView::OnDraw`enregistré .

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Notes

`TRUE`indique que le document a été créé par dllhost pour les vignettes.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

Spécifie `CDocument` que l’objet a été créé par prevhost pour Rich Preview. Devrait être `CView::OnDraw`enregistré .

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Notes

TRUE indique que le document a été créé par prevhost pour Rich Preview.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode

Précise que l’objet `CDocument` a été créé par l’indexeur ou par une autre application de recherche.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Notes

`TRUE`indique que le document a été créé par l’indexeur ou par une autre application de recherche.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

Spécifie la couleur de fond de la fenêtre Rich Preview. Cette couleur est définie par l’hôte.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Notes

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

Spécifie la couleur de premier plan de la fenêtre Rich Preview. Cette couleur est définie par l’hôte.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Notes

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

Spécifie la police de texte pour la fenêtre Rich Preview. Cette information de police est définie par l’hôte.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged

Appelé avant la police Rich Preview est changé.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList

Appelé par le cadre après qu’une vue est ajoutée ou supprimée du document.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction vérifie si la dernière vue est supprimée et, dans l’affirmative, supprime le document. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lorsque le cadre ajoute ou supprime une vue. Par exemple, si vous voulez qu’un document reste ouvert même s’il n’y a pas de vues qui y sont jointes, remplacez cette fonction.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument

Appelé par le cadre lorsque le document est fermé, généralement dans le cadre de la commande De fichier Close.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction détruit toutes les images utilisées pour la visualisation du document, ferme la vue, nettoie le contenu du document, puis appelle la fonction membre [DeleteContents](#deletecontents) pour supprimer les données du document.

Remplacez cette fonction si vous souhaitez effectuer un traitement de nettoyage spécial lorsque le cadre ferme un document. Par exemple, si le document représente un enregistrement dans une base de données, vous pouvez remplacer cette fonction pour fermer la base de données. Vous devez appeler la version de classe de base de cette fonction à partir de votre remplacement.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame

Appelé par le cadre quand il a besoin de créer un cadre de prévisualisation pour Rich Preview.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le cadre est créé avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent

Appelé par le cadre en réponse à un événement de document.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Paramètres

*deEvent*<br/>
[dans] Un type de données énuméré qui décrit le type d’événement.

### <a name="remarks"></a>Notes

Les événements documentaires peuvent affecter plusieurs classes. Cette méthode est responsable de la gestion des événements documentaires qui affectent des classes autres que la [classe CDocument](../../mfc/reference/cdocument-class.md). Actuellement, la seule classe qui doit répondre aux événements documentaires est la [classe CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). La `CDocument` classe a d’autres méthodes dérogations responsables de la manipulation de l’effet sur le `CDocument`.

Le tableau suivant énumère les valeurs possibles pour *deEvent* et les événements auxquels elles correspondent.

|Valeur|Événement correspondant|
|-----------|-------------------------|
|`onAfterNewDocument`|Un nouveau document a été créé.|
|`onAfterOpenDocument`|Un nouveau document a été ouvert.|
|`onAfterSaveDocument`|Le document a été enregistré.|
|`onAfterCloseDocument`|Le document a été fermé.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail

Remplacer cette méthode dans une classe dérivée pour dessiner la vignette.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
Une référence au contexte d’un appareil.

*lprcBounds (lprcBounds)*<br/>
Spécifie un rectangle de délimitation de la zone où la vignette doit être tirée.

### <a name="remarks"></a>Notes

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::OnFileSendMail

Envoie un message via l’hébergeur de courrier résident (le cas échéant) avec le document comme pièce jointe.

```cpp
void OnFileSendMail();
```

### <a name="remarks"></a>Notes

`OnFileSendMail`invite [OnSaveDocument](#onsavedocument) à sérialiser (enregistrer) des documents sans titre et modifiés à un fichier temporaire, qui est ensuite envoyé par courrier électronique. Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire; l’original est envoyé. `OnFileSendMail`charge MAPI32. DLL s’il n’a pas déjà été chargé.

Une mise `OnFileSendMail` en œuvre spéciale de [COleDocument](../../mfc/reference/coledocument-class.md) gère correctement les fichiers composés.

`CDocument`prend en charge l’envoi de votre document par la poste si le support postal (MAPI) est présent. Voir les articles [MAPI Topics](../../mfc/mapi.md) et [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentDeStream

Appelé par le cadre quand il a besoin de charger les données de document à partir d’un flux.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
Un pointeur à un flux entrant.

*grfMode grfMode*<br/>
Mode d’accès au flux.

### <a name="return-value"></a>Valeur de retour

S_OK si la charge est réussie; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument

Appelé par le cadre dans le cadre du fichier Nouveau commandement.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a été paradérodé avec succès; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction appelle la fonction membre [DeleteContents](#deletecontents) pour s’assurer que le document est vide, puis marque le nouveau document comme propre. Remplacer cette fonction pour initialiser la structure de données d’un nouveau document. Vous devez appeler la version de classe de base de cette fonction à partir de votre remplacement.

Si l’utilisateur choisit la commande Fichier Nouveau dans une application SDI, le cadre utilise cette fonction pour réinitialiser le document existant, plutôt que d’en créer une nouvelle. Si l’utilisateur choisit File New dans une application d’interface documentaire multiple (MDI), le cadre crée un nouveau document à chaque fois, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction plutôt que dans le constructeur pour que la commande File New soit efficace dans les applications SDI.

Notez qu’il `OnNewDocument` y a des cas où est appelé deux fois. Cela se produit lorsque le document est intégré comme un serveur de documents ActiveX. La fonction est d’abord appelée `CreateInstance` `COleObjectFactory`par la méthode (exposée par `InitNew` la classe `COleServerDoc`dérivée) et une deuxième fois par la méthode (exposée par la classe dérivée).

### <a name="example"></a>Exemple

Les exemples suivants illustrent d’autres méthodes d’initialisation d’un objet documentaire.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::OnOpenDocument

Appelé par le cadre dans le cadre de la commande File Open.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
Indique le chemin de l’ouverture du document.

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a été chargé avec succès; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction ouvre le fichier spécifié, appelle la fonction membre [DeleteContents](#deletecontents) pour s’assurer que le document est vide, appelle [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour lire le contenu du fichier, puis marque le document comme propre. Remplacez cette fonction si vous souhaitez utiliser autre chose que le mécanisme d’archivage ou le mécanisme de fichier. Par exemple, vous pouvez écrire une application lorsque les documents représentent des enregistrements dans une base de données plutôt que des fichiers distincts.

Si l’utilisateur choisit la commande File Open dans une application SDI, le `CDocument` cadre utilise cette fonction pour réinitialiser l’objet existant, plutôt que de créer un nouveau. Si l’utilisateur choisit File Open dans une application MDI, le cadre construit un nouvel `CDocument` objet à chaque fois, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction plutôt que dans le constructeur pour que la commande File Open soit efficace dans les applications SDI.

### <a name="example"></a>Exemple

Les exemples suivants illustrent d’autres méthodes d’initialisation d’un objet documentaire.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus

Dirige le gestionnaire de prévisualisation pour `GetFocus` retourner le HWND récupéré en appelant la fonction.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Paramètres

*phwnd*<br/>
[out] Lorsque cette méthode revient, contient un pointeur `GetFocus` pour le HWND retourné d’appeler la fonction à partir du fil de premier plan du gestionnaire de prévisualisation.

### <a name="return-value"></a>Valeur de retour

Retours S_OK en cas de succès; ou une valeur d’erreur autrement.

### <a name="remarks"></a>Notes

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator

Dirige le gestionnaire de prévisualisation pour gérer une frappe passée à partir de la pompe de message du processus dans lequel le gestionnaire de prévisualisation est en cours d’exécution.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Paramètres

*pmsg*<br/>
[dans] Un pointeur à un message de fenêtre.

### <a name="return-value"></a>Valeur de retour

Si le message de frappe peut être traité par le gestionnaire de prévisualisation, le gestionnaire le traite et renvoie S_OK. Si le gestionnaire de prévisualisation ne peut pas `IPreviewHandlerFrame::TranslateAccelerator`traiter le message de frappe, il l’offre à l’hôte via . Si l’hôte traite le message, cette méthode renvoie S_OK. Si l’hôte ne traite pas le message, cette méthode renvoie S_FALSE.

### <a name="remarks"></a>Notes

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged

Appelé lorsque la couleur de fond Rich Preview a changé.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged

Appelé lorsque la police Rich Preview a changé.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged

Appelé lorsque le site Rich Preview a changé.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged

Appelé lorsque la couleur du texte Rich Preview a changé.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument

Appelé par le cadre dans le cadre de l’enregistrement de fichier ou de fichier Enregistrer comme commande.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
Indique le chemin entièrement qualifié vers lequel le fichier doit être enregistré.

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a été sauvé avec succès; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction ouvre le fichier spécifié, appelle [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour écrire les données du document au fichier, puis marque le document comme propre. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsque le cadre enregistre un document. Par exemple, vous pouvez écrire une application lorsque les documents représentent des enregistrements dans une base de données plutôt que des fichiers distincts.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler

Appelé par le cadre lorsque le gestionnaire de prévisualisation est déchargé.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Notes

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail

Permet la commande ID_FILE_SEND_MAIL si le support postal (MAPI) est présent.

```cpp
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur de l’objet [CCmdUI](../../mfc/reference/ccmdui-class.md) associé à la commande ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Notes

Dans le cas contraire, la fonction supprime la commande ID_FILE_SEND_MAIL du menu, y compris les séparateurs au-dessus ou en dessous de l’élément de menu, le cas échéant. MAPI est activé si MAPI32. DLL est présent sur le chemin et, dans la section [Mail] du WIN. Fichier INI, MApi-1. La plupart des applications mettent cette commande sur le menu Fichier.

`CDocument`prend en charge l’envoi de votre document par la poste si le support postal (MAPI) est présent. Voir les articles [MAPI Topics](../../mfc/mapi.md) et [MAPI Support in MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame

Cette fonction de membre est appelée par le cadre avant que la fenêtre de cadre soit détruite.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Paramètres

*pFrame (en)*<br/>
Pointeur vers le [CFrameWnd](../../mfc/reference/cframewnd-class.md) qui détient l’objet associé. `CDocument`

### <a name="remarks"></a>Notes

Il peut être remplacé pour fournir un nettoyage personnalisé, mais assurez-vous d’appeler la classe de base ainsi.

Le défaut `PreCloseFrame` de `CDocument`ne fait rien dans . Les `CDocument`classes dérivées [COleDocument](../../mfc/reference/coledocument-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utilisent cette fonction de membre.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue

Lit la valeur suivante de morceau.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Paramètres

*ppValue*<br/>
[out] Lorsque la fonction revient, *ppValue* contient la valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile

Cette fonction de membre est appelée par le cadre pour libérer un fichier, le rendant disponible pour une utilisation par d’autres applications.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Paramètres

*pFile (en)*<br/>
Un pointeur à l’objet CFile à libérer.

*bAbort (en)*<br/>
Précise si le fichier doit être publié `CFile::Close` `CFile::Abort`en utilisant l’un ou l’autre ou . FALSE si le fichier doit être publié à l’aide [de CFile::Close](../../mfc/reference/cfile-class.md#close); VRAI si le fichier doit être publié à l’aide [de CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Notes

Si *bAbort* est `ReleaseFile` `CFile::Abort`VRAI, les appels, et le fichier est publié. `CFile::Abort`ne jettera pas d’exception.

Si *bAbort* est `ReleaseFile` `CFile::Close` FALSE, les appels et le fichier est publié.

Remplacer cette fonction de membre pour exiger une action de l’utilisateur avant la sortie du fichier.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk

Supprime un morceau avec le GUID spécifié.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Paramètres

*Guid*<br/>
Spécifie le GUID d’un morceau à enlever.

*Pid*<br/>
Spécifie la MIP d’un morceau à enlever.

### <a name="remarks"></a>Notes

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView

Appelez cette fonction pour détacher une vue d’un document.

```cpp
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView (en)*<br/>
Points à la vue étant supprimée.

### <a name="remarks"></a>Notes

Cette fonction supprime la vue spécifiée de la liste des vues associées au document; il définit également le pointeur de document de la vue à NULL. Cette fonction est appelée par le cadre lorsqu’une fenêtre de cadre est fermée ou qu’une vitre d’un fendre est fermée.

Appelez cette fonction uniquement si vous détachez manuellement une vue. En règle générale, vous laisserez le cadre détacher les documents et les vues en définissant un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour associer une classe de documents, une classe de vue et une classe de fenêtre de cadre.

Voir l’exemple à [AddView](#addview) pour une mise en œuvre de l’échantillon.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException

Appelé si une exception est lancée (généralement un [CFileException](../../mfc/reference/cfileexception-class.md) ou [CArchiveException](../../mfc/reference/carchiveexception-class.md)) lors de l’enregistrement ou le chargement du document.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
Points au nom du document qui a été enregistré ou chargé.

*E*<br/>
Points à l’exception qui a été jeté. Peut être NULL.

*bSaving (en)*<br/>
Drapeau indiquant quelle opération était en cours; nonzero si le document a été enregistré, 0 si le document était chargé.

*nIDPDefault (en)*<br/>
Identifiant le message d’erreur à afficher si la fonction ne spécifie pas un message plus spécifique.

### <a name="remarks"></a>Notes

L’implémentation par défaut examine l’objet d’exception et recherche un message d’erreur qui décrit spécifiquement la cause. Si un message spécifique n’est pas trouvé ou si *e* est NULL, le message général spécifié par le paramètre *nIDPDefault* est utilisé. La fonction affiche ensuite une boîte de message contenant le message d’erreur. Remplacez cette fonction si vous souhaitez fournir des messages d’échec supplémentaires et personnalisés. C’est un avancé primordial.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::SaveModified

Appelé par le cadre avant qu’un document modifié soit fermé.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Valeur de retour

Nonzero s’il est sécuritaire de continuer et de fermer le document; 0 si le document ne doit pas être fermé.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction affiche une boîte de message demandant à l’utilisateur s’il y a lieu d’enregistrer les modifications apportées au document, le cas échéant. Remplacez cette fonction si votre programme nécessite une procédure d’incitation différente. C’est un avancé primordial.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue

Définit une valeur de morceau.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Spécifie une valeur de morceau à définir.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag

Appelez cette fonction après avoir apporté des modifications au document.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModifié*<br/>
Indicateur indiquant si le document a été modifié.

### <a name="remarks"></a>Notes

En appelant cette fonction de manière cohérente, vous vous assurez que le cadre incite l’utilisateur à enregistrer les modifications avant de fermer un document. En règle générale, vous devez utiliser la valeur par défaut de TRUE pour le paramètre *bModified.* Pour marquer un document comme propre (non modifié), appelez cette fonction avec une valeur de FALSE.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName

Appelez cette fonction pour spécifier le chemin entièrement qualifié du fichier disque du document.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszPathName (en)*<br/>
Points à la chaîne à utiliser comme le chemin pour le document.

*bAddToMRU (en anglais seulement)*<br/>
Détermine si le nom de fichier est ajouté à la liste de fichiers la plus utilisée récemment . Si VRAI, le nom de fichier est ajouté; si FALSE, il n’est pas ajouté.

### <a name="remarks"></a>Notes

Selon la valeur de *bAddToMRU,* le chemin est ajouté, ou non, à la liste MRU maintenue par l’application. Notez que certains documents ne sont pas associés à un fichier disque. Appelez cette fonction uniquement si vous dépassez la implémentation par défaut pour l’ouverture et l’enregistrement des fichiers utilisés par le cadre.

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle

Appelez cette fonction pour spécifier le titre du document (la chaîne affichée dans la barre de titre d’une fenêtre de cadre).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Paramètres

*lpszTitle (lpszTitle)*<br/>
Indique la chaîne à utiliser comme titre du document.

### <a name="remarks"></a>Notes

L’appel de cette fonction met à jour les titres de toutes les fenêtres d’images qui affichent le document.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews

Appelez cette fonction après que le document a été modifié.

```cpp
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Indique l’opinion qui a modifié le document, ou NULL si toutes les vues doivent être mises à jour.

*lHint (en anglais)*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Indique un objet stockant des informations sur la modification.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction après avoir appelé la fonction [membre SetModifiedFlag.](#setmodifiedflag) Cette fonction informe chaque vue jointe au document, à l’exception de la vue spécifiée par *pSender*, que le document a été modifié. Vous appelez généralement cette fonction depuis votre classe de vue après que l’utilisateur a changé le document par le biais d’une vue.

Cette fonction appelle la fonction de membre [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) pour chacune des vues du document, sauf la vue d’envoi, passant *pHint* et *lHint*. Utilisez ces paramètres pour transmettre des informations aux points de vue sur les modifications apportées au document. Vous pouvez coder des informations à *l’aide de lHint* et/ou vous pouvez définir une classe dérivée de [CObject](../../mfc/reference/cobject-class.md)pour stocker des informations sur les modifications et passer un objet de cette classe à l’aide de *pHint*. Remplacez `CView::OnUpdate` la fonction membre dans votre classe dérivée de [CView](../../mfc/reference/cview-class.md)afin d’optimiser la mise à jour de l’affichage de la vue en fonction des informations transmises.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
