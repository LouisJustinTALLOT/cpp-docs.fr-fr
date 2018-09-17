---
title: CDocument, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16f812fc941284122ce2a869786ae73447bff83a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722629"
---
# <a name="cdocument-class"></a>CDocument (classe)
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
|[CDocument::BeginReadChunks](#beginreadchunks)|Initialise segment lecture.|  
|[CDocument::CanCloseFrame](#cancloseframe)|Advanced substituable ; appelé avant la fermeture d’une fenêtre frame affichage de ce document.|  
|[CDocument::ClearChunkList](#clearchunklist)|Efface la liste segment.|  
|[CDocument::ClearPathName](#clearpathname)|Efface le chemin d’accès de l’objet document.|  
|[CDocument::DeleteContents](#deletecontents)|Appelée pour effectuer un nettoyage du document.|  
|[CDocument::FindChunk](#findchunk)|Recherche d’un segment comprenant le GUID spécifié.|  
|[CDocument::GetAdapter](#getadapter)|Retourne un pointeur vers l’objet qui implémente `IDocument` interface.|  
|[CDocument::GetDocTemplate](#getdoctemplate)|Retourne un pointeur vers le modèle de document qui décrit le type du document.|  
|[CDocument::GetFile](#getfile)|Retourne un pointeur vers le texte souhaité `CFile` objet.|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Retourne la position du premier dans la liste des vues ; permet de commencer l’itération.|  
|[CDocument::GetNextView](#getnextview)|Parcourt la liste des vues associée au document.|  
|[CDocument::GetPathName](#getpathname)|Retourne le chemin d’accès du fichier de données du document.|  
|[CDocument::GetThumbnail](#getthumbnail)|Appelée pour créer une image bitmap à être utilisé par le fournisseur de miniatures pour afficher la miniature.|  
|[CDocument::GetTitle](#gettitle)|Retourne le titre du document.|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Appelée pour initialiser le contenu de recherche pour le Gestionnaire de recherche.|  
|[CDocument::IsModified](#ismodified)|Indique si le document a été modifié depuis son dernier enregistrement.|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Indique si cette instance de `CDocument` objet a été créé pour le Gestionnaire d’organiser et de recherche.|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Appelé pour charger les données de document de flux de données.|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Appelé avant la modification de police de l’aperçu détaillé.|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|Appelé après qu’une vue est ajoutée ou supprimée du document.|  
|[CDocument::OnCloseDocument](#onclosedocument)|Appelée pour fermer le document.|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Appelé par l’infrastructure lorsqu’il a besoin créer une image d’aperçu pour l’aperçu riche.|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|Appelé par l’infrastructure en réponse à un événement de document.|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Substituez cette méthode dans une classe dérivée pour dessiner le contenu de miniature.|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Appelé par l’infrastructure lorsqu’il a besoin de charger les données de document de flux de données.|  
|[CDocument::OnNewDocument](#onnewdocument)|Appelée pour créer un nouveau document.|  
|[CDocument::OnOpenDocument](#onopendocument)|Appelé pour ouvrir un document existant.|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Dirige le Gestionnaire d’aperçus pour retourner le HWND de l’appel de la fonction GetFocus.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Dirige le Gestionnaire d’aperçus pour gérer une séquence de touches remontée à partir de la pompe de messages du processus dans lequel le Gestionnaire d’aperçus est en cours d’exécution.|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Appelé lorsque la couleur d’arrière-plan aperçu riche a changé.|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Appelé lorsque la police de l’aperçu détaillé a changé.|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Appelée lorsque le site d’aperçu riche a changé.|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Appelé lorsque la couleur du texte Aperçu riche a changé.|  
|[CDocument::OnSaveDocument](#onsavedocument)|Appelé pour enregistrer le document sur le disque.|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|Appelé par le framework lorsque le Gestionnaire d’aperçus est en cours de déchargement.|  
|[CDocument::PreCloseFrame](#precloseframe)|Appelé avant la fermeture de la fenêtre frame.|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Lit la valeur de segment suivant.|  
|[CDocument::ReleaseFile](#releasefile)|Libère un fichier pour le rendre disponible pour une utilisation par d’autres applications.|  
|[CDocument::RemoveChunk](#removechunk)|Supprime un segment comprenant le GUID spécifié.|  
|[CDocument::RemoveView](#removeview)|Détache une vue à partir du document.|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Advanced substituable ; appelé lorsqu’une ouverture ou l’opération d’enregistrement ne peut pas être effectuée en raison d’une exception.|  
|[CDocument::SaveModified](#savemodified)|Advanced substituable ; appelée pour demander à l’utilisateur si le document doit être enregistré.|  
|[CDocument::SetChunkValue](#setchunkvalue)|Définit une valeur de segment.|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Définit un indicateur indiquant que vous avez modifié le document depuis son dernier enregistrement.|  
|[CDocument::SetPathName](#setpathname)|Définit le chemin d’accès du fichier de données utilisé par le document.|  
|[CDocument::SetTitle](#settitle)|Définit le titre du document.|  
|[CDocument::UpdateAllViews](#updateallviews)|Indique à toutes les vues de document a été modifié.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|Envoie un message électronique avec le document joint.|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Active la commande Envoyer un message si la prise en charge de la messagerie est présent.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Spécifie que `CDocument` objet a été créé par dllhost pour les miniatures. Doit être vérifiée `CView::OnDraw`.|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Spécifie que `CDocument` objet a été créé par prevhost pour `Rich Preview`. Doit être vérifiée `CView::OnDraw`.|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|Spécifie que `CDocument` objet a été créé par l’indexeur ou une autre application de recherche.|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Spécifie la couleur d’arrière-plan de la fenêtre d’aperçu détaillé. Cette couleur est définie par l’hôte.|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Spécifie la couleur de premier plan de la fenêtre d’aperçu détaillé. Cette couleur est définie par l’hôte.|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Spécifie la police du texte de la fenêtre d’aperçu détaillé. Ces informations de police sont définies par l’hôte.|  
  
## <a name="remarks"></a>Notes  
 Un document représente l’unité de données que l’utilisateur s’ouvre avec la commande fichier ouvrir généralement et enregistre avec la commande de l’enregistrement du fichier.  
  
 `CDocument` prend en charge des opérations standards telles que la création d’un document, son chargement et l’enregistrer. Manipule les documents à l’aide de l’interface définie par l’infrastructure `CDocument`.  
  
 Une application peut prendre en charge plusieurs types de document ; par exemple, une application peut prendre en charge des feuilles de calcul et de documents texte. Chaque type de document a un modèle de document associé ; le modèle de document spécifie quelles ressources (par exemple, menu icône, table ou accélérateur) sont utilisés pour ce type de document. Chaque document contient un pointeur vers son associé `CDocTemplate` objet.  
  
 Les utilisateurs interagissent avec un document via le [CView](../../mfc/reference/cview-class.md) ou les objets associés. Une vue restitue une image du document dans une fenêtre frame et interprète les entrées utilisateur en tant qu’opérations sur le document. Un document peut avoir plusieurs vues associées. Lorsque l’utilisateur ouvre une fenêtre sur un document, le framework crée une vue et l’attache au document. Le modèle de document spécifie quel type de vue et frame de fenêtre sont utilisés pour afficher chaque type de document.  
  
 Documents font partie de la norme de l’infrastructure routage des commandes et par conséquent recevoir des commandes à partir des composants d’interface utilisateur standard (par exemple, l’élément de menu d’enregistrement de fichier). Un document reçoit des commandes transmises par la vue active. Si le document ne gère pas une commande donnée, il transfère la commande pour le modèle de document qui le gère.  
  
 Lorsque les données d’un document sont modifiées, chacune de ses vues doit refléter ces modifications. `CDocument` fournit le [UpdateAllViews](#updateallviews) fonction membre pour vous informer les vues de telles modifications, donc les vues se repeindre en fonction des besoins. Le framework invite également à l’utilisateur d’enregistrer un fichier modifié avant sa fermeture.  
  
 Pour implémenter des documents dans une application classique, vous devez procédez comme suit :  
  
-   Dérivez une classe de `CDocument` pour chaque type de document.  
  
-   Ajoutez des variables membres pour stocker les données de chaque document.  
  
-   Implémenter des fonctions de membre pour lire et modifier les données du document. Vues du document sont les utilisateurs plus importantes de ces fonctions membres.  
  
-   Remplacer le [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) fonction membre dans votre classe de document pour écrire et lire les données du document vers et depuis le disque.  
  
 `CDocument` prend en charge l’envoi de votre document par e-mail si la prise en charge de messagerie (MAPI) est présente. Consultez les articles [MAPI](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Pour plus d’informations sur `CDocument`, consultez [sérialisation](../../mfc/serialization-in-mfc.md), [rubriques sur l’Architecture Document/vue](../../mfc/document-view-architecture.md), et [création de Document/vue](../../mfc/document-view-creation.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="addview"></a>  CDocument::AddView  
 Appelez cette fonction pour joindre une vue au document.  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>Paramètres  
 *pView*  
 Pointe vers la vue en cours d’ajout.  
  
### <a name="remarks"></a>Notes  
 Cette fonction ajoute la vue spécifiée à la liste des affichages associés au document ; la fonction définit également le pointeur de document de la vue à ce document. L’infrastructure appelle cette fonction lors de l’attachement d’un objet de vue qui vient d’être créée pour un document ; Cela se produit en réponse à une commande fichier nouveau, ouvrir le fichier ou une nouvelle fenêtre ou quand une fenêtre fractionnée est fractionnée.  
  
 Appelez cette fonction uniquement si vous êtes manuellement création et attachement d’une vue. En général vous permettra l’infrastructure à relier des documents et des vues en définissant un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objet à associer une classe de document, la classe d’affichage et la classe de fenêtre frame.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks  
 Initialise segment lecture.  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame  
 Appelé par l’infrastructure avant la fermeture d’une fenêtre frame affichant le document.  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFrame*  
 Pointe vers la fenêtre frame d’une vue associée au document.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si elle est sécurisée fermer la fenêtre frame ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut vérifie s’il existe d’autres fenêtres frame affichant le document. Si la fenêtre frame spécifié est le dernier qui affiche le document, la fonction invite l’utilisateur à enregistrer le document s’il a été modifié. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’une fenêtre frame est fermée. Il s’agit d’une avancée substituable.  
  
##  <a name="cdocument"></a>  CDocument::CDocument  
 Construit un objet `CDocument`.  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>Notes  
 Le framework gère la création d’un document pour vous. Remplacer le [OnNewDocument](#onnewdocument) fonction membre pour effectuer une initialisation sur une base par document ; cela est particulièrement important dans les applications SDI (interface) de document unique.  
  
##  <a name="clearchunklist"></a>  CDocument::ClearChunkList  
 Efface la liste segment.  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="clearpathname"></a>  CDocument::ClearPathName  
 Efface le chemin d’accès de l’objet document.  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>Notes  
 Effacer le chemin d’accès à partir d’un `CDocument` objet entraîne l’application inviter l’utilisateur lorsque le document est ensuite enregistré. Cela rend une **enregistrer** commande se comportent comme un **Enregistrer sous** commande.  
  
##  <a name="deletecontents"></a>  CDocument::DeleteContents  
 Appelé par l’infrastructure pour supprimer les données du document sans détruire la `CDocument` objet lui-même.  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>Notes  
 Il est appelé juste avant que le document est d’être détruit. Il est également appelée pour vous assurer qu’un document est vide avant qu’il est réutilisé. Cela est particulièrement important pour une application SDI, qui utilise un seul document ; le document est réutilisé chaque fois que l’utilisateur crée ou ouvre un autre document. Appelez cette fonction pour implémenter une « Modifier Effacer tout » ou une commande similaire qui supprime toutes les données du document. L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour supprimer les données dans votre document.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>  CDocument::FindChunk  
 Recherche d’un segment comprenant un GUID spécifié.  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Paramètres  
 *guid*  
 Spécifie le GUID d’un segment à rechercher.  
  
 *pid*  
 Spécifie un PID d’un segment à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Position dans la liste de bloc interne en cas de réussite. Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getadapter"></a>  CDocument::GetAdapter  
 Retourne un pointeur vers un objet qui implémente le `IDocument` interface.  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un objet qui implémente le `IDocument` interface.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate  
 Appelez cette fonction pour obtenir un pointeur vers le modèle de document pour ce type de document.  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le modèle de document pour ce type de document, ou NULL si le document n’est pas géré par un modèle de document.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>  CDocument::GetFile  
 Appelez cette fonction membre pour obtenir un pointeur vers un `CFile` objet.  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszFileName*  
 Chaîne qui est le chemin d’accès au fichier désiré. Le chemin d’accès peut être relatif ou absolu.  
  
 *pError*  
 Pointeur vers un objet d’exception de fichier existant qui indique l’état d’achèvement de l’opération.  
  
 *nOpenFlags*  
 Mode de partage et d’accès. Spécifie l’action à entreprendre lors de l’ouverture du fichier. Vous pouvez combiner les options répertoriées dans le constructeur CFile [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) à l’aide de l’opération OR au niveau du bit (&#124;) opérateur. Autorisation d’un accès et un partage sont requis ; le `modeCreate` et `modeNoInherit` modes sont facultatifs.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CFile` objet.  
  
##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition  
 Appelez cette fonction pour obtenir la position de la première vue dans la liste des vues associée au document.  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur POSITION qui peut être utilisée pour l’itération avec le [GetNextView](#getnextview) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>  CDocument::GetNextView  
 Appelez cette fonction pour effectuer une itération à travers toutes les vues du document.  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rPosition*  
 Une référence à une valeur de la POSITION retournée par un appel précédent à la `GetNextView` ou [GetFirstViewPosition](#getfirstviewposition) fonctions membres. Cette valeur ne doit pas être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la vue identifiée par *rPosition*.  
  
### <a name="remarks"></a>Notes  
 La fonction retourne la vue identifiée par *rPosition* et définit ensuite *rPosition* à la valeur de la POSITION de la vue suivante dans la liste. Si la vue récupérée est le dernier dans la liste, puis *rPosition* est définie sur NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>  CDocument::GetPathName  
 Appelez cette fonction pour obtenir le chemin d’accès qualifié complet du fichier de disque du document.  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chemin d’accès qualifié complet du document. Cette chaîne est vide si le document n’a pas été enregistré ou n’a pas d’un fichier de disque associé.  
  
##  <a name="getthumbnail"></a>  CDocument::GetThumbnail  
 Crée une image bitmap à être utilisé par le fournisseur de miniature pour afficher la miniature.  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>Paramètres  
 *CX*  
 Spécifie la largeur et la hauteur de la bitmap.  
  
 *phbmp*  
 Contient un handle vers une bitmap, lorsque la fonction est retournée avec succès.  
  
 *pdwAlpha*  
 Contient une valeur de DWORD qui spécifie la valeur du canal alpha, lorsque la fonction est retournée avec succès.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si une image bitmap pour la miniature a été créé avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gettitle"></a>  CDocument::GetTitle  
 Appelez cette fonction pour obtenir le titre du document, qui est généralement dérivé de nom de fichier du document.  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le titre du document.  
  
##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent  
 Appelée pour initialiser le contenu de recherche pour le Gestionnaire de recherche.  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour initialiser le contenu de recherche. Le contenu doit être une chaîne avec les parties séparées par « ; ». Par exemple, « pointer ; rectangle ; élément OLE ».  
  
##  <a name="ismodified"></a>  CDocument::IsModified  
 Appelez cette fonction pour déterminer si le document a été modifié depuis son dernier enregistrement.  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document a été modifié depuis son dernier enregistrement ; sinon 0.  
  
##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler  
 Indique si cette instance de `CDocument` a été créé pour le Gestionnaire d’organiser et de recherche.  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si cette instance de `CDocument` a été créé pour le Gestionnaire d’organiser et de recherche.  
  
### <a name="remarks"></a>Notes  
 Actuellement, cette fonction retourne TRUE uniquement pour les gestionnaires d’aperçu riche implémentées dans un serveur hors processus. Vous pouvez définir les indicateurs appropriés (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) au niveau de votre application à rendre cette fonction renvoie la valeur TRUE.  
  
##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream  
 Appelé pour charger des données de document à partir d’un flux de données.  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *pStream*  
 Pointeur vers un flux de données. Ce flux est fourni par l’interpréteur de commandes.  
  
 *dwGrfMode*  
 Mode d’accès dans le flux.  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK si l’opération de chargement réussit, sinon HRESULT avec un code d’erreur.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez substituer cette méthode dans une classe dérivée pour personnaliser comment charger des données à partir du flux.  
  
##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode  
 Spécifie que le `CDocument` objet a été créé par dllhost pour les miniatures. Doit être vérifiée `CView::OnDraw`.  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>Notes  
 `TRUE` Indique que le document a été créé par dllhost pour les miniatures.  
  
##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode  
 Spécifie que le `CDocument` objet a été créé par prevhost pour l’aperçu riche. Doit être vérifiée `CView::OnDraw`.  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>Notes  
 TRUE indique que le document a été créé par prevhost pour l’aperçu riche.  
  
##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode  
 Spécifie que le `CDocument` objet a été créé par l’indexeur ou par une autre application de recherche.  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>Notes  
 `TRUE` Indique que le document a été créé par l’indexeur ou par une autre application de recherche.  
  
##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor  
 Spécifie la couleur d’arrière-plan de la fenêtre d’aperçu détaillé. Cette couleur est définie par l’hôte.  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor  
 Spécifie la couleur de premier plan de la fenêtre d’aperçu détaillé. Cette couleur est définie par l’hôte.  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont  
 Spécifie la police du texte de la fenêtre d’aperçu détaillé. Ces informations de police sont définies par l’hôte.  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged  
 Appelé avant la modification de la police de l’aperçu détaillé.  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList  
 Appelé par le framework après qu’une vue est ajoutée ou supprimée du document.  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction vérifie si la dernière vue est en cours de suppression et, dans ce cas, supprime le document. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de l’infrastructure ajoute ou supprime une vue. Par exemple, si vous souhaitez un document restent ouverts même lorsqu’aucun affichage attaché, remplacez cette fonction.  
  
##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument  
 Appelé par le framework lorsque le document est fermé, dans le cadre de la commande File Close.  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction détruit tous les cadres utilisés pour afficher le document, ferme la vue, nettoie le contenu du document et appelle ensuite la [DeleteContents](#deletecontents) fonction membre à supprimer du document données.  
  
 Remplacez cette fonction si vous souhaitez effectuer un nettoyage spécial traitement lorsque le framework ferme un document. Par exemple, si le document représente un enregistrement dans une base de données, vous souhaiterez substituer cette fonction pour fermer la base de données. Vous devez appeler la version de la classe de base de cette fonction à partir de votre remplacement.  
  
##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame  
 Appelé par l’infrastructure lorsqu’il a besoin créer une image d’aperçu pour l’aperçu riche.  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si le frame est créé avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent  
 Appelé par l’infrastructure en réponse à un événement de document.  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>Paramètres  
*deEvent*<br/>
[in] Type de données énuméré qui décrit le type d’événement.  
  
### <a name="remarks"></a>Notes  
 Événements de document peuvent affecter plusieurs classes. Cette méthode est chargée pour la gestion des événements de document qui affectent les classes autres que la [CDocument (classe)](../../mfc/reference/cdocument-class.md). Actuellement, la seule classe qui doit répondre aux événements de document est la [cdatarecoveryhandler, classe](../../mfc/reference/cdatarecoveryhandler-class.md). Le `CDocument` classe a d’autres méthodes remplaçables chargés de gérer l’effet sur le `CDocument`.  
  
 Le tableau suivant répertorie les valeurs possibles pour *deEvent* et les événements qu’ils correspondent aux.  
  
|Value|Événement correspondant|  
|-----------|-------------------------|  
|`onAfterNewDocument`|Un nouveau document a été créé.|  
|`onAfterOpenDocument`|Un nouveau document a été ouvert.|  
|`onAfterSaveDocument`|Le document a été enregistré.|  
|`onAfterCloseDocument`|Le document a été fermé.|  
  
##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail  
 Substituez cette méthode dans une classe dérivée pour dessiner la miniature.  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>Paramètres  
 *dc*  
 Une référence à un contexte de périphérique.  
  
 *lprcBounds*  
 Spécifie un rectangle englobant de la zone où la miniature doit être dessinée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail  
 Envoie un message par le biais de l’hôte de messagerie résident (le cas échéant) avec le document en tant que pièce jointe.  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>Notes  
 `OnFileSendMail` appels [OnSaveDocument](#onsavedocument) pour sérialiser (des documents sans titre et modifiés dans un fichier temporaire, qui est ensuite envoyé par courrier électronique Enregistrer). Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire ; la version d’origine est envoyée. `OnFileSendMail` charge MAPI32. DLL s’il n’a pas déjà été chargé.  
  
 Une implémentation spéciale de `OnFileSendMail` pour [COleDocument](../../mfc/reference/coledocument-class.md) gère correctement les fichiers composés.  
  
 `CDocument` prend en charge l’envoi de votre document par e-mail si la prise en charge de messagerie (MAPI) est présente. Consultez les articles [MAPI rubriques](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream  
 Appelé par l’infrastructure lorsqu’il a besoin charger les données de document à partir d’un flux de données.  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *pStream*  
 Pointeur vers un flux entrant.  
  
 *grfMode*  
 Mode d’accès dans le flux.  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK si le chargement a réussi ; sinon un code d’erreur.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onnewdocument"></a>  CDocument::OnNewDocument  
 Appelé par l’infrastructure en tant que partie de la commande fichier nouveau.  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document a été initialisé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction appelle le [DeleteContents](#deletecontents) fonction membre pour vous assurer que le document est vide et marque ensuite le nouveau document comme étant propre. Remplacez cette fonction pour initialiser la structure de données pour un nouveau document. Vous devez appeler la version de la classe de base de cette fonction à partir de votre remplacement.  
  
 Si l’utilisateur choisit la commande fichier nouveau dans une application SDI, l’infrastructure utilise cette fonction pour réinitialiser le document existant, au lieu de créer un nouveau. Si l’utilisateur choisit le nouveau fichier dans une application d’interface (multidocument MDI) document, le framework crée un nouveau document chaque fois, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction au lieu de dans le constructeur de la commande fichier nouveau être efficace dans les applications SDI.  
  
 Notez qu’il existe les cas où `OnNewDocument` est appelée deux fois. Cela se produit lorsque le document est incorporé en tant qu’un serveur de documents ActiveX. La fonction est appelée tout d’abord par le `CreateInstance` (méthode) (exposées par le `COleObjectFactory`-classe dérivée) et une deuxième fois par la `InitNew` (méthode) (exposé par le `COleServerDoc`-classe dérivée).  
  
### <a name="example"></a>Exemple  
 Les exemples suivants illustrent d’autres méthodes de l’initialisation d’un objet de document.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>  CDocument::OnOpenDocument  
 Appelé par l’infrastructure en tant que partie de la commande Ouvrir un fichier.  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPathName*  
 Pointe vers le chemin d’accès du document à ouvrir.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document a été chargé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction ouvre le fichier spécifié, appelle le [DeleteContents](#deletecontents) fonction membre pour vous assurer que le document est vide, appelle [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour lire le fichier contenu et marque ensuite le document comme étant propre. Remplacez cette fonction si vous souhaitez utiliser un élément autre que le mécanisme d’archivage ou le fichier. Par exemple, vous pouvez écrire une application où les documents représentent les enregistrements dans une base de données plutôt que des fichiers distincts.  
  
 Si l’utilisateur choisit la commande fichier ouvrir dans une application SDI, l’infrastructure utilise cette fonction pour réinitialiser existant `CDocument` objet, plutôt que de créer un nouveau. Si l’utilisateur choisit ouvrir le fichier dans une application MDI, l’infrastructure construit un nouvel `CDocument` objet chaque fois, puis appelle cette fonction pour l’initialiser. Vous devez placer votre code d’initialisation dans cette fonction au lieu de dans le constructeur de la commande Ouvrir un fichier pour être efficaces dans les applications SDI.  
  
### <a name="example"></a>Exemple  
 Les exemples suivants illustrent d’autres méthodes de l’initialisation d’un objet de document.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus  
 Dirige le Gestionnaire d’aperçus pour retourner le HWND récupérées à partir de l’appel le `GetFocus` (fonction).  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *phwnd*  
 [out] Lorsque cette méthode est retournée, contient un pointeur vers le HWND retourné en appelant le `GetFocus` fonction à partir du thread de premier plan du Gestionnaire d’aperçus.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite ; ou une valeur d’erreur dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator  
 Dirige le Gestionnaire d’aperçus pour gérer une séquence de touches remontée à partir de la pompe de messages du processus dans lequel le Gestionnaire d’aperçus est en cours d’exécution.  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMsg*  
 [in] Pointeur vers un message de fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le message de séquence de touches peut être traité par le Gestionnaire d’aperçus, le gestionnaire traite et retourne S_OK. Si le Gestionnaire d’aperçus ne peut pas traiter le message de séquence de touches, il l’offre à l’hôte via `IPreviewHandlerFrame::TranslateAccelerator`. Si l’hôte traite le message, cette méthode retourne S_OK. Si l’hôte ne traite pas le message, cette méthode retourne S_FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged  
 Appelé lorsque la couleur d’arrière-plan aperçu riche a changé.  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged  
 Appelé lorsque la police de l’aperçu détaillé a changé.  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged  
 Appelée lorsque le site d’aperçu riche a changé.  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged  
 Appelé lorsque la couleur du texte Aperçu riche a changé.  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument  
 Appelé par l’infrastructure en tant que partie de la commande fichier enregistrer ou enregistrer sous.  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPathName*  
 Pointe vers le chemin d’accès qualifié complet à laquelle le fichier doit être enregistré.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document a été enregistré avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction ouvre le fichier spécifié, les appels [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour écrire les données du document pour le fichier et marque le document en tant que nettoyer. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial quand le framework enregistre un document. Par exemple, vous pouvez écrire une application où les documents représentent les enregistrements dans une base de données plutôt que des fichiers distincts.  
  
##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler  
 Appelé par le framework lorsque le Gestionnaire d’aperçus est déchargé.  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail  
 Active la commande ID_FILE_SEND_MAIL si la prise en charge de messagerie (MAPI) est présente.  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers le [CCmdUI](../../mfc/reference/ccmdui-class.md) objet associé à la commande ID_FILE_SEND_MAIL.  
  
### <a name="remarks"></a>Notes  
 Sinon, la fonction supprime la commande ID_FILE_SEND_MAIL dans le menu, y compris les séparateurs au-dessus ou au-dessous de l’élément de menu comme il convient. MAPI est activée si MAPI32. DLL est présent dans le chemin d’accès et, dans la section [Mail] du fichier WIN. Fichier INI, MAPI = 1. La plupart des applications placer cette commande dans le menu fichier.  
  
 `CDocument` prend en charge l’envoi de votre document par e-mail si la prise en charge de messagerie (MAPI) est présente. Consultez les articles [MAPI rubriques](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="precloseframe"></a>  CDocument::PreCloseFrame  
 Cette fonction membre est appelée par l’infrastructure avant la destruction de la fenêtre frame.  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFrame*  
 Pointeur vers le [CFrameWnd](../../mfc/reference/cframewnd-class.md) qui contient le texte associé `CDocument` objet.  
  
### <a name="remarks"></a>Notes  
 Il peut être substituée pour fournir un nettoyage personnalisé, mais veillez à appeler la classe de base.  
  
 La valeur par défaut de `PreCloseFrame` n’a aucun effet `CDocument`. Le `CDocument`-classes dérivées [COleDocument](../../mfc/reference/coledocument-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) utiliser cette fonction membre.  
  
##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue  
 Lit la valeur de segment suivante.  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppValue*  
 [out] Lorsque la fonction retourne, *ppValue* contient la valeur qui a été lu.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="releasefile"></a>  CDocument::ReleaseFile  
 Cette fonction membre est appelée par l’infrastructure pour la mise en production d’un fichier, ce qui rend disponible pour une utilisation par d’autres applications.  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFile*  
 Pointeur vers l’objet CFile soit libéré.  
  
 *bAbort*  
 Spécifie si le fichier doit être libéré à l’aide `CFile::Close` ou `CFile::Abort`. FALSE si le fichier doit être libérée en utilisant [CFile::Close](../../mfc/reference/cfile-class.md#close); TRUE si le fichier doit être libérée en utilisant [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="remarks"></a>Notes  
 Si *bAbort* a la valeur TRUE, `ReleaseFile` appelle `CFile::Abort`, et le fichier est libéré. `CFile::Abort` pas lève une exception.  
  
 Si *bAbort* est FALSE, `ReleaseFile` appels `CFile::Close` et le fichier est libéré.  
  
 Remplacez cette fonction membre pour exiger une action de l’utilisateur avant la publication du fichier.  
  
##  <a name="removechunk"></a>  CDocument::RemoveChunk  
 Supprime un segment comprenant le GUID spécifié.  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Paramètres  
 *Guid*  
 Spécifie le GUID d’un segment à supprimer.  
  
 *PID*  
 Spécifie le PID d’un segment à supprimer.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removeview"></a>  CDocument::RemoveView  
 Appelez cette fonction pour détacher une vue à partir d’un document.  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>Paramètres  
 *pView*  
 Pointe vers la vue en cours de suppression.  
  
### <a name="remarks"></a>Notes  
 Cette fonction supprime la vue spécifiée dans la liste des affichages associés au document ; Il définit également le pointeur de document de la vue avec la valeur NULL. Cette fonction est appelée par l’infrastructure quand une fenêtre frame est fermée ou d’un volet d’une fenêtre fractionnée est fermé.  
  
 Appelez cette fonction uniquement si vous sont détacher manuellement d’une vue. En général vous permettra l’infrastructure à détacher des documents et vues en définissant un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objet à associer une classe de document, la classe d’affichage et la classe de fenêtre frame.  
  
 Consultez l’exemple [AddView](#addview) pour un exemple d’implémentation.  
  
##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException  
 Appelé si une exception est levée (généralement un [CFileException](../../mfc/reference/cfileexception-class.md) ou [exception CArchiveException](../../mfc/reference/carchiveexception-class.md)) pendant l’enregistrement ou chargement du document.  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPathName*  
 Pointe vers le nom du document qui était en cours d’enregistrement ou chargement.  
  
 *e*  
 Points à l’exception qui a été levée. Peut être NULL.  
  
 *benregistrement des*  
 Indicateur qui indique quelle opération était en cours ; différent de zéro si le document a été enregistré, 0 si le document a été chargé.  
  
 *nIDPDefault*  
 Identificateur du message d’erreur à afficher si la fonction ne spécifie pas une valeur plus spécifique.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut examine l’objet exception et recherche un message d’erreur qui décrit précisément la cause. Si un message spécifique est introuvable ou si *e* est NULL, le message général spécifié par le *nIDPDefault* paramètre est utilisé. La fonction puis affiche un message contenant le message d’erreur. Remplacez cette fonction si vous souhaitez fournir des messages d’échec supplémentaire et personnalisé. Il s’agit d’une avancée substituable.  
  
##  <a name="savemodified"></a>  CDocument::SaveModified  
 Appelé par l’infrastructure avant un document modifié est le point d’être fermé.  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si elle est fiable continuer et fermer le document ; 0 si le document ne doit pas être fermé.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction affiche un message demandant à l’utilisateur s’il faut enregistrer les modifications apportées au document, si les ont été apportées. Remplacez cette fonction si votre programme nécessite une autre procédure invite. Il s’agit d’une avancée substituable.  
  
##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue  
 Définit une valeur de segment.  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *pValue*  
 Spécifie une valeur de segment à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag  
 Appelez cette fonction après avoir apporté toutes les modifications au document.  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bModified*  
 Indicateur précisant si le document a été modifié.  
  
### <a name="remarks"></a>Notes  
 En appelant cette fonction de manière cohérente, vous vérifiez que le framework invite l’utilisateur à enregistrer les modifications avant de fermer un document. En général, vous devez utiliser la valeur par défaut True pour le *bModified* paramètre. Pour marquer un document comme nettoyer (non modifié), appelez cette fonction avec la valeur FALSE.  
  
##  <a name="setpathname"></a>  CDocument::SetPathName  
 Appelez cette fonction pour spécifier le chemin d’accès qualifié complet du fichier de disque du document.  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPathName*  
 Pointe vers la chaîne à utiliser en tant que le chemin d’accès pour le document.  
  
 *bAddToMRU*  
 Détermine si le nom de fichier est ajouté à la plus récemment (MRU) liste des fichiers utilisés. Si la valeur est TRUE, le nom de fichier est ajouté ; Si la valeur est FALSE, il n’est pas ajouté.  
  
### <a name="remarks"></a>Notes  
 Selon la valeur de *bAddToMRU* le chemin d’accès est ajouté ou pas ajouté à la liste des derniers fichiers utilisés conservée par l’application. Notez que certains documents ne sont pas associés à un fichier de disque. Appelez cette fonction uniquement si vous substituez l’implémentation par défaut pour ouvrir et enregistrer des fichiers utilisés par l’infrastructure.  
  
##  <a name="settitle"></a>  CDocument::SetTitle  
 Appelez cette fonction pour spécifier le titre du document (la chaîne affichée dans la barre de titre d’une fenêtre frame).  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszTitle*  
 Pointe vers la chaîne à utiliser comme le titre du document.  
  
### <a name="remarks"></a>Notes  
 Appel de cette fonction met à jour les titres de toutes les fenêtres frame qui affichent le document.  
  
##  <a name="updateallviews"></a>  CDocument::UpdateAllViews  
 Appelez cette fonction une fois que le document a été modifié.  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pSender*  
 Pointe vers la vue qui a modifié le document, ou NULL si toutes les vues doivent être mis à jour.  
  
 *lHint*  
 Contient des informations sur la modification.  
  
 *pHint*  
 Pointe vers un objet stockant les informations sur la modification.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler cette fonction après avoir appelé la [SetModifiedFlag](#setmodifiedflag) fonction membre. Cette fonction informe chaque vue associée au document, à l’exception de la vue spécifiée par *pSender*, que le document a été modifié. En général, vous appelez cette fonction à partir de votre classe d’affichage une fois que l’utilisateur a modifié le document via une vue.  
  
 Cette fonction appelle le [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) afficher de la fonction membre pour chacune des vues du document à l’exception de l’envoi, en passant *pHint* et *lHint*. Utilisez ces paramètres pour passer des informations aux vues sur les modifications apportées au document. Vous pouvez encoder à l’aide des informations *lHint* et/ou que vous pouvez définir un [CObject](../../mfc/reference/cobject-class.md)-classe pour stocker des informations sur les modifications et passer un objet de ce à l’aide de la classe dérivée *pHint*. Remplacer le `CView::OnUpdate` fonction membre dans votre [CView](../../mfc/reference/cview-class.md)-classe afin d’optimiser la mise à jour de l’affichage de la vue en fonction des informations passées dérivée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Exemple MFC SNAPVW](../../visual-cpp-samples.md)   
 [Exemple MFC NPP](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)
