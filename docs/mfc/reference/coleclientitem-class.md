---
title: COleClientItem, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleClientItem
- AFXOLE/COleClientItem
- AFXOLE/COleClientItem::COleClientItem
- AFXOLE/COleClientItem::Activate
- AFXOLE/COleClientItem::ActivateAs
- AFXOLE/COleClientItem::AttachDataObject
- AFXOLE/COleClientItem::CanCreateFromData
- AFXOLE/COleClientItem::CanCreateLinkFromData
- AFXOLE/COleClientItem::CanPaste
- AFXOLE/COleClientItem::CanPasteLink
- AFXOLE/COleClientItem::Close
- AFXOLE/COleClientItem::ConvertTo
- AFXOLE/COleClientItem::CopyToClipboard
- AFXOLE/COleClientItem::CreateCloneFrom
- AFXOLE/COleClientItem::CreateFromClipboard
- AFXOLE/COleClientItem::CreateFromData
- AFXOLE/COleClientItem::CreateFromFile
- AFXOLE/COleClientItem::CreateLinkFromClipboard
- AFXOLE/COleClientItem::CreateLinkFromData
- AFXOLE/COleClientItem::CreateLinkFromFile
- AFXOLE/COleClientItem::CreateNewItem
- AFXOLE/COleClientItem::CreateStaticFromClipboard
- AFXOLE/COleClientItem::CreateStaticFromData
- AFXOLE/COleClientItem::Deactivate
- AFXOLE/COleClientItem::DeactivateUI
- AFXOLE/COleClientItem::Delete
- AFXOLE/COleClientItem::DoDragDrop
- AFXOLE/COleClientItem::DoVerb
- AFXOLE/COleClientItem::Draw
- AFXOLE/COleClientItem::GetActiveView
- AFXOLE/COleClientItem::GetCachedExtent
- AFXOLE/COleClientItem::GetClassID
- AFXOLE/COleClientItem::GetClipboardData
- AFXOLE/COleClientItem::GetDocument
- AFXOLE/COleClientItem::GetDrawAspect
- AFXOLE/COleClientItem::GetExtent
- AFXOLE/COleClientItem::GetIconFromRegistry
- AFXOLE/COleClientItem::GetIconicMetafile
- AFXOLE/COleClientItem::GetInPlaceWindow
- AFXOLE/COleClientItem::GetItemState
- AFXOLE/COleClientItem::GetLastStatus
- AFXOLE/COleClientItem::GetLinkUpdateOptions
- AFXOLE/COleClientItem::GetType
- AFXOLE/COleClientItem::GetUserType
- AFXOLE/COleClientItem::IsInPlaceActive
- AFXOLE/COleClientItem::IsLinkUpToDate
- AFXOLE/COleClientItem::IsModified
- AFXOLE/COleClientItem::IsOpen
- AFXOLE/COleClientItem::IsRunning
- AFXOLE/COleClientItem::OnActivate
- AFXOLE/COleClientItem::OnActivateUI
- AFXOLE/COleClientItem::OnChange
- AFXOLE/COleClientItem::OnDeactivate
- AFXOLE/COleClientItem::OnDeactivateUI
- AFXOLE/COleClientItem::OnGetClipboardData
- AFXOLE/COleClientItem::OnInsertMenus
- AFXOLE/COleClientItem::OnRemoveMenus
- AFXOLE/COleClientItem::OnSetMenu
- AFXOLE/COleClientItem::OnShowControlBars
- AFXOLE/COleClientItem::OnUpdateFrameTitle
- AFXOLE/COleClientItem::ReactivateAndUndo
- AFXOLE/COleClientItem::Release
- AFXOLE/COleClientItem::Reload
- AFXOLE/COleClientItem::Run
- AFXOLE/COleClientItem::SetDrawAspect
- AFXOLE/COleClientItem::SetExtent
- AFXOLE/COleClientItem::SetHostNames
- AFXOLE/COleClientItem::SetIconicMetafile
- AFXOLE/COleClientItem::SetItemRects
- AFXOLE/COleClientItem::SetLinkUpdateOptions
- AFXOLE/COleClientItem::SetPrintDevice
- AFXOLE/COleClientItem::UpdateLink
- AFXOLE/COleClientItem::CanActivate
- AFXOLE/COleClientItem::OnChangeItemPosition
- AFXOLE/COleClientItem::OnDeactivateAndUndo
- AFXOLE/COleClientItem::OnDiscardUndoState
- AFXOLE/COleClientItem::OnGetClipRect
- AFXOLE/COleClientItem::OnGetItemPosition
- AFXOLE/COleClientItem::OnGetWindowContext
- AFXOLE/COleClientItem::OnScrollBy
- AFXOLE/COleClientItem::OnShowItem
dev_langs:
- C++
helpviewer_keywords:
- COleClientItem [MFC], COleClientItem
- COleClientItem [MFC], Activate
- COleClientItem [MFC], ActivateAs
- COleClientItem [MFC], AttachDataObject
- COleClientItem [MFC], CanCreateFromData
- COleClientItem [MFC], CanCreateLinkFromData
- COleClientItem [MFC], CanPaste
- COleClientItem [MFC], CanPasteLink
- COleClientItem [MFC], Close
- COleClientItem [MFC], ConvertTo
- COleClientItem [MFC], CopyToClipboard
- COleClientItem [MFC], CreateCloneFrom
- COleClientItem [MFC], CreateFromClipboard
- COleClientItem [MFC], CreateFromData
- COleClientItem [MFC], CreateFromFile
- COleClientItem [MFC], CreateLinkFromClipboard
- COleClientItem [MFC], CreateLinkFromData
- COleClientItem [MFC], CreateLinkFromFile
- COleClientItem [MFC], CreateNewItem
- COleClientItem [MFC], CreateStaticFromClipboard
- COleClientItem [MFC], CreateStaticFromData
- COleClientItem [MFC], Deactivate
- COleClientItem [MFC], DeactivateUI
- COleClientItem [MFC], Delete
- COleClientItem [MFC], DoDragDrop
- COleClientItem [MFC], DoVerb
- COleClientItem [MFC], Draw
- COleClientItem [MFC], GetActiveView
- COleClientItem [MFC], GetCachedExtent
- COleClientItem [MFC], GetClassID
- COleClientItem [MFC], GetClipboardData
- COleClientItem [MFC], GetDocument
- COleClientItem [MFC], GetDrawAspect
- COleClientItem [MFC], GetExtent
- COleClientItem [MFC], GetIconFromRegistry
- COleClientItem [MFC], GetIconicMetafile
- COleClientItem [MFC], GetInPlaceWindow
- COleClientItem [MFC], GetItemState
- COleClientItem [MFC], GetLastStatus
- COleClientItem [MFC], GetLinkUpdateOptions
- COleClientItem [MFC], GetType
- COleClientItem [MFC], GetUserType
- COleClientItem [MFC], IsInPlaceActive
- COleClientItem [MFC], IsLinkUpToDate
- COleClientItem [MFC], IsModified
- COleClientItem [MFC], IsOpen
- COleClientItem [MFC], IsRunning
- COleClientItem [MFC], OnActivate
- COleClientItem [MFC], OnActivateUI
- COleClientItem [MFC], OnChange
- COleClientItem [MFC], OnDeactivate
- COleClientItem [MFC], OnDeactivateUI
- COleClientItem [MFC], OnGetClipboardData
- COleClientItem [MFC], OnInsertMenus
- COleClientItem [MFC], OnRemoveMenus
- COleClientItem [MFC], OnSetMenu
- COleClientItem [MFC], OnShowControlBars
- COleClientItem [MFC], OnUpdateFrameTitle
- COleClientItem [MFC], ReactivateAndUndo
- COleClientItem [MFC], Release
- COleClientItem [MFC], Reload
- COleClientItem [MFC], Run
- COleClientItem [MFC], SetDrawAspect
- COleClientItem [MFC], SetExtent
- COleClientItem [MFC], SetHostNames
- COleClientItem [MFC], SetIconicMetafile
- COleClientItem [MFC], SetItemRects
- COleClientItem [MFC], SetLinkUpdateOptions
- COleClientItem [MFC], SetPrintDevice
- COleClientItem [MFC], UpdateLink
- COleClientItem [MFC], CanActivate
- COleClientItem [MFC], OnChangeItemPosition
- COleClientItem [MFC], OnDeactivateAndUndo
- COleClientItem [MFC], OnDiscardUndoState
- COleClientItem [MFC], OnGetClipRect
- COleClientItem [MFC], OnGetItemPosition
- COleClientItem [MFC], OnGetWindowContext
- COleClientItem [MFC], OnScrollBy
- COleClientItem [MFC], OnShowItem
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43f9e1b342d6de1a93906d2469d0fd1eb211e886
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765003"
---
# <a name="coleclientitem-class"></a>COleClientItem, classe
Définit l'interface du conteneur pour les éléments OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleClientItem : public CDocItem  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleClientItem::COleClientItem](#coleclientitem)|Construit un objet `COleClientItem`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleClientItem::Activate](#activate)|Ouvre l’élément OLE pour une opération, puis exécute le verbe spécifié.|  
|[COleClientItem::ActivateAs](#activateas)|Active l’élément dans un autre type.|  
|[COleClientItem::AttachDataObject](#attachdataobject)|Accède aux données dans l’objet OLE.|  
|[COleClientItem::CanCreateFromData](#cancreatefromdata)|Indique si une application conteneur peut créer un objet incorporé.|  
|[COleClientItem::CanCreateLinkFromData](#cancreatelinkfromdata)|Indique si une application conteneur peut créer un objet lié.|  
|[COleClientItem::CanPaste](#canpaste)|Indique si le Presse-papiers contient un élément OLE intégrable ou statique.|  
|[COleClientItem::CanPasteLink](#canpastelink)|Indique si le Presse-papiers contient un élément OLE pouvant être lié.|  
|[COleClientItem::Close](#close)|Ferme un lien vers un serveur, mais ne détruit pas l’élément OLE.|  
|[COleClientItem::ConvertTo](#convertto)|Convertit l’élément à un autre type.|  
|[COleClientItem::CopyToClipboard](#copytoclipboard)|Copie l’élément OLE dans le Presse-papiers.|  
|[COleClientItem::CreateCloneFrom](#createclonefrom)|Crée un doublon d’un élément existant.|  
|[COleClientItem::CreateFromClipboard](#createfromclipboard)|Crée un élément incorporé à partir du Presse-papiers.|  
|[COleClientItem::CreateFromData](#createfromdata)|Crée un élément incorporé à partir d’un objet de données.|  
|[COleClientItem::CreateFromFile](#createfromfile)|Crée un élément incorporé à partir d’un fichier.|  
|[COleClientItem::CreateLinkFromClipboard](#createlinkfromclipboard)|Crée un élément lié à partir du Presse-papiers.|  
|[COleClientItem::CreateLinkFromData](#createlinkfromdata)|Crée un élément lié à partir d’un objet de données.|  
|[COleClientItem::CreateLinkFromFile](#createlinkfromfile)|Crée un élément lié à partir d’un fichier.|  
|[COleClientItem::CreateNewItem](#createnewitem)|Crée un nouvel élément incorporé en lançant l’application serveur.|  
|[COleClientItem::CreateStaticFromClipboard](#createstaticfromclipboard)|Crée un élément statique à partir du Presse-papiers.|  
|[COleClientItem::CreateStaticFromData](#createstaticfromdata)|Crée un élément statique à partir d’un objet de données.|  
|[COleClientItem::Deactivate](#deactivate)|Désactive l’élément.|  
|[COleClientItem::DeactivateUI](#deactivateui)|Restaure l’interface utilisateur de l’application de conteneur à son état d’origine.|  
|[COleClientItem::Delete](#delete)|Supprime ou ferme l’élément OLE, s’il s’agissait d’un élément lié.|  
|[COleClientItem::DoDragDrop](#dodragdrop)|Effectue une opération de glisser-déplacer.|  
|[COleClientItem::DoVerb](#doverb)|Exécute le verbe spécifié.|  
|[COleClientItem::Draw](#draw)|Dessine l’élément OLE.|  
|[COleClientItem::GetActiveView](#getactiveview)|Obtient la vue sur laquelle l’élément est activé sur place.|  
|[COleClientItem::GetCachedExtent](#getcachedextent)|Retourne les limites du rectangle de l’élément OLE.|  
|[COleClientItem::GetClassID](#getclassid)|Obtient l’ID de classe. de l’élément présent|  
|[COleClientItem::GetClipboardData](#getclipboarddata)|Obtient les données qui seraient placées sur le Presse-papiers en appelant le `CopyToClipboard` fonction membre.|  
|[COleClientItem::GetDocument](#getdocument)|Retourne le `COleDocument` objet qui contient l’élément présent.|  
|[COleClientItem::GetDrawAspect](#getdrawaspect)|Obtient l’affichage actuel de l’élément pour le rendu.|  
|[COleClientItem::GetExtent](#getextent)|Retourne les limites du rectangle de l’élément OLE.|  
|[COleClientItem::GetIconFromRegistry](#geticonfromregistry)|Récupère un handle d’une icône associée au serveur d’un CLSID particulier.|  
|[COleClientItem::GetIconicMetafile](#geticonicmetafile)|Obtient le métafichier utilisé pour dessiner l’icône de l’élément.|  
|[COleClientItem::GetInPlaceWindow](#getinplacewindow)|Retourne un pointeur vers la fenêtre de modification sur place de l’élément.|  
|[COleClientItem::GetItemState](#getitemstate)|Obtient l’état actuel de l’élément.|  
|[COleClientItem::GetLastStatus](#getlaststatus)|Retourne l’état de la dernière opération OLE.|  
|[COleClientItem::GetLinkUpdateOptions](#getlinkupdateoptions)|Retourne le mode de mise à jour pour un élément lié (fonctionnalité avancée).|  
|[COleClientItem::GetType](#gettype)|Retourne le type de l’élément OLE (incorporé, lié ou statique).|  
|[COleClientItem::GetUserType](#getusertype)|Obtient une chaîne décrivant le type de l’élément.|  
|[COleClientItem::IsInPlaceActive](#isinplaceactive)|Retourne la valeur TRUE si l’élément est actif en place.|  
|[COleClientItem::IsLinkUpToDate](#islinkuptodate)|Retourne TRUE si un élément lié est à jour avec son document source.|  
|[COleClientItem::IsModified](#ismodified)|Retourne TRUE si l’élément a été modifié depuis son dernier enregistrée.|  
|[COleClientItem::IsOpen](#isopen)|Retourne TRUE si l’élément est actuellement à ouvrir dans l’application serveur.|  
|[COleClientItem::IsRunning](#isrunning)|Retourne la valeur TRUE si l’application de serveur de l’élément est en cours d’exécution.|  
|[COleClientItem::OnActivate](#onactivate)|Appelé par l’infrastructure pour avertir l’élément qu’il est activé.|  
|[COleClientItem::OnActivateUI](#onactivateui)|Appelé par l’infrastructure pour avertir l’élément qu’il est activé et qu’il doit afficher son interface utilisateur.|  
|[COleClientItem::OnChange](#onchange)|Appelé lorsque le serveur modifie l’élément OLE. Implémentation requis.|  
|[COleClientItem::OnDeactivate](#ondeactivate)|Appelé par l’infrastructure quand un élément est désactivé.|  
|[COleClientItem::OnDeactivateUI](#ondeactivateui)|Appelé par le framework lorsque le serveur a supprimé de son interface utilisateur sur place.|  
|[COleClientItem::OnGetClipboardData](#ongetclipboarddata)|Appelé par l’infrastructure pour obtenir les données à copier dans le Presse-papiers.|  
|[COleClientItem::OnInsertMenus](#oninsertmenus)|Appelé par le framework pour créer un menu composite.|  
|[COleClientItem::OnRemoveMenus](#onremovemenus)|Appelé par l’infrastructure pour supprimer les menus du conteneur à partir d’un menu composite.|  
|[COleClientItem::OnSetMenu](#onsetmenu)|Appelé par l’infrastructure pour installer et supprimer un menu composite.|  
|[COleClientItem::OnShowControlBars](#onshowcontrolbars)|Appelé par l’infrastructure pour afficher et masquer les barres de contrôles.|  
|[COleClientItem::OnUpdateFrameTitle](#onupdateframetitle)|Appelé par l’infrastructure pour mettre à jour de la barre de titre de la fenêtre frame.|  
|[COleClientItem::ReactivateAndUndo](#reactivateandundo)|Réactive de l’élément et annule la dernière opération de modification sur place.|  
|[COleClientItem::Release](#release)|Libère la connexion à un élément lié de OLE et la ferme si elle a été ouverte. Ne détruit pas l’élément client.|  
|[COleClientItem::Reload](#reload)|Recharge l’élément après un appel à `ActivateAs`.|  
|[COleClientItem::Run](#run)|Exécute l’application associée à l’élément.|  
|[COleClientItem::SetDrawAspect](#setdrawaspect)|Définit la vue actuelle de l’élément rendu.|  
|[COleClientItem::SetExtent](#setextent)|Définit le rectangle englobant de l’élément OLE.|  
|[COleClientItem::SetHostNames](#sethostnames)|Définit les noms du serveur affiche quand vous modifiez l’élément OLE.|  
|[COleClientItem::SetIconicMetafile](#seticonicmetafile)|Met en cache le métafichier utilisé pour dessiner l’icône de l’élément.|  
|[COleClientItem::SetItemRects](#setitemrects)|Définit le rectangle englobant de l’élément.|  
|[COleClientItem::SetLinkUpdateOptions](#setlinkupdateoptions)|Définit le mode de mise à jour pour un élément lié (fonctionnalité avancée).|  
|[COleClientItem::SetPrintDevice](#setprintdevice)|Définit le périphérique d’impression pour cet élément de client.|  
|[COleClientItem::UpdateLink](#updatelink)|Met à jour le cache de présentation d’un élément.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[COleClientItem::CanActivate](#canactivate)|Appelé par l’infrastructure pour déterminer si l’activation sur place est autorisée.|  
|[COleClientItem::OnChangeItemPosition](#onchangeitemposition)|Appelé par l’infrastructure lors de la position d’un élément change.|  
|[COleClientItem::OnDeactivateAndUndo](#ondeactivateandundo)|Appelé par l’infrastructure pour l’annuler après l’activation.|  
|[COleClientItem::OnDiscardUndoState](#ondiscardundostate)|Appelé par l’infrastructure pour ignorer les informations d’état annulation de l’élément.|  
|[COleClientItem::OnGetClipRect](#ongetcliprect)|Appelé par l’infrastructure pour obtenir les coordonnées du rectangle de découpage de l’élément.|  
|[COleClientItem::OnGetItemPosition](#ongetitemposition)|Appelé par le framework pour obtenir la position par rapport à la vue.|  
|[COleClientItem::OnGetWindowContext](#ongetwindowcontext)|Appelé par le framework lorsqu’un élément est activé sur place.|  
|[COleClientItem::OnScrollBy](#onscrollby)|Appelé par l’infrastructure pour faire défiler l’élément dans la vue.|  
|[COleClientItem::OnShowItem](#onshowitem)|Appelé par l’infrastructure pour afficher l’élément OLE.|  
  
## <a name="remarks"></a>Notes  
 Un élément OLE représente des données, créés et gérés par une application serveur, qui peut être incorporée « en toute transparence » dans un document afin qu’il apparaisse à l’utilisateur pour être un document unique. Le résultat est un « document composé » de l’élément OLE et un document contenant.  
  
 Un élément OLE peut être incorporé ou lié. S’il est incorporé, ses données sont stockées en tant que partie du document composé. S’il est lié, ses données sont stockées dans le cadre d’un fichier distinct créé par l’application serveur, et uniquement un lien vers ce fichier est stocké dans le document composé. Tous les éléments OLE contiennent des informations en spécifiant l’application serveur qui doit être appelée pour les modifier.  
  
 `COleClientItem` définit plusieurs fonctions substituables qui sont appelées en réponse aux demandes de l’application serveur ; Ces fonctions substituables agissent généralement sous forme de notifications. Cela permet à l’application de serveur pour informer le conteneur de modifications effectuées par l’utilisateur lors de la modification de l’élément OLE ou pour extraire les informations nécessaires lors de l’édition.  
  
 `COleClientItem` peut être utilisé avec le [COleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md), ou [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) classe. Pour utiliser `COleClientItem`, dérivez une classe à partir de celui-ci et implémenter la [OnChange](#onchange) fonction membre, qui définit la manière dont le conteneur répond aux modifications apportées à l’élément. Pour prendre en charge l’activation sur place, vous devez remplacer le [OnGetItemPosition](#ongetitemposition) fonction membre. Cette fonction fournit des informations sur la position affichée de l’élément OLE.  
  
 Pour plus d’informations sur l’utilisation de l’interface du conteneur, consultez les articles [conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md) et [Activation](../../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Le Kit de développement logiciel Windows fait référence à des éléments liés et incorporés en tant que « objets » et fait référence aux types d’éléments en tant que « classes ». Cette référence utilise le terme « item » pour l’entité OLE distinguer de l’objet C++ correspondant et le terme « type » pour distinguer la catégorie OLE à partir de la classe C++.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="activate"></a>  COleClientItem::Activate  
 Appelez cette fonction pour exécuter le verbe spécifié à la place de [DoVerb](#doverb) afin que vous pouvez effectuer votre propre traitement lorsqu’une exception est levée.  
  
```  
void Activate(
    LONG nVerb,  
    CView* pView,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVerb*  
 Spécifie le verbe à exécuter. Il peut avoir l'une des valeurs suivantes :  
  
|Value|Signification|Symbole|  
|-----------|-------------|------------|  
|- 0|Primary (verbe)|OLEIVERB_PRIMARY|  
|- 1|Verbe secondaire|(Aucun)|  
|- 1|Élément d’affichage pour la modification|OLEIVERB_SHOW|  
|- 2|Modifier l’élément dans une fenêtre distincte|OLEIVERB_OPEN|  
|- 3|Masquer l’élément|OLEIVERB_HIDE|  
  
 La valeur-1 est généralement un alias pour un autre verbe. Si la modification ouvert n’est pas prise en charge, -2 a le même effet que -1. Pour connaître les valeurs supplémentaires, consultez [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.  
  
 *pView*  
 Pointeur vers la fenêtre de vue du conteneur qui contient l’élément OLE ; Cela est utilisé par l’application serveur pour l’activation sur place. Ce paramètre doit être NULL si le conteneur ne prend pas en charge l’activation sur place.  
  
 *lpMsg*  
 Pointeur vers le message qui a provoqué l’élément à être activé.  
  
### <a name="remarks"></a>Notes  
 Si l’application serveur ait été écrit à l’aide de la bibliothèque Microsoft Foundation Class, cette fonction provoque la [OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb) fonction membre correspondante `COleServerItem` objet doit être exécuté.  
  
 Si le verbe principal est Edit et zéro est spécifié dans le *nVerb* paramètre, l’application serveur est lancée pour autoriser l’élément OLE à modifier. Si l’application conteneur prend en charge l’activation sur place, modification peut être effectuée en place. Si le conteneur ne prend pas en charge l’activation sur place (ou si le verbe Open est spécifié), le serveur est lancé dans une fenêtre distincte et modification permettre être effectuée. En règle générale, lorsque l’utilisateur de l’application de conteneur double-clique sur l’élément OLE, la valeur pour le verbe principal dans le *nVerb* paramètre détermine quelle action l’utilisateur peut prendre. Toutefois, si le serveur prend en charge une seule action, il prend cette action, quel que soit ce qui est spécifiée dans le *nVerb* paramètre.  
  
 Pour plus d’informations, consultez [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.  
  
##  <a name="activateas"></a>  COleClientItem::ActivateAs  
 Utilise les fonctions de conversion d’objets OLE pour activer l’élément comme s’il s’agissait d’un élément du type spécifié par *clsidNew*.  
  
```  
virtual BOOL ActivateAs(
    LPCTSTR lpszUserType,  
    REFCLSID clsidOld,  
    REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszUserType*  
 Pointeur vers une chaîne représentant le type d’utilisateur cible, telles que « Document Word. »  
  
 *clsidOld*  
 ID une référence à la classe en cours de l’élément d'. L’ID de classe doit représenter le type de l’objet réel, tel que stocké, sauf s’il est un lien. Dans ce cas, il doit être le CLSID de l’élément auquel le lien fait référence. Le [classe COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md) fournit automatiquement l’ID de classe approprié pour l’élément.  
  
 *clsidNew*  
 Une référence à l’ID de classe cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cela est appelé automatiquement par [COleConvertDialog::DoConvert](../../mfc/reference/coleconvertdialog-class.md#doconvert). Il n'est pas généralement appelée directement.  
  
##  <a name="attachdataobject"></a>  COleClientItem::AttachDataObject  
 Appelez cette fonction pour initialiser un [COleDataObject](../../mfc/reference/coledataobject-class.md) pour accéder aux données dans l’élément OLE.  
  
```  
void AttachDataObject(COleDataObject& rDataObject) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rDataObject*  
 Référence à un `COleDataObject` objet sera initialisée pour autoriser l’accès aux données dans l’élément OLE.  
  
##  <a name="canactivate"></a>  COleClientItem::CanActivate  
 Appelé par le framework lorsque l’utilisateur demande l’activation sur place de l’élément OLE ; valeur de retour de cette fonction détermine si l’activation sur place est autorisée.  
  
```  
virtual BOOL CanActivate();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’activation sur place est autorisée ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut permet l’activation sur place si le conteneur possède une fenêtre valide. Remplacez cette fonction pour implémenter une logique spéciale accepte ou refuse la demande d’activation. Par exemple, une demande d’activation peut être refusée si l’élément OLE est trop petite ou pas actuellement visible.  
  
 Pour plus d’informations, consultez [IOleInPlaceSite::CanInPlaceActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplacesite-caninplaceactivate) dans le SDK Windows.  
  
##  <a name="cancreatefromdata"></a>  COleClientItem::CanCreateFromData  
 Vérifie si une application conteneur peut créer un objet incorporé à partir de la donnée `COleDataObject` objet.  
  
```  
static BOOL PASCAL CanCreateFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) objet à partir duquel l’élément OLE doit être créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le conteneur peut créer un objet incorporé à partir de la `COleDataObject` objet ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le `COleDataObject` classe est utilisée dans les transferts de données pour récupérer des données dans différents formats à partir du Presse-papiers, par glisser- déposer, ou à partir d’un élément OLE incorporé.  
  
 Conteneurs peuvent utiliser cette fonction pour décider activer ou désactiver leurs commandes d’édition coller et modifier le collage spécial.  
  
 Pour plus d’informations, consultez l’article [objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
##  <a name="cancreatelinkfromdata"></a>  COleClientItem::CanCreateLinkFromData  
 Vérifie si une application conteneur peut créer un objet lié à partir de la donnée `COleDataObject` objet.  
  
```  
static BOOL PASCAL CanCreateLinkFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) objet à partir duquel l’élément OLE doit être créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le conteneur peut créer un objet lié à partir de la `COleDataObject` objet.  
  
### <a name="remarks"></a>Notes  
 Le `COleDataObject` classe est utilisée dans les transferts de données pour récupérer des données dans différents formats à partir du Presse-papiers, par glisser- déposer, ou à partir d’un élément OLE incorporé.  
  
 Conteneurs peuvent utiliser cette fonction pour décider activer ou désactiver leurs commandes modifier Collage spécial et modifier le lien coller.  
  
 Pour plus d’informations, consultez l’article [objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
##  <a name="canpaste"></a>  COleClientItem::CanPaste  
 Appelez cette fonction pour voir si un élément OLE incorporé peut être collé à partir du Presse-papiers.  
  
```  
static BOOL PASCAL CanPaste();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un élément OLE incorporé peut être collé à partir du Presse-papiers ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [OleGetClipboard](/windows/desktop/api/ole2/nf-ole2-olegetclipboard) et [OleQueryCreateFromData](/windows/desktop/api/ole2/nf-ole2-olequerycreatefromdata) dans le SDK Windows.  
  
##  <a name="canpastelink"></a>  COleClientItem::CanPasteLink  
 Appelez cette fonction pour voir si un élément OLE lié peut être collé à partir du Presse-papiers.  
  
```  
static BOOL PASCAL CanPasteLink();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un élément OLE lié peut être collé à partir du Presse-papiers ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [OleGetClipboard](/windows/desktop/api/ole2/nf-ole2-olegetclipboard) et [OleQueryLinkFromData](/windows/desktop/api/ole2/nf-ole2-olequerylinkfromdata) dans le SDK Windows.  
  
##  <a name="close"></a>  COleClientItem::Close  
 Appelez cette fonction pour modifier l’état d’un élément OLE à partir de l’état en cours d’exécution à l’état chargé, autrement dit, chargée avec son gestionnaire en mémoire, mais le serveur ne fonctionne ne pas.  
  
```  
void Close(OLECLOSE dwCloseOption = OLECLOSE_SAVEIFDIRTY);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwCloseOption*  
 Indicateur qui spécifie dans quelles circonstances l’élément OLE est enregistré quand elle retourne à l’état chargé. Il peut avoir l’une des valeurs suivantes :  
  
- Élément OLECLOSE_SAVEIFDIRTY enregistrer le OLE.  
  
- OLECLOSE_NOSAVE ne pas enregistrer l’élément OLE.  
  
- OLECLOSE_PROMPTSAVE invite l’utilisateur si vous souhaitez enregistrer l’élément OLE.  
  
### <a name="remarks"></a>Notes  
 Cette fonction n’a aucun effet lorsque l’élément OLE ne fonctionne pas.  
  
 Pour plus d’informations, consultez [IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) dans le SDK Windows.  
  
##  <a name="coleclientitem"></a>  COleClientItem::COleClientItem  
 Construit un `COleClientItem` de l’objet et l’ajoute à la collection du document conteneur d’éléments de document, qui construit uniquement l’objet C++ et n’effectue pas de toute initialisation OLE.  
  
```  
COleClientItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pContainerDoc*  
 Pointeur vers le document conteneur qui contiendra cet élément. Il peut s’agir d’un [COleDocument](../../mfc/reference/coledocument-class.md) dérivé.  
  
### <a name="remarks"></a>Notes  
 Si vous passez un pointeur NULL, aucun ajout n’est effectuée pour le document conteneur. Vous devez appeler explicitement [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem).  
  
 Vous devez appeler une des fonctions de membre de création suivantes avant d’utiliser l’élément OLE :  
  
- [CreateFromClipboard](#createfromclipboard)  
  
- [CreateFromData](#createfromdata)  
  
- [CreateFromFile](#createfromfile)  
  
- [CreateStaticFromClipboard](#createstaticfromclipboard)  
  
- [CreateStaticFromData](#createstaticfromdata)  
  
- [CreateLinkFromClipboard](#createlinkfromclipboard)  
  
- [CreateLinkFromData](#createlinkfromdata)  
  
- [CreateLinkFromFile](#createlinkfromfile)  
  
- [CreateNewItem](#createnewitem)  
  
- [CreateCloneFrom](#createclonefrom)  
  
##  <a name="convertto"></a>  COleClientItem::ConvertTo  
 Appelez cette fonction membre pour convertir le type spécifié par l’élément *clsidNew*.  
  
```  
virtual BOOL ConvertTo(REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>Paramètres  
 *clsidNew*  
 L’ID de classe du type cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cela est appelé automatiquement par [classe COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md). Il n’est pas nécessaire d’appeler directement.  
  
##  <a name="copytoclipboard"></a>  COleClientItem::CopyToClipboard  
 Appelez cette fonction pour copier l’élément OLE dans le Presse-papiers.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bIncludeLink*  
 TRUE si les informations de lien doivent être copiées dans le Presse-papiers, ce qui permet un élément lié être collé ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous appelez cette fonction lors de l’écriture de gestionnaires de messages pour les commandes copier ou Couper dans le menu Edition. Vous devez implémenter la sélection d’éléments dans votre application conteneur si vous souhaitez implémenter les commandes copier ou Couper.  
  
 Pour plus d’informations, consultez [OleSetClipboard](/windows/desktop/api/ole2/nf-ole2-olesetclipboard) dans le SDK Windows.  
  
##  <a name="createclonefrom"></a>  COleClientItem::CreateCloneFrom  
 Appelez cette fonction pour créer une copie de l’élément OLE spécifié.  
  
```  
BOOL CreateCloneFrom(const COleClientItem* pSrcItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pSrcItem*  
 Pointeur vers l’élément OLE à dupliquer.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La copie est identique à l’élément source. Vous pouvez utiliser cette fonction pour prendre en charge les opérations d’annulation.  
  
##  <a name="createfromclipboard"></a>  COleClientItem::CreateFromClipboard  
 Appelez cette fonction pour créer un élément incorporé à partir du contenu du Presse-papiers.  
  
```  
BOOL CreateFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous appelez cette fonction à partir du Gestionnaire de message pour la commande Coller dans le menu Edition. (La commande Coller est activée par le framework si la [CanPaste](#canpaste) fonction membre retourne une valeur différente de zéro.)  
  
 Pour plus d’informations, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createfromdata"></a>  COleClientItem::CreateFromData  
 Appelez cette fonction pour créer un élément incorporé à partir d’un `COleDataObject` objet.  
  
```  
BOOL CreateFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) objet à partir duquel l’élément OLE doit être créé.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Fournissent des opérations de transfert de données, telles que collage à partir du Presse-papiers ou les opérations de glisser-déplacer, `COleDataObject` objets contenant les informations offertes par une application serveur. Il est généralement utilisé dans votre substitution de [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop).  
  
 Pour plus d’informations, consultez [OleCreateFromData](/windows/desktop/api/ole2/nf-ole2-olecreatefromdata), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createfromfile"></a>  COleClientItem::CreateFromFile  
 Appelez cette fonction pour créer un élément OLE incorporé à partir d’un fichier.  
  
```  
BOOL CreateFromFile(
    LPCTSTR lpszFileName,  
    REFCLSID clsid = CLSID_NULL,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszFileName*  
 Pointeur vers le nom du fichier à partir duquel l’élément OLE doit être créé.  
  
 *clsid*  
 Réservé à un usage ultérieur.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction à partir de [COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem) si l’utilisateur choisit OK à partir de la boîte de dialogue Insérer un objet lorsque l’à partir d’un bouton de fichier est sélectionné.  
  
 Pour plus d’informations, consultez [OleCreateFromFile](/windows/desktop/api/ole/nf-ole-olecreatefromfile), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createlinkfromclipboard"></a>  COleClientItem::CreateLinkFromClipboard  
 Appelez cette fonction pour créer un élément lié à partir du contenu du Presse-papiers.  
  
```  
BOOL CreateLinkFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous appelez cette fonction à partir du Gestionnaire de message pour la commande Coller la liaison dans le menu Edition. (La commande Coller la liaison est activée dans l’implémentation par défaut de [COleDocument](../../mfc/reference/coledocument-class.md) si le Presse-papiers contient un élément OLE qui peut être lié à.)  
  
 Pour plus d’informations, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createlinkfromdata"></a>  COleClientItem::CreateLinkFromData  
 Appelez cette fonction pour créer un élément lié à partir d’un `COleDataObject` objet.  
  
```  
BOOL CreateLinkFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) objet à partir duquel l’élément OLE doit être créé.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appeler pendant une opération de déplacement lorsque l’utilisateur indique un lien doit être créé. Il peut également servir à gérer la commande Coller modifier. Elle est appelée par l’infrastructure dans `COleClientItem::CreateLinkFromClipboard` et dans [COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem) lorsque l’option de liaison a été sélectionnée.  
  
 Pour plus d’informations, consultez [OleCreateLinkFromData](/windows/desktop/api/ole2/nf-ole2-olecreatelinkfromdata), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createlinkfromfile"></a>  COleClientItem::CreateLinkFromFile  
 Appelez cette fonction pour créer un élément OLE lié à partir d’un fichier.  
  
```  
BOOL CreateLinkFromFile(
    LPCTSTR lpszFileName,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszFileName*  
 Pointeur vers le nom du fichier à partir duquel l’élément OLE doit être créé.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction si l’utilisateur choisit OK à partir de la boîte de dialogue Insérer un objet lorsque l’à partir d’un bouton de fichier est sélectionné et le lien case à cocher est activée. Elle est appelée à partir de [COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem).  
  
 Pour plus d’informations, consultez [OleCreateLinkToFile](/windows/desktop/api/ole2/nf-ole2-olecreatelinktofile), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createnewitem"></a>  COleClientItem::CreateNewItem  
 Appelez cette fonction pour créer un élément incorporé ; Cette fonction lance l’application serveur qui permet à l’utilisateur créer l’élément OLE.  
  
```  
BOOL CreateNewItem(
    REFCLSID clsid,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 ID qui identifie de façon unique le type d’élément OLE à créer.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction si l’utilisateur choisit OK à partir de la boîte de dialogue Insérer un objet lorsque le bouton Créer est sélectionné.  
  
 Pour plus d’informations, consultez [OleCreate](/windows/desktop/api/ole/nf-ole-olecreate), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createstaticfromclipboard"></a>  COleClientItem::CreateStaticFromClipboard  
 Appelez cette fonction pour créer un élément statique à partir du contenu du Presse-papiers.  
  
```  
BOOL CreateStaticFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un élément statique contient les données de présentation, mais pas les données natives ; Par conséquent il ne peut pas être modifié. En règle générale, vous appelez cette fonction si le [CreateFromClipboard](#createfromclipboard) fonction membre échoue.  
  
 Pour plus d’informations, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="createstaticfromdata"></a>  COleClientItem::CreateStaticFromData  
 Appelez cette fonction pour créer un élément statique à partir d’un `COleDataObject` objet.  
  
```  
BOOL CreateStaticFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) objet à partir duquel l’élément OLE doit être créé.  
  
 *Rendu*  
 Indicateur qui spécifie comment le serveur affiche l’élément OLE. Pour les valeurs possibles, consultez [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender) dans le SDK Windows.  
  
 *cfFormat*  
 Spécifie le format de données du Presse-papiers doit être mis en cache lors de la création de l’élément OLE.  
  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure utilisée si *restituer* est OLERENDER_FORMAT ou OLERENDER_DRAW. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si vous omettez ce paramètre, les valeurs par défaut sont utilisées pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un élément statique contient les données de présentation, mais pas les données natives ; Par conséquent, il ne peut pas être modifié. Il s’agit essentiellement le même que [CreateStaticFromClipboard](#createstaticfromclipboard) , à ceci près qu’un élément statique peut être créé à partir d’une commande arbitraire `COleDataObject`, pas seulement à partir du Presse-papiers.  
  
 Utilisé dans [COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem) lorsque statique est sélectionné.  
  
 Pour plus d’informations, consultez [OleCreateStaticFromData](/windows/desktop/api/ole2/nf-ole2-olecreatestaticfromdata), [OLERENDER](/windows/desktop/api/oleidl/ne-oleidl-tagolerender), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
##  <a name="deactivate"></a>  COleClientItem::Deactivate  
 Appelez cette fonction pour désactiver l’élément OLE et libérer toutes les ressources associées.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Notes  
 En général, vous désactivez un élément OLE sur place actif lorsque l’utilisateur clique sur la souris sur la zone cliente en dehors des limites de l’élément. Notez que la désactivation de l’élément OLE ignore son état d’annulation, ce qui empêche d’appeler le [ReactivateAndUndo](#reactivateandundo) fonction membre.  
  
 Si votre application prend en charge l’annulation, n’appelez pas `Deactivate`; au lieu de cela, appelez [DeactivateUI](#deactivateui).  
  
 Pour plus d’informations, consultez [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) dans le SDK Windows.  
  
##  <a name="deactivateui"></a>  COleClientItem::DeactivateUI  
 Appelez cette fonction lorsque l’utilisateur désactive un élément qui a été activé sur place.  
  
```  
void DeactivateUI();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction restaure l’interface utilisateur de l’application de conteneur à son état d’origine, masquage des menus et autres contrôles qui ont été créés pour l’activation sur place.  
  
 Cette fonction ne vide pas les informations d’état annulation pour l’élément. Que les informations sont conservées afin que [ReactivateAndUndo](#reactivateandundo) peuvent être utilisées ultérieurement pour exécuter une commande d’annulation dans l’application serveur, en cas de commande d’annulation du conteneur est choisie immédiatement après la désactivation de l’élément.  
  
 Pour plus d’informations, consultez [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) dans le SDK Windows.  
  
##  <a name="delete"></a>  COleClientItem::Delete  
 Appelez cette fonction pour supprimer l’élément OLE à partir du document conteneur.  
  
```  
void Delete(BOOL bAutoDelete = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAutoDelete*  
 Spécifie si l’élément doit être supprimé du document.  
  
### <a name="remarks"></a>Notes  
 Cette fonction appelle le [version](#release) fonction membre, ce qui à son tour supprime l’objet C++ pour l’élément, et supprime définitivement l’élément OLE à partir du document. Si l’élément OLE est incorporé, les données natives pour l’élément sont supprimées. Il ferme toujours un serveur en cours d’exécution ; Par conséquent, si l’élément est d’ouvrir le lien, cette fonction le ferme.  
  
##  <a name="dodragdrop"></a>  COleClientItem::DoDragDrop  
 Appelez le `DoDragDrop` fonction membre pour effectuer une opération de glisser-déplacer.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpItemRect,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpItemRect*  
 Rectangle de l’élément sur l’écran en coordonnées clientes (pixels).  
  
 *ptOffset*  
 Le décalage à partir de *lpItemRect* où la position de la souris était au moment de l’opération glisser.  
  
 *bIncludeLink*  
 Affectez la valeur TRUE si la liaison de données doivent être copiées dans le Presse-papiers. Affectez-lui la valeur FALSE si votre application serveur ne prend pas en charge les liens.  
  
 *dwEffects*  
 Détermine les effets de la source de glissement autorisera dans l’opération glisser.  
  
 *lpRectStartDrag*  
 Pointeur vers le rectangle qui définit où commence l’opération glisser. Pour plus d'informations, consultez la section Notes qui suit.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur DROPEFFECT. Si elle est DROPEFFECT_MOVE, les données d’origine doivent être supprimées.  
  
### <a name="remarks"></a>Notes  
 L’opération de glisser-déplacer ne démarre pas immédiatement. Il attend que le curseur de la souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu'à ce qu’un nombre spécifié de millisecondes écoulées. Si *lpRectStartDrag* est NULL, la taille du rectangle est un pixel.  
  
 Le délai spécifié par un paramètre de clé de Registre. Vous pouvez modifier le temps de retard en appelant [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas le temps de retard, 200 millisecondes comme valeur par défaut est utilisée. Faites glisser retarder l’heure est stockée comme suit :  
  
-   Retarder l’heure de glissement de Windows NT est stocké dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Retarder l’heure de Windows 3.x glisser est stockée dans le fichier WIN. Fichier INI, la section [Windows}.  
  
-   Retarder l’heure de Windows 95/98 glisser est stockée dans une version de WIN. INI.  
  
 Pour plus d’informations sur la façon faites glisser les informations de retard sont stockées dans le Registre ou le. Fichier INI, consultez [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) dans le SDK Windows.  
  
##  <a name="doverb"></a>  COleClientItem::DoVerb  
 Appelez `DoVerb` pour exécuter le verbe spécifié.  
  
```  
virtual BOOL DoVerb(
    LONG nVerb,  
    CView* pView,
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVerb*  
 Spécifie le verbe à exécuter. Il peut inclure un des éléments suivants :  
  
|Value|Signification|Symbole|  
|-----------|-------------|------------|  
|- 0|Primary (verbe)|OLEIVERB_PRIMARY|  
|- 1|Verbe secondaire|(Aucun)|  
|- 1|Élément d’affichage pour la modification|OLEIVERB_SHOW|  
|- 2|Modifier l’élément dans une fenêtre distincte|OLEIVERB_OPEN|  
|- 3|Masquer l’élément|OLEIVERB_HIDE|  
  
 La valeur-1 est généralement un alias pour un autre verbe. Si la modification ouvert n’est pas prise en charge, -2 a le même effet que -1. Pour connaître les valeurs supplémentaires, consultez [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.  
  
 *pView*  
 Pointeur vers la fenêtre d’affichage ; Cela est utilisé par le serveur pour l’activation sur place. Ce paramètre doit être NULL si l’application de conteneur n’autorise pas l’activation sur place.  
  
 *lpMsg*  
 Pointeur vers le message qui a provoqué l’élément à être activé.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le verbe a été exécuté avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction appelle le [activer](#activate) fonction membre pour exécuter le verbe. Également, il intercepte les exceptions et affiche une boîte de message pour l’utilisateur si une exception est levée.  
  
 Si le verbe principal est Edit et zéro est spécifié dans le *nVerb* paramètre, l’application serveur est lancée pour autoriser l’élément OLE à modifier. Si l’application conteneur prend en charge l’activation sur place, modification peut être effectuée en place. Si le conteneur ne prend pas en charge l’activation sur place (ou si le verbe Open est spécifié), le serveur est lancé dans une fenêtre distincte et modification permettre être effectuée. En règle générale, lorsque l’utilisateur de l’application de conteneur double-clique sur l’élément OLE, la valeur pour le verbe principal dans le *nVerb* paramètre détermine quelle action l’utilisateur peut prendre. Toutefois, si le serveur prend en charge une seule action, il prend cette action, quel que soit ce qui est spécifiée dans le *nVerb* paramètre.  
  
##  <a name="draw"></a>  COleClientItem::Draw  
 Appelez cette fonction pour dessiner l’élément OLE dans le rectangle englobant spécifié en utilisant le contexte de périphérique spécifié.  
  
```  
BOOL Draw(
    CDC* pDC,  
    LPCRECT lpBounds,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Pointeur vers un [CDC](../../mfc/reference/cdc-class.md) objet utilisé pour dessiner l’élément OLE.  
  
 *lpBounds*  
 Pointeur vers un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou `RECT` structure qui définit le rectangle englobant dans lequel dessiner l’élément OLE (en unités logiques déterminées par le contexte de périphérique).  
  
 *nDrawAspect*  
 Spécifie l’aspect de l’OLE de l’élément, autrement dit, comment il doit s’afficher. Si *nDrawAspect* est -1, le dernier aspect défini à l’aide [SetDrawAspect](#setdrawaspect) est utilisé. Pour plus d’informations sur les valeurs possibles pour cet indicateur, consultez [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La fonction peut utiliser la représentation sous forme de métafichier de l’élément OLE créé par le [OnDraw](../../mfc/reference/coleserveritem-class.md#ondraw) fonction membre de `COleServerItem`.  
  
 En général vous utilisez `Draw` pour afficher l’écran, en passant le contexte de périphérique en tant que *pDC*. Dans ce cas, vous devez spécifier uniquement les deux premiers paramètres.  
  
 Le *lpBounds* paramètre identifie le rectangle dans le contexte de périphérique cible (par rapport à son mode de mappage en cours). Le rendu peut impliquer la mise à l’échelle de l’image et utilisable par les applications de conteneur pour imposer une vue qui évolue entre l’affichage et l’image finale.  
  
 Pour plus d’informations, consultez [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) dans le SDK Windows.  
  
##  <a name="getactiveview"></a>  COleClientItem::GetActiveView  
 Retourne la vue sur laquelle l’élément est activé sur place.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la vue ; Sinon, NULL si l’élément n’est pas activé sur place.  
  
##  <a name="getcachedextent"></a>  COleClientItem::GetCachedExtent  
 Appelez cette fonction pour extraire la taille de l’élément OLE.  
  
```  
BOOL GetCachedExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpSize*  
 Pointeur vers un `SIZE` structure ou un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui recevra les informations de taille.  
  
 *nDrawAspect*  
 Spécifie l’aspect de l’élément OLE dont les limites doivent être récupérés. Pour connaître les valeurs possibles, consultez [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; 0 si l’élément OLE est vide.  
  
### <a name="remarks"></a>Notes  
 Cette fonction fournit les mêmes informations que [GetExtent](#getextent). Toutefois, vous pouvez appeler `GetCachedExtent` pour obtenir des informations de mesure pendant le traitement des autres gestionnaires OLE, tel que [OnChange](#onchange). Les dimensions sont exprimées en unités MM_HIMETRIC.  
  
 Cela est possible, car `GetCachedExtent` utilise le [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2) interface au lieu d’utiliser le [IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject) interface permettant d’obtenir l’étendue de cet élément. Le `IViewObject2` objet COM met en cache les informations de mesure utilisées dans l’appel précédent à [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw).  
  
 Pour plus d’informations, consultez [IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) dans le SDK Windows.  
  
##  <a name="getclassid"></a>  COleClientItem::GetClassID  
 Retourne l’ID de classe de l’élément dans la mémoire vers laquelle pointée *pClassID*.  
  
```  
void GetClassID(CLSID* pClassID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pClassID*  
 Pointeur vers un identificateur de type [CLSID](/windows/desktop/com/clsid-key-hklm) pour récupérer l’ID de classe. Pour plus d’informations sur les CLSID, consultez le Kit de développement Windows.  
  
### <a name="remarks"></a>Notes  
 L’ID de classe est un nombre de 128 bits qui identifie de façon unique l’application qui modifie l’élément.  
  
 Pour plus d’informations, consultez [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) dans le SDK Windows.  
  
##  <a name="getclipboarddata"></a>  COleClientItem::GetClipboardData  
 Appelez cette fonction pour obtenir un `COleDataSource` objet contenant toutes les données qui seraient placées sur le Presse-papiers par un appel à la [CopyToClipboard](#copytoclipboard) fonction membre.  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataSource*  
 Pointeur vers un [COleDataSource](../../mfc/reference/coledatasource-class.md) objet qui recevra les données contenues dans l’élément OLE.  
  
 *bIncludeLink*  
 TRUE si la liaison de données doit être incluses ; Sinon, FALSE.  
  
 *lpOffset*  
 Le décalage du pointeur de souris à partir de l’origine de l’objet en pixels.  
  
 *lpSize*  
 La taille de l’objet en pixels.  
  
### <a name="remarks"></a>Notes  
 `GetClipboardData` est appelé en tant que l’implémentation par défaut de [OnGetClipboardData](#ongetclipboarddata). Substituer `OnGetClipboardData` uniquement si vous souhaitez proposer des formats de données en plus de celles offertes par `CopyToClipboard`. Placer ces formats dans le `COleDataSource` objet avant ou après l’appel `CopyToClipboard`, puis passez le `COleDataSource` de l’objet à la [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) (fonction). Par exemple, si vous souhaitez la position de l’élément OLE dans son document de conteneur à accompagner sur le Presse-papiers, définir votre propre format pour transmettre ces informations et placez-le dans le `COleDataSource` avant d’appeler `CopyToClipboard`.  
  
##  <a name="getdocument"></a>  COleClientItem::GetDocument  
 Appelez cette fonction pour obtenir un pointeur vers le document qui contient l’élément OLE.  
  
```  
COleDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le document qui contient l’élément OLE. NULL si l’élément ne fait pas partie d’un document.  
  
### <a name="remarks"></a>Notes  
 Ce pointeur permet d’accéder à la `COleDocument` objet que vous avez passé en tant qu’argument à la `COleClientItem` constructeur.  
  
##  <a name="getdrawaspect"></a>  COleClientItem::GetDrawAspect  
 Appelez le `GetDrawAspect` fonction membre pour déterminer l’aspect « actuel », ou, de l’élément.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur de l’énumération DVASPECT, dont les valeurs sont répertoriées dans la référence pour [SetDrawAspect](#setdrawaspect).  
  
### <a name="remarks"></a>Notes  
 L’aspect spécifie la façon dont l’élément doit être restitué.  
  
##  <a name="getextent"></a>  COleClientItem::GetExtent  
 Appelez cette fonction pour extraire la taille de l’élément OLE.  
  
```  
BOOL GetExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)- 1);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpSize*  
 Pointeur vers un `SIZE` structure ou un `CSize` objet qui recevra les informations de taille.  
  
 *nDrawAspect*  
 Spécifie l’aspect de l’élément OLE dont les limites doivent être récupérés. Pour connaître les valeurs possibles, consultez [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; 0 si l’élément OLE est vide.  
  
### <a name="remarks"></a>Notes  
 Si l’application serveur ait été écrit à l’aide de la bibliothèque Microsoft Foundation Class, cette fonction provoque la [OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent) fonction membre correspondante `COleServerItem` objet à appeler. Notez que la taille récupérée peut différer de la taille dernièrement défini à la [SetExtent](#setextent) fonction membre ; la taille spécifiée par `SetExtent` est traitée comme une suggestion. Les dimensions sont exprimées en unités MM_HIMETRIC.  
  
> [!NOTE]
>  N’appelez pas `GetExtent` pendant le traitement d’un gestionnaire d’OLE, tel que [OnChange](#onchange). Appelez [GetCachedExtent](#getcachedextent) à la place.  
  
 Pour plus d’informations, consultez [IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) dans le SDK Windows.  
  
##  <a name="geticonfromregistry"></a>  COleClientItem::GetIconFromRegistry  
 Appelez cette fonction membre pour récupérer un handle vers une ressource d’icône associée au serveur d’un CLSID particulier.  
  
```  
HICON GetIconFromRegistry() const;  
  
static HICON GetIconFromRegistry(CLSID& clsid);
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 Une référence au CLSID pour le serveur associé à l’icône.  
  
### <a name="return-value"></a>Valeur de retour  
 Valide handle vers la ressource icône, ou NULL si l’icône de serveur ou une icône par défaut, ne peut pas être trouvée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre ne démarrera pas le serveur ou obtenir une icône de manière dynamique, même si le serveur est déjà en cours d’exécution. Au lieu de cela, cette fonction membre ouvre l’image exécutable du serveur et récupère l’icône statique associée au serveur car il a été inscrit.  
  
##  <a name="geticonicmetafile"></a>  COleClientItem::GetIconicMetafile  
 Récupère le métafichier utilisé pour dessiner l’icône de l’élément.  
  
```  
HGLOBAL GetIconicMetafile();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle du métafichier en cas de réussite ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 S’il n’existe aucune icône actuelle, une icône par défaut est retournée. Cela est appelé automatiquement par les boîtes de dialogue MFC/OLE et n’est généralement pas appelée directement.  
  
 Cette fonction appelle également [SetIconicMetafile](#seticonicmetafile) pour mettre en cache le métafichier pour une utilisation ultérieure.  
  
##  <a name="getinplacewindow"></a>  COleClientItem::GetInPlaceWindow  
 Appelez le `GetInPlaceWindow` fonction membre pour obtenir un pointeur vers la fenêtre dans laquelle l’élément a été ouvert pour modification sur place.  
  
```  
CWnd* GetInPlaceWindow();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la fenêtre d’édition sur place de l’élément ; NULL si l’élément n’est pas actif ou si son serveur n’est pas disponible.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée uniquement pour les éléments qui sont actifs sur place.  
  
##  <a name="getitemstate"></a>  COleClientItem::GetItemState  
 Appelez cette fonction pour obtenir l’état actuel de l’élément OLE.  
  
```  
UINT GetItemState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `COleClientItem::ItemState` énumérée de valeur, qui peut prendre l’une des opérations suivantes : `emptyState`, `loadedState`, `openState`, `activeState`, `activeUIState`. Pour plus d’informations sur ces États, consultez l’article [conteneurs : États d’élément Client](../../mfc/containers-client-item-states.md).  
  
### <a name="remarks"></a>Notes  
 Pour être informé de l’état de l’élément OLE change, vous devez utiliser le [OnChange](#onchange) fonction membre.  
  
 Pour plus d’informations, consultez l’article [conteneurs : États d’élément Client](../../mfc/containers-client-item-states.md).  
  
##  <a name="getlaststatus"></a>  COleClientItem::GetLastStatus  
 Retourne le code d’état de la dernière opération OLE.  
  
```  
SCODE GetLastStatus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur SCODE.  
  
### <a name="remarks"></a>Notes  
 Pour les fonctions membres qui retournent des fonctions qui retournent la valeur NULL, une valeur Booléenne FALSE ou autres membres `GetLastStatus` retourne plus d’informations sur l’échec. N’oubliez pas que la plupart des fonctions de membre OLE lèvent des exceptions pour les erreurs plus sérieux. Les informations spécifiques sur l’interprétation de la SCODE dépendent de l’appel OLE sous-jacent qui dernière a retourné une valeur SCODE.  
  
 Pour plus d’informations sur SCODE, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans la documentation du SDK Windows.  
  
##  <a name="getlinkupdateoptions"></a>  COleClientItem::GetLinkUpdateOptions  
 Appelez cette fonction pour obtenir la valeur actuelle de l’option de mise à jour de liaisons pour l’élément OLE.  
  
```  
OLEUPDATE GetLinkUpdateOptions();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs suivantes :  
  
- OLEUPDATE_ALWAYS mettre à jour l’élément lié chaque fois que possible. Cette option prend en charge la case d’option lien-mise à jour automatique dans la boîte de dialogue Liaisons.  
  
- OLEUPDATE_ONCALL mettre à jour l’élément lié uniquement sur demande à partir de l’application de conteneur (lorsque le [UpdateLink](#updatelink) fonction membre est appelée). Cette option prend en charge la case d’option lien-mise à jour manuelle dans la boîte de dialogue Liaisons.  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’une opération avancée.  
  
 Cette fonction est appelée automatiquement par le [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md) classe.  
  
 Pour plus d’informations, consultez [IOleLink::GetUpdateOptions](/windows/desktop/api/oleidl/nf-oleidl-iolelink-getupdateoptions) dans le SDK Windows.  
  
##  <a name="gettype"></a>  COleClientItem::GetType  
 Appelez cette fonction pour déterminer si l’élément OLE est lié ou incorporé, ou statiques.  
  
```  
OLE_OBJTYPE GetType() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Entier non signé avec l’une des valeurs suivantes :  
  
- Élément OT_LINK l’OLE est un lien.  
  
- Élément OT_EMBEDDED l’OLE est incorporé.  
  
- Élément OT_STATIC l’OLE est statique, autrement dit, il contient uniquement des données de présentation, les données non natives et par conséquent ne peut pas être modifié.  
  
##  <a name="getusertype"></a>  COleClientItem::GetUserType  
 Appelez cette fonction pour obtenir la chaîne visible par l’utilisateur, décrivant le type de l’élément OLE, telles que « document Word. »  
  
```  
void GetUserType(
    USERCLASSTYPE nUserClassType,  
    CString& rString);
```  
  
### <a name="parameters"></a>Paramètres  
 *nUserClassType*  
 Une valeur qui indique la variante souhaitée de la chaîne décrivant le type de l’élément OLE. Cela peut avoir l’une des valeurs suivantes :  
  
- USERCLASSTYPE_FULL complet tapez nom affiché à l’utilisateur.  
  
- USERCLASSTYPE_SHORT un nom court (15 caractères au maximum) pour une utilisation dans les menus déroulants et de la boîte de dialogue Modifier les liens.  
  
- USERCLASSTYPE_APPNAME le nom de l’application de la classe de maintenance.  
  
 *rString*  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet auquel la chaîne décrivant le type de l’élément OLE est à retourner.  
  
### <a name="remarks"></a>Notes  
 Il s’agit souvent l’entrée dans la base de données système d’inscription.  
  
 Si le nom de type complet est demandée mais non disponibles, le nom court est utilisé à la place. Si aucune entrée pour le type de l’élément OLE est trouvée dans la base de données d’inscription, ou s’il n’y a aucun type de l’utilisateur inscrit pour le type de l’élément OLE, puis le type de l’utilisateur actuellement stockés dans l’élément OLE est utilisée. Si ce nom de type utilisateur est une chaîne vide, « Objet inconnu » est utilisé.  
  
 Pour plus d’informations, consultez [IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) dans le SDK Windows.  
  
##  <a name="isinplaceactive"></a>  COleClientItem::IsInPlaceActive  
 Appelez cette fonction pour voir si l’élément OLE est actif en place.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément OLE est actif en place ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Il est courant pour exécuter une logique différente selon que l’élément est modifié sur place. La fonction vérifie si l’état d’élément actuel est égal à la `activeState` ou `activeUIState`.  
  
##  <a name="islinkuptodate"></a>  COleClientItem::IsLinkUpToDate  
 Appelez cette fonction pour voir si l’élément OLE est à jour.  
  
```  
BOOL IsLinkUpToDate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément OLE est à jour ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Un élément lié peut être obsolète si son document source a été mis à jour. Un élément incorporé qui contient des liens qu’il contient peut même devenir obsolète. La fonction effectue une vérification récursive de l’élément OLE. Notez que pour déterminer si un élément OLE est obsolète peut être coûteuse que réellement effectuer une mise à jour.  
  
 Cela est appelé automatiquement par le [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md) implémentation.  
  
 Pour plus d’informations, consultez [IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) dans le SDK Windows.  
  
##  <a name="ismodified"></a>  COleClientItem::IsModified  
 Appelez cette fonction pour voir si l’élément OLE est modifié (modifié depuis son dernier enregistrement).  
  
```  
BOOL IsModified() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément OLE est modifiée ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IPersistStorage::IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) dans le SDK Windows.  
  
##  <a name="isopen"></a>  COleClientItem::IsOpen  
 Appelez cette fonction pour voir si l’élément OLE est ouvert ; Autrement dit, il est ouvert dans une instance de l’application serveur en cours d’exécution dans une fenêtre distincte.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément OLE est ouvert ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Il est utilisé pour déterminer le moment de dessiner l’objet avec un modèle de hachurage. Un objet ouvert doit avoir un modèle de hachurage dessiné sur l’objet. Vous pouvez utiliser un [CRectTracker](../../mfc/reference/crecttracker-class.md) objet pour effectuer cette opération.  
  
##  <a name="isrunning"></a>  COleClientItem::IsRunning  
 Appelez cette fonction pour voir si l’élément OLE est en cours d’exécution ; Autrement dit, si l’élément est chargé et en cours d’exécution dans l’application serveur.  
  
```  
BOOL IsRunning() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément OLE est en cours d’exécution ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [OleIsRunning](/windows/desktop/api/ole2/nf-ole2-oleisrunning) dans le SDK Windows.  
  
##  <a name="onactivate"></a>  COleClientItem::OnActivate  
 Appelé par l’infrastructure pour avertir l’élément qu’il a simplement été activé en place.  
  
```  
virtual void OnActivate();
```  
  
### <a name="remarks"></a>Notes  
 Notez que cette fonction est appelée pour indiquer que le serveur est en cours d’exécution, afin de ne pas pour indiquer que son interface utilisateur a été installée dans l’application conteneur. À ce stade, l’objet n’a pas d’une interface utilisateur actif (n’est pas `activeUIState`). Il n’a pas installé ses menus ou la barre d’outils. Le [OnActivateUI](#onactivateui) fonction membre est appelée lorsque cela se produit.  
  
 L’implémentation par défaut appelle la [OnChange](#onchange) fonction membre avec OLE_CHANGEDSTATE en tant que paramètre. Remplacez cette fonction pour effectuer un traitement personnalisé lorsqu’un élément devienne actif en place.  
  
##  <a name="onactivateui"></a>  COleClientItem::OnActivateUI  
 Le framework appelle `OnActivateUI` lorsque l’objet a entré l’état de l’interface utilisateur actif.  
  
```  
virtual void OnActivateUI();
```  
  
### <a name="remarks"></a>Notes  
 L’objet a installé maintenant sa barre d’outils et les menus.  
  
 L’implémentation par défaut souvient HWND du serveur pour une utilisation ultérieure `GetServerWindow` appels.  
  
##  <a name="onchange"></a>  COleClientItem::OnChange  
 Appelé par le framework lorsque l’utilisateur modifie, enregistre ou ferme l’élément OLE.  
  
```  
virtual void OnChange(
    OLE_NOTIFICATION nCode,  
    DWORD dwParam);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCode*  
 La raison pour laquelle le serveur a modifié cet élément. Il peut avoir l’une des valeurs suivantes :  
  
- OLE_CHANGED The OLE apparence de l’élément a changé.  
  
- Élément OLE_SAVED The OLE a été enregistré.  
  
- Élément OLE_CLOSED The OLE a été fermé.  
  
- Élément OLE_CHANGED_STATE The OLE a changé d’un état à un autre.  
  
 *dwParam*  
 Si *nCode* est OLE_SAVED ou OLE_CLOSED, ce paramètre n’est pas utilisé. Si *nCode* est OLE_CHANGED, ce paramètre spécifie l’aspect de l’élément OLE qui a changé. Pour connaître les valeurs possibles, consultez le *dwParam* paramètre de [COleClientItem::Draw](#draw). Si *nCode* est OLE_CHANGED_STATE, ce paramètre est un `COleClientItem::ItemState` valeur énumérée et décrit l’état en cours. Il peut avoir l’une des valeurs suivantes : `emptyState`, `loadedState`, `openState`, `activeState`, ou `activeUIState`.  
  
### <a name="remarks"></a>Notes  
 (Si l’application serveur est écrit à l’aide de la bibliothèque Microsoft Foundation Class, cette fonction est appelée en réponse à la `Notify` fonctions membres de `COleServerDoc` ou `COleServerItem`.) L’implémentation par défaut marque le document conteneur comme modifié se *nCode* est OLE_CHANGED ou OLE_SAVED.  
  
 Pour OLE_CHANGED_STATE, l’état actuel est retourné à partir de [GetItemState](#getitemstate) sera toujours l’ancien état, ce qui signifie que l’état qui était actuel avant ce changement d’état.  
  
 Remplacez cette fonction pour répondre aux modifications de l’état de l’élément OLE. En général, vous mettez à jour apparence de l’élément en invalidant la zone dans laquelle l’élément est affiché. Appeler l’implémentation de classe de base au début du remplacement.  
  
##  <a name="onchangeitemposition"></a>  COleClientItem::OnChangeItemPosition  
 Appelé par l’infrastructure pour notifier au conteneur étendue de l’élément OLE a été modifié pendant l’activation sur place.  
  
```  
virtual BOOL OnChangeItemPosition(const CRect& rectPos);
```  
  
### <a name="parameters"></a>Paramètres  
 *rectPos*  
 Indique la position par rapport à la zone cliente de l’application de conteneur.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la position de l’élément a été correctement modifiée ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut détermine le nouveau rectangle visible de l’élément OLE et d’appels [SetItemRects](#setitemrects) avec les nouvelles valeurs. L’implémentation par défaut calcule le rectangle visible pour l’élément et transmet ces informations au serveur.  
  
 Remplacez cette fonction pour appliquer des règles spéciales pour l’opération de redimensionnement et de déplacement. Si l’application est écrite dans MFC, cet appel aboutit, car le serveur appelé [COleServerDoc::RequestPositionChange](../../mfc/reference/coleserverdoc-class.md#requestpositionchange).  
  
##  <a name="ondeactivate"></a>  COleClientItem::OnDeactivate  
 Appelé par l’infrastructure lorsque l’élément OLE passe de l’état actif sur place ( `activeState`) à l’état chargé, ce qui signifie qu’elle est désactivée après une activation sur place.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Notes  
 Notez que cette fonction est appelée pour indiquer que l’élément OLE est fermé, pas son interface utilisateur ayant été supprimé de l’application de conteneur. Lorsque cela se produit, le [OnDeactivateUI](#ondeactivateui) fonction membre est appelée.  
  
 L’implémentation par défaut appelle la [OnChange](#onchange) fonction membre avec OLE_CHANGEDSTATE en tant que paramètre. Remplacez cette fonction pour effectuer un traitement personnalisé lorsqu’un élément actif sur place est désactivé. Par exemple, si vous prenez en charge la commande Annuler dans votre application de conteneur, vous pouvez remplacer cette fonction pour ignorer l’état d’annulation, indiquant que la dernière opération effectuée sur l’élément OLE ne peut pas être annulée une fois que l’élément est désactivé.  
  
##  <a name="ondeactivateandundo"></a>  COleClientItem::OnDeactivateAndUndo  
 Appelé par le framework lorsque l’utilisateur appelle la commande Annuler après l’activation de l’élément OLE sur place.  
  
```  
virtual void OnDeactivateAndUndo();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut appelle [DeactivateUI](#deactivateui) pour désactiver l’interface du serveur utilisateur. Remplacez cette fonction si vous implémentez la commande Annuler dans votre application conteneur. Dans la substitution, appelez la version de la classe de base de la fonction et annuler la dernière commande exécutée dans votre application.  
  
 Pour plus d’informations, consultez [IOleInPlaceSite::DeactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplacesite-deactivateandundo) dans le SDK Windows.  
  
##  <a name="ondeactivateui"></a>  COleClientItem::OnDeactivateUI  
 Appelée lorsque l’utilisateur désactive un élément qui a été activé sur place.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Paramètres  
 *bUndoable*  
 Spécifie si les modifications sont annulables.  
  
### <a name="remarks"></a>Notes  
 Cette fonction restaure l’interface utilisateur de l’application de conteneur à son état d’origine, masquage des menus et autres contrôles qui ont été créés pour l’activation sur place.  
  
 Si *bUndoable* est FALSE, le conteneur doit désactiver la commande Annuler, en vigueur en ignorant l’état d’annulation du conteneur, car il indique que la dernière opération effectuée par le serveur n’est pas annulable.  
  
##  <a name="ondiscardundostate"></a>  COleClientItem::OnDiscardUndoState  
 Appelé par l’infrastructure lorsque l’utilisateur effectue une action qui ignore l’état d’annulation lors de la modification de l’élément OLE.  
  
```  
virtual void OnDiscardUndoState();
```  
  
### <a name="remarks"></a>Notes  
 L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction si vous implémentez la commande Annuler dans votre application conteneur. Dans la substitution, ignorer l’état d’annulation de l’application de conteneur.  
  
 Si le serveur a été écrit avec la bibliothèque Microsoft Foundation Class, le serveur peut provoquer cette fonction à appeler en appelant [COleServerDoc::DiscardUndoState](../../mfc/reference/coleserverdoc-class.md#discardundostate).  
  
 Pour plus d’informations, consultez [IOleInPlaceSite::DiscardUndoState](/windows/desktop/api/oleidl/nf-oleidl-ioleinplacesite-discardundostate) dans le SDK Windows.  
  
##  <a name="ongetclipboarddata"></a>  COleClientItem::OnGetClipboardData  
 Appelé par le framework pour obtenir un `COleDataSource` objet contenant toutes les données qui seraient placées sur le Presse-papiers par un appel à la [CopyToClipboard](#copytoclipboard) ou [DoDragDrop](#dodragdrop) fonction membre.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *bIncludeLink*  
 Affectez la valeur TRUE si les données de lien doivent être copiées dans le Presse-papiers. Affectez la valeur FALSE si le serveur de votre application ne prend pas en charge les liens.  
  
 *lpOffset*  
 Pointeur vers l’offset du pointeur de souris à partir de l’origine de l’objet en pixels.  
  
 *lpSize*  
 Pointeur vers la taille de l’objet en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [COleDataSource](../../mfc/reference/coledatasource-class.md) objet contenant les données du Presse-papiers.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction appelle [exception de GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetcliprect"></a>  COleClientItem::OnGetClipRect  
 Le framework appelle la `OnGetClipRect` fonction membre pour obtenir les coordonnées du rectangle de découpage de l’élément qui est en cours de modification en place.  
  
```  
virtual void OnGetClipRect(CRect& rClipRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *rClipRect*  
 Pointeur vers un objet de classe [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contiendra les coordonnées du rectangle de découpage de l’élément.  
  
### <a name="remarks"></a>Notes  
 Coordonnées sont exprimées en pixels par rapport à la zone cliente de la fenêtre d’application de conteneur.  
  
 L’implémentation par défaut retourne simplement le rectangle client de la vue sur laquelle l’élément est actif en place.  
  
##  <a name="ongetitemposition"></a>  COleClientItem::OnGetItemPosition  
 Le framework appelle la `OnGetItemPosition` fonction membre pour obtenir les coordonnées de l’élément qui est en cours de modification en place.  
  
```  
virtual void OnGetItemPosition(CRect& rPosition);
```  
  
### <a name="parameters"></a>Paramètres  
 *rPosition*  
 Référence à la [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui contient les coordonnées de position de l’élément.  
  
### <a name="remarks"></a>Notes  
 Coordonnées sont exprimées en pixels par rapport à la zone cliente de la fenêtre d’application de conteneur.  
  
 L’implémentation par défaut de cette fonction est sans effet. Les applications qui prennent en charge la modification sur place nécessitent son implémentation.  
  
##  <a name="ongetwindowcontext"></a>  COleClientItem::OnGetWindowContext  
 Appelé par le framework lorsqu’un élément est activé sur place.  
  
```  
virtual BOOL OnGetWindowContext(
    CFrameWnd** ppMainFrame,  
    CFrameWnd** ppDocFrame,  
    LPOLEINPLACEFRAMEINFO lpFrameInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppMainFrame*  
 Pointeur vers un pointeur vers la fenêtre frame principale.  
  
 *ppDocFrame*  
 Pointeur vers un pointeur vers la fenêtre frame de document.  
  
 *lpFrameInfo*  
 Pointeur vers un [oleinplaceframeinfo que](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) structure qui recevra les informations de la fenêtre frame.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour récupérer des informations sur la fenêtre parente de l’élément OLE.  
  
 Si le conteneur est une application MDI, l’implémentation par défaut retourne un pointeur vers le [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) dans l’objet *ppMainFrame* et un pointeur vers l’actif [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)dans l’objet *ppDocFrame*. Si le conteneur est une application SDI, l’implémentation par défaut retourne un pointeur vers le [CFrameWnd](../../mfc/reference/cframewnd-class.md) dans l’objet *ppMainFrame* et retourne la valeur NULL dans *ppDocFrame*. L’implémentation par défaut remplit également les membres de *lpFrameInfo*.  
  
 Remplacez cette fonction uniquement si l’implémentation par défaut ne répondent pas à votre application ; par exemple, si votre application comporte un modèle d’interface utilisateur qui diffère de SDI ou MDI. Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez [IOleInPlaceSite::GetWindowContext](/windows/desktop/api/oleidl/nf-oleidl-ioleinplacesite-getwindowcontext) et [oleinplaceframeinfo que](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) structure dans le SDK Windows.  
  
##  <a name="oninsertmenus"></a>  COleClientItem::OnInsertMenus  
 Appelé par l’infrastructure pendant l’activation sur place pour insérer les menus de l’application de conteneur dans un menu vide.  
  
```  
virtual void OnInsertMenus(
    CMenu* pMenuShared,  
    LPOLEMENUGROUPWIDTHS lpMenuWidths);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMenuShared*  
 Pointe vers un menu vide.  
  
 *lpMenuWidths*  
 Pointe vers un tableau de six longues valeurs indiquant le nombre de menus est dans chacun des groupes de menus suivants : fichier, Edition, conteneur, objet, fenêtre, aide. Il incombe à l’application de conteneur pour les groupes de menu fichier, conteneur et fenêtre, correspondant aux éléments 0, 2 et 4 de ce tableau.  
  
### <a name="remarks"></a>Notes  
 Ce menu est ensuite transmis au serveur, qui insère ses propres menus, création d’un menu composite. Cette fonction peut être appelée à plusieurs reprises pour générer plusieurs menus composites.  
  
 L’implémentation par défaut insère *pMenuShared* les menus sur place conteneur ; autrement dit, les groupes de menu fichier, conteneur et fenêtre. [CDocTemplate::SetContainerInfo](../../mfc/reference/cdoctemplate-class.md#setcontainerinfo) est utilisé pour définir cette ressource de menu. L’implémentation par défaut affecte également les valeurs appropriées aux éléments 0, 2 et 4 dans *lpMenuWidths*, en fonction de la ressource de menu. Remplacez cette fonction si l’implémentation par défaut n’est pas appropriée pour votre application ; par exemple, si votre application n’utilise pas les modèles de document pour associer des ressources avec des types de documents. Si vous substituez cette fonction, vous devez également substituer [OnSetMenu](#onsetmenu) et [OnRemoveMenus](#onremovemenus). Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez [IOleInPlaceFrame::InsertMenu](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceframe-insertmenus) dans le SDK Windows.  
  
##  <a name="onremovemenus"></a>  COleClientItem::OnRemoveMenus  
 Appelé par l’infrastructure pour supprimer les menus du conteneur dans le menu composite spécifié lors de l’activation en place se termine.  
  
```  
virtual void OnRemoveMenus(CMenu* pMenuShared);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMenuShared*  
 Pointe vers le menu composite construit par les appels à la [OnInsertMenus](#oninsertmenus) fonction membre.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut supprime *pMenuShared* les menus sur place conteneur, qui est, les groupes de menu fichier, conteneur et fenêtre. Remplacez cette fonction si l’implémentation par défaut n’est pas appropriée pour votre application ; par exemple, si votre application n’utilise pas les modèles de document pour associer des ressources avec des types de documents. Si vous substituez cette fonction, vous devez substituer probablement [OnInsertMenus](#oninsertmenus) et [OnSetMenu](#onsetmenu) également. Il s’agit d’une avancée substituable.  
  
 Les sous-menus *pMenuShared* peuvent être partagées par plusieurs menu composite si le serveur a appelé à plusieurs reprises `OnInsertMenus`. Par conséquent, vous ne devez pas supprimer des sous-menus dans votre substitution de `OnRemoveMenus`; vous devez uniquement les détacher.  
  
 Pour plus d’informations, consultez [IOleInPlaceFrame::RemoveMenus](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceframe-removemenus) dans le SDK Windows.  
  
##  <a name="onscrollby"></a>  COleClientItem::OnScrollBy  
 Appelé par l’infrastructure pour faire défiler l’élément OLE en réponse aux demandes à partir du serveur.  
  
```  
virtual BOOL OnScrollBy(CSize sizeExtent);
```  
  
### <a name="parameters"></a>Paramètres  
 *sizeExtent*  
 Spécifie les distances, en pixels, pour faire défiler vers le directions x et y.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’utilisateur a fait défiler l’élément ; 0 si l’élément n’a pas pu faire défiler.  
  
### <a name="remarks"></a>Notes  
 Par exemple, si l’élément OLE est partiellement visible et que l’utilisateur se déplace en dehors de la région visible lors de l’exécution de modification sur place, cette fonction est appelée pour que le curseur reste visible. L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour faire défiler l’élément de la quantité spécifiée. Notez que, à la suite de défilement, la partie visible de l’élément OLE peut changer. Appelez [SetItemRects](#setitemrects) pour mettre à jour le rectangle visible de l’élément.  
  
 Pour plus d’informations, consultez [IOleInPlaceSite::Scroll](/windows/desktop/api/oleidl/nf-oleidl-ioleinplacesite-scroll) dans le SDK Windows.  
  
##  <a name="onsetmenu"></a>  COleClientItem::OnSetMenu  
 Appelé par l’infrastructure deux fois lors de l’activation en place commence et se termine. la première fois pour installer le menu composite et la deuxième fois (avec *holemenu* égale à NULL) pour le supprimer.  
  
```  
virtual void OnSetMenu(
    CMenu* pMenuShared,  
    HOLEMENU holemenu,  
    HWND hwndActiveObject);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMenuShared*  
 Pointeur vers le menu composite construit par les appels à la [OnInsertMenus](#oninsertmenus) fonction membre et le `InsertMenu` (fonction).  
  
 *holemenu*  
 Handle vers le descripteur de menu retourné par la `OleCreateMenuDescriptor` de fonction, ou NULL si le code de distribution doit être supprimée.  
  
 *hwndActiveObject*  
 Handle de la fenêtre d’édition pour l’élément OLE. Il s’agit de la fenêtre qui reçoit les commandes d’édition à partir d’OLE.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut installe ou supprime le menu composite, puis appelle la [OleSetMenuDescriptor](/windows/desktop/api/ole2/nf-ole2-olesetmenudescriptor) (fonction) pour installer ou supprimer le code de distribution. Remplacez cette fonction si l’implémentation par défaut n’est pas appropriée pour votre application. Si vous substituez cette fonction, vous devez substituer probablement [OnInsertMenus](#oninsertmenus) et [OnRemoveMenus](#onremovemenus) également. Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez [OleCreateMenuDescriptor](/windows/desktop/api/ole2/nf-ole2-olecreatemenudescriptor), [OleSetMenuDescriptor](/windows/desktop/api/ole2/nf-ole2-olesetmenudescriptor), et [IOleInPlaceFrame::SetMenu](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceframe-setmenu) dans le SDK Windows.  
  
##  <a name="onshowcontrolbars"></a>  COleClientItem::OnShowControlBars  
 Appelé par l’infrastructure pour afficher et masquer les barres de contrôle de l’application de conteneur.  
  
```  
virtual BOOL OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFrameWnd*  
 Pointeur vers la fenêtre frame de l’application de conteneur. Cela peut être une fenêtre frame principale ou une fenêtre enfant MDI.  
  
 *bShow*  
 Spécifie si les barres de contrôles doivent être affichés ou masqués.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’appel de fonction provoque une modification dans l’état de barres de contrôles ; 0 si l’appel ne subit aucune modification, ou si *pFrameWnd* ne pointe pas vers la fenêtre frame du conteneur.  
  
### <a name="remarks"></a>Notes  
 Cette fonction retourne 0 si les barres de contrôles se trouvent déjà dans l’état spécifié par *bShow.* Cela pourrait se produire, par exemple, si les barres de contrôle sont masquées et *bShow* a la valeur FALSE.  
  
 L’implémentation par défaut supprime la barre d’outils de la fenêtre frame de niveau supérieur.  
  
##  <a name="onshowitem"></a>  COleClientItem::OnShowItem  
 Appelé par l’infrastructure pour afficher l’élément OLE, rendant totalement visible lors de l’édition.  
  
```  
virtual void OnShowItem();
```  
  
### <a name="remarks"></a>Notes  
 Il est utilisé lorsque votre application conteneur prend en charge des liens vers des éléments incorporés (autrement dit, si vous avez dérivé votre classe de document à partir de [COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md)). Cette fonction est appelée pendant l’activation sur place ou lorsque l’élément OLE est une source de liaison et l’utilisateur souhaite le modifier. L’implémentation par défaut active la première vue sur le document conteneur. Remplacez cette fonction pour faire défiler le document afin que l’élément OLE est visible.  
  
##  <a name="onupdateframetitle"></a>  COleClientItem::OnUpdateFrameTitle  
 Appelé par l’infrastructure pendant l’activation sur place pour mettre à jour de la barre de titre de la fenêtre frame.  
  
```  
virtual BOOL OnUpdateFrameTitle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si cette fonction correctement mis à jour pour le titre du frame, sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut ne change pas le titre de la fenêtre frame. Remplacez cette fonction si vous souhaitez un titre d’autre frame pour votre application, par exemple « *application server* - *élément* dans *docname*» (par exemple, « Microsoft Excel - feuille de calcul dans le rapport. DOC »). Il s’agit d’une avancée substituable.  
  
##  <a name="reactivateandundo"></a>  COleClientItem::ReactivateAndUndo  
 Appelez cette fonction pour réactiver l’élément OLE et annuler la dernière opération effectuée par l’utilisateur lors de l’édition sur place.  
  
```  
BOOL ReactivateAndUndo();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si votre application conteneur prend en charge la commande Annuler, appelez cette fonction si l’utilisateur choisit la commande Annuler immédiatement après la désactivation de l’élément OLE.  
  
 Si l’application serveur est écrite avec les bibliothèques de classes Microsoft Foundation, cette fonction, le serveur appelle [COleServerDoc::OnReactivateAndUndo](../../mfc/reference/coleserverdoc-class.md#onreactivateandundo).  
  
 Pour plus d’informations, consultez [IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) dans le SDK Windows.  
  
##  <a name="release"></a>  COleClientItem::Release  
 Appelez cette fonction pour nettoyer les ressources utilisées par l’élément OLE.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwCloseOption*  
 Indicateur qui spécifie dans quelles circonstances l’élément OLE est enregistré quand elle retourne à l’état chargé. Pour obtenir la liste des valeurs possibles, consultez [COleClientItem::Close](#close).  
  
### <a name="remarks"></a>Notes  
 `Release` est appelée par le `COleClientItem` destructeur.  
  
 Pour plus d’informations, consultez [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) dans le SDK Windows.  
  
##  <a name="reload"></a>  COleClientItem::Reload  
 Ferme et le recharge l’élément.  
  
```  
BOOL Reload();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez le `Reload` fonction après l’activation de l’élément en tant qu’élément d’un autre type par un appel à [ActivateAs](#activateas).  
  
##  <a name="run"></a>  COleClientItem::Run  
 Exécute l’application associée à cet élément.  
  
```  
void Run();
```  
  
### <a name="remarks"></a>Notes  
 Appelez le `Run` fonction membre pour lancer l’application serveur avant d’activer l’élément. Cette opération est effectuée automatiquement par [activer](#activate) et [DoVerb](#doverb), il est donc généralement pas nécessaire d’appeler cette fonction. Appelez cette fonction s’il est nécessaire exécuter le serveur afin de définir un attribut d’élément, tel que [SetExtent](#setextent), avant d’exécuter [DoVerb](#doverb).  
  
##  <a name="setdrawaspect"></a>  COleClientItem::SetDrawAspect  
 Appelez le `SetDrawAspect` fonction membre pour définir la « h », ou la vue, de l’élément.  
  
```  
virtual void SetDrawAspect(DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawAspect*  
 Une valeur de l’énumération DVASPECT. Ce paramètre peut prendre l'une des valeurs suivantes :  
  
- Élément de DVASPECT_CONTENT est représenté de manière à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- DVASPECT_THUMBNAIL est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- Élément de DVASPECT_ICON est représenté par une icône.  
  
- Élément de DVASPECT_DOCPRINT est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
### <a name="remarks"></a>Notes  
 L’aspect spécifie comment l’élément doit être restitué par [dessiner](#draw) lorsque la valeur par défaut de cette fonction *nDrawAspect* argument est utilisé.  
  
 Cette fonction est appelée automatiquement par l’icône de modification (et d’autres boîtes de dialogue qui appellent directement de la boîte de dialogue Changer d’icône) pour activer l’aspect de l’affichage sous forme d’icône lorsque demandé par l’utilisateur.  
  
##  <a name="setextent"></a>  COleClientItem::SetExtent  
 Appelez cette fonction pour indiquer la quantité d’espace disponible pour l’élément OLE.  
  
```  
void SetExtent(
    const CSize& size,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Paramètres  
 *size*  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui contient les informations de taille.  
  
 *nDrawAspect*  
 Spécifie l’aspect de l’élément OLE dont les limites doivent être définies. Pour connaître les valeurs possibles, consultez [SetDrawAspect](#setdrawaspect).  
  
### <a name="remarks"></a>Notes  
 Si l’application serveur ait été écrit à l’aide de la bibliothèque Microsoft Foundation Class, cela entraîne la [OnSetExtent](../../mfc/reference/coleserveritem-class.md#onsetextent) fonction membre correspondante `COleServerItem` objet à appeler. L’élément OLE pouvez ensuite ajuster son affichage en conséquence. Les dimensions doivent être des unités MM_HIMETRIC. Appelez cette fonction quand l’utilisateur redimensionne l’élément OLE ou si vous prenez en charge une forme de négociation de disposition.  
  
 Pour plus d’informations, consultez [IOleObject::SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) dans le SDK Windows.  
  
##  <a name="sethostnames"></a>  COleClientItem::SetHostNames  
 Appelez cette fonction pour spécifier le nom de l’application de conteneur et le nom du conteneur pour un élément OLE incorporé.  
  
```  
void SetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszHost*  
 Pointeur vers le nom visible par l’utilisateur de l’application de conteneur.  
  
 *lpszHostObj*  
 Pointeur vers une chaîne d’identification du conteneur qui contient l’élément OLE.  
  
### <a name="remarks"></a>Notes  
 Si l’application serveur ait été écrit à l’aide de la bibliothèque Microsoft Foundation Class, cette fonction appelle le [OnSetHostNames](../../mfc/reference/coleserverdoc-class.md#onsethostnames) fonction membre de la `COleServerDoc` document qui contient l’élément OLE. Ces informations sont utilisées dans les titres de fenêtre lorsque l’élément OLE est en cours de modification. Chaque fois qu’un document conteneur est chargé, l’infrastructure appelle cette fonction pour tous les éléments OLE dans le document. `SetHostNames` s’applique uniquement aux éléments incorporés. Il n’est pas nécessaire d’appeler cette fonction à chaque fois qu’un élément OLE incorporé est activé pour la modification.  
  
 Cela est également appelée automatiquement avec le nom de document et le nom de l’application lorsqu’un objet est chargé ou lorsqu’un fichier est enregistré sous un autre nom. En conséquence, il n’est pas généralement nécessaire d’appeler cette fonction directement.  
  
 Pour plus d’informations, consultez [IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) dans le SDK Windows.  
  
##  <a name="seticonicmetafile"></a>  COleClientItem::SetIconicMetafile  
 Met en cache le métafichier utilisé pour dessiner l’icône de l’élément.  
  
```  
BOOL SetIconicMetafile(HGLOBAL hMetaPict);
```  
  
### <a name="parameters"></a>Paramètres  
 *hMetaPict*  
 Handle du métafichier utilisé pour dessiner l’icône de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez [GetIconicMetafile](#geticonicmetafile) pour récupérer le métafichier.  
  
 Le *hMetaPict* paramètre est copié dans l’élément ; par conséquent, *hMetaPict* doit être libérée par l’appelant.  
  
##  <a name="setitemrects"></a>  COleClientItem::SetItemRects  
 Appelez cette fonction pour définir le rectangle englobant ou le rectangle visible de l’élément OLE.  
  
```  
BOOL SetItemRects(
    LPCRECT lpPosRect = NULL,  
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lprcPosRect*  
 Pointeur vers le rectangle contenant les limites de l’élément OLE par rapport à sa fenêtre parente, dans les coordonnées clientes.  
  
 *lprcClipRect*  
 Pointeur vers le rectangle contenant les limites de la partie visible de l’élément OLE par rapport à sa fenêtre parente, dans les coordonnées clientes.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée par l’implémentation par défaut de la [OnChangeItemPosition](#onchangeitemposition) fonction membre. Vous devez appeler cette fonction chaque fois que les modifications d’élément de la position ou la partie visible de l’OLE. Cela signifie généralement que vous l’appelez à partir de votre vue [OnSize](../../mfc/reference/cwnd-class.md#onsize) et [OnScrollBy](../../mfc/reference/cview-class.md#onscrollby) fonctions membres.  
  
 Pour plus d’informations, consultez [IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) dans le SDK Windows.  
  
##  <a name="setlinkupdateoptions"></a>  COleClientItem::SetLinkUpdateOptions  
 Appelez cette fonction pour définir l’option de mise à jour de liaisons pour la présentation de l’élément lié spécifié.  
  
```  
void SetLinkUpdateOptions(OLEUPDATE dwUpdateOpt);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwUpdateOpt*  
 La valeur de l’option de mise à jour de liaisons pour cet élément. Cette valeur doit être une des opérations suivantes :  
  
- OLEUPDATE_ALWAYS mettre à jour l’élément lié chaque fois que possible. Cette option prend en charge la case d’option lien-mise à jour automatique dans la boîte de dialogue Liaisons.  
  
- OLEUPDATE_ONCALL mettre à jour l’élément lié uniquement sur demande à partir de l’application de conteneur (lorsque le [UpdateLink](#updatelink) fonction membre est appelée). Cette option prend en charge la case d’option lien-mise à jour manuelle dans la boîte de dialogue Liaisons.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous ne devez pas modifier les options de mise à jour choisies par l’utilisateur dans la boîte de dialogue Liaisons.  
  
 Pour plus d’informations, consultez [IOleLink::SetUpdateOptions](/windows/desktop/api/oleidl/nf-oleidl-iolelink-setupdateoptions) dans le SDK Windows.  
  
##  <a name="setprintdevice"></a>  COleClientItem::SetPrintDevice  
 Appelez cette fonction pour modifier le périphérique cible à l’impression pour cet élément.  
  
```  
BOOL SetPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL SetPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Paramètres  
 *ptd*  
 Pointeur vers un [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) structure de données qui contient des informations sur le nouveau périphérique cible à l’impression. Peut être NULL.  
  
 *PPD*  
 Pointeur vers un [PRINTDLG](https://msdn.microsoft.com/library/windows/desktop/ms646940) structure de données qui contient des informations sur le nouveau périphérique cible à l’impression. Peut être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction met à jour le périphérique d’impression pour l’élément, mais elle n’actualise pas le cache de présentation. Pour mettre à jour le cache de présentation pour un élément, appelez [UpdateLink](#updatelink).  
  
 Les arguments de cette fonction contiennent des informations que le système OLE utilise pour identifier l’appareil cible. Le `PRINTDLG` structure contient des informations Windows utilise pour initialiser la boîte de dialogue d’impression commune. Une fois que l’utilisateur ferme la boîte de dialogue, Windows retourne des informations sur les sélections d’utilisateur dans cette structure. Le `m_pd` membre d’un [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objet est un `PRINTDLG` structure.  
  
 Pour plus d’informations sur cette structure, consultez [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) dans le SDK Windows.  
  
 Pour plus d’informations, consultez [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) dans le SDK Windows.  
  
##  <a name="updatelink"></a>  COleClientItem::UpdateLink  
 Appelez cette fonction pour mettre à jour les données de présentation de l’élément OLE immédiatement.  
  
```  
BOOL UpdateLink();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour les éléments liés, la fonction recherche la source de liaison pour obtenir une présentation de l’élément OLE. Ce processus peut impliquer une ou plusieurs applications de serveur, qui peuvent prendre du temps en cours d’exécution. Pour les éléments incorporés, la fonction opère de manière récursive, la vérification si l’élément incorporé contient des liens qui peuvent être obsolètes et les mettre à jour. L’utilisateur peut mettre à jour également manuellement à l’aide de la boîte de dialogue Liaisons des liens individuels.  
  
 Pour plus d’informations, consultez [IOleLink::Update](/windows/desktop/api/oleidl/nf-oleidl-iolelink-update) dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MFCBIND](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [CDocItem, classe](../../mfc/reference/cdocitem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
