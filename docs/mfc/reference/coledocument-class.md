---
title: COleDocument, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95eea7434fdaa12a6178ebd9648e8088b24b4dc8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205946"
---
# <a name="coledocument-class"></a>COleDocument, classe
Classe de base des documents OLE qui prennent en charge la modification sur place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|Construit un objet `COleDocument`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|Ajoute un élément à la liste des éléments gérés par le document.|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Définit le périphérique d’impression pour tous les éléments de client dans le document.|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Provoque des documents à stocker en utilisant le format de fichier de stockage structuré OLE.|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Retourne l’élément OLE qui est actif actuellement en place.|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|Obtient l’élément suivant de client pour une itération.|  
|[COleDocument::GetNextItem](#getnextitem)|Obtient l’élément de document suivant pour une itération.|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|Obtient l’élément suivant du serveur pour une itération.|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Retourne l’élément OLE principal sélectionné dans le document.|  
|[COleDocument::GetStartPosition](#getstartposition)|Obtient la position initiale pour commencer l’itération.|  
|[COleDocument::HasBlankItems](#hasblankitems)|Vérifie les éléments vides dans le document.|  
|[COleDocument::OnShowViews](#onshowviews)|Appelé lorsque le document devient visible ou invisible.|  
|[COleDocument::RemoveItem](#removeitem)|Supprime un élément de la liste des éléments gérés par le document.|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Marque le document comme modifié si un des éléments OLE contenus ont été modifié.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Gère les événements de la commande de menu changer d’icône.|  
|[COleDocument::OnEditConvert](#oneditconvert)|Gère la conversion d’un objet incorporé ou lié à partir d’un type vers un autre.|  
|[COleDocument::OnEditLinks](#oneditlinks)|Gère les événements dans la commande de liens dans le menu Edition.|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|Envoie un message électronique avec le document joint.|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Appelé par l’infrastructure pour mettre à jour de la commande interface utilisateur pour l’option de menu modifier/changer d’icône.|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Appelé par l’infrastructure pour mettre à jour de la commande interface utilisateur pour l’option de menu Modifier/liens.|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Appelé par l’infrastructure pour mettre à jour de la commande interface utilisateur pour la modification / *ObjectName* option de menu et le sous-menu verbe accédé à partir de l’édition / *ObjectName*.|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Appelé par l’infrastructure pour mettre à jour de la commande interface utilisateur pour l’option de menu Collage spécial.|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Appelé par l’infrastructure pour mettre à jour de la commande interface utilisateur pour l’option de menu Coller.|  
  
## <a name="remarks"></a>Notes  
 `COleDocument` est dérivé de `CDocument`, ce qui permet à vos applications OLE à utiliser l’architecture document/vue fournie par la bibliothèque Microsoft Foundation Class.  
  
 `COleDocument` traite un document comme une collection de [CDocItem](../../mfc/reference/cdocitem-class.md) objets pour traiter les éléments OLE. Applications conteneur et serveur nécessitent une telle architecture, car leurs documents doivent être en mesure de contenir des éléments OLE. Le [COleServerItem](../../mfc/reference/coleserveritem-class.md) et [COleClientItem](../../mfc/reference/coleclientitem-class.md) des classes, tous deux dérivés de `CDocItem`, gérer les interactions entre les applications et des éléments OLE.  
  
 Si vous écrivez une application de conteneur simple, dérivez votre classe de document de `COleDocument`. Si vous écrivez une application de conteneur qui prend en charge la liaison aux éléments incorporés contenues par ses documents, dérivez votre classe de document de [COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md). Si vous écrivez un serveur d’application ou combinaison conteneur/serveur, dérivez votre classe de document de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` et `COleServerDoc` sont dérivés de `COleDocument`, de sorte que ces classes héritent de tous les services disponibles dans `COleDocument` et `CDocument`.  
  
 Pour utiliser `COleDocument`, dérivez une classe à partir de celui-ci et ajouter des fonctionnalités pour gérer l’application non-OLE données ainsi que les éléments liés ou incorporés. Si vous définissez `CDocItem`-les classes dérivées pour stocker les données d’application native, vous pouvez utiliser l’implémentation par défaut définie par `COleDocument` pour stocker votre OLE et les données non OLE. Vous pouvez également concevoir vos propres structures de données pour le stockage des données non-OLE séparément à partir des éléments OLE. Pour plus d’informations, consultez l’article [conteneurs : fichiers composés](../../mfc/containers-compound-files.md)...  
  
 `CDocument` prend en charge l’envoi de votre document par e-mail si la prise en charge de messagerie (MAPI) est présente. `COleDocument` a mis à jour [OnFileSendMail](#onfilesendmail) pour gérer correctement les documents composés. Pour plus d’informations, consultez les articles [MAPI](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 Appelez cette fonction pour ajouter un élément au document.  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointeur vers l’élément de document en cours d’ajout.  
  
### <a name="remarks"></a>Notes  
 Vous n’avez pas besoin d’appeler explicitement cette fonction quand elle est appelée par le `COleClientItem` ou `COleServerItem` constructeur qui accepte un pointeur vers un document.  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 Appelez cette fonction pour modifier le périphérique cible à l’impression pour toutes les incorporé [COleClientItem](../../mfc/reference/coleclientitem-class.md) éléments dans le document du conteneur de votre application.  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Paramètres  
 *ptd*  
 Pointeur vers un `DVTARGETDEVICE` structure de données qui contient des informations sur le nouveau périphérique cible à l’impression. Peut être NULL.  
  
 *PPD*  
 Pointeur vers un `PRINTDLG` structure de données qui contient des informations sur le nouveau périphérique cible à l’impression. Peut être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction met à jour le périphérique d’impression pour tous les éléments, mais elle n’actualise pas le cache de présentation pour ces éléments. Pour mettre à jour le cache de présentation pour un élément, appelez [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).  
  
 Les arguments de cette fonction contiennent des informations OLE utilise pour identifier l’appareil cible. Le [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) structure contient des informations Windows utilise pour initialiser la boîte de dialogue d’impression commune. Une fois que l’utilisateur ferme la boîte de dialogue, Windows retourne des informations sur les sélections d’utilisateur dans cette structure. Le `m_pd` membre d’un [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objet est un `PRINTDLG` structure.  
  
 Pour plus d’informations, consultez le [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez le [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) structure dans le SDK Windows.  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 Construit un objet `COleDocument`.  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 Appelez cette fonction si vous souhaitez stocker le document en utilisant le format de fichier composé.  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bActivez*  
 Spécifie si la prise en charge de fichier composé est activé ou désactivé.  
  
### <a name="remarks"></a>Notes  
 Cela est également appelée stockage structuré. Vous appelez généralement cette fonction à partir du constructeur de votre `COleDocument`-classe dérivée. Pour plus d’informations sur les documents composés, consultez l’article [conteneurs : fichiers composés](../../mfc/containers-compound-files.md)...  
  
 Si vous n’appelez pas cette fonction membre, les documents sont stockés dans un format non structuré (« plate »).  
  
 Une fois que la prise en charge de fichier composé est activé ou désactivé pour un document, le paramètre ne doit pas être modifié pendant la durée de vie du document.  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 Appel de cette fonction pour obtenir le OLE d’élément qui est actuellement activé sur place dans la fenêtre frame contenant l’affichage identifié par *pWnd*.  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers la fenêtre qui affiche le document conteneur.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’unique, in situ OLE élément actif ; NULL s’il n’existe actuellement aucun élément OLE dans un état « actif sur place ».  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments de client dans votre document.  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *points de vente*  
 Une référence à une POSITION a de valeur par un appel précédent à `GetNextClientItem`; la valeur initiale est retournée par la `GetStartPosition` fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le client suivant dans le document d’élément, ou NULL si aucun élément client plus.  
  
### <a name="remarks"></a>Notes  
 Après chaque appel, la valeur de *pos* est définie pour l’élément suivant dans le document, qui peut ou ne peut pas un élément client.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments dans votre document.  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *points de vente*  
 Une référence à une POSITION a de valeur par un appel précédent à `GetNextItem`; la valeur initiale est retournée par la `GetStartPosition` fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’élément de document à la position spécifiée.  
  
### <a name="remarks"></a>Notes  
 Après chaque appel, la valeur de *pos* est définie sur la valeur de la POSITION de l’élément suivant dans le document. Si l’élément récupéré est le dernier élément dans le document, la nouvelle valeur de *pos* a la valeur NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments de serveur dans votre document.  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *points de vente*  
 Une référence à une POSITION a de valeur par un appel précédent à `GetNextServerItem`; la valeur initiale est retournée par la `GetStartPosition` fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le serveur suivant dans le document d’élément, ou NULL si aucun élément de serveur plus.  
  
### <a name="remarks"></a>Notes  
 Après chaque appel, la valeur de *pos* est définie pour l’élément suivant dans le document, qui peut ou ne peut pas un élément de serveur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 Appelé par l’infrastructure pour récupérer l’élément OLE actuellement sélectionné dans la vue spécifiée.  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>Paramètres  
 *pView*  
 Pointeur vers l’objet de vue active affichant le document.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’élément OLE unique, sélectionné ; NULL si aucun élément OLE n’est sélectionnées ou s’il y a plusieurs est sélectionné.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut recherche des éléments pour un seul élément sélectionné de la liste de relation contenant-contenu OLE et retourne un pointeur vers elle. Si aucun élément sélectionné, ou s’il existe plus d’un élément sélectionné, la fonction retourne NULL. Vous devez substituer la `CView::IsSelected` fonction membre dans votre classe d’affichage pour cette fonction à utiliser. Remplacez cette fonction si vous avez votre propre méthode de stockage de relation contenant-contenu des éléments OLE.  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 Appelez cette fonction pour obtenir la position du premier élément dans le document.  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur POSITION qui peut être utilisée pour commencer l’itération au sein des éléments du document ; NULL si le document n’a aucun élément.  
  
### <a name="remarks"></a>Notes  
 Passez la valeur retournée pour `GetNextItem`, `GetNextClientItem`, ou `GetNextServerItem`.  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 Appelez cette fonction pour déterminer si le document contient des éléments vides.  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document contient des éléments vides ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Un élément vide est une dont le rectangle est vide.  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 Affiche la boîte de dialogue OLE changer d’icône et modifie l’icône représentant l’élément OLE actuellement sélectionné à l’icône de que l’utilisateur sélectionne dans la boîte de dialogue.  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>Notes  
 `OnEditChangeIcon` Crée et lance un `COleChangeIconDialog` boîte de dialogue Changer d’icône.  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 Affiche la boîte de dialogue Convertir OLE et convertit ou Active l’élément OLE actuellement sélectionné en fonction des sélections de l’utilisateur dans la boîte de dialogue.  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>Notes  
 `OnEditConvert` Crée et lance un `COleConvertDialog` boîte de dialogue Convertir.  
  
 Un exemple de conversion convertit un document Microsoft Word dans un document WordPad.  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 Affiche la boîte de dialogue OLE/liens d’édition.  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>Notes  
 `OnEditLinks` Crée et lance un `COleLinksDialog` boîte de dialogue de liens qui autorise l’utilisateur à modifier les objets liés.  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 Envoie un message par le biais de l’hôte de messagerie résident (le cas échéant) avec le document en tant que pièce jointe.  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>Notes  
 `OnFileSendMail` appels `OnSaveDocument` pour sérialiser (des documents sans titre et modifiés dans un fichier temporaire, qui est ensuite envoyé par courrier électronique Enregistrer). Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire ; la version d’origine est envoyée. `OnFileSendMail` charge MAPI32. DLL s’il n’a pas déjà été chargé.  
  
 Contrairement à l’implémentation de `OnFileSendMail` pour `CDocument`, cette fonction gère correctement les fichiers composés.  
  
 Pour plus d’informations, consultez le [MAPI rubriques](../../mfc/mapi.md) et [prise en charge MAPI dans MFC](../../mfc/mapi-support-in-mfc.md) articles...  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 L’infrastructure appelle cette fonction après une visibilité du document changements d’état.  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>Paramètres  
 *bVisible*  
 Indique si le document est visible ou invisible.  
  
### <a name="remarks"></a>Notes  
 La version par défaut de cette fonction ne fait rien. Remplacer si votre application doit effectuer un traitement spécial lors de la visibilité du document change.  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 Appelé par l’infrastructure pour mettre à jour de la commande Changer d’icône dans le menu Edition.  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un `CCmdUI` structure qui représente le menu qui a généré la commande de mise à jour. Les appels de gestionnaire de mise à jour le `Enable` fonction membre de la `CCmdUI` structure via *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
### <a name="remarks"></a>Notes  
 `OnUpdateEditChangeIcon` met à jour d’interface d’utilisateur de la commande en fonction de la nécessité ou non une icône valide existe dans le document. Remplacez cette fonction pour modifier le comportement.  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 Appelé par l’infrastructure pour mettre à jour de la commande de liens dans le menu Edition.  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un `CCmdUI` structure qui représente le menu qui a généré la commande de mise à jour. Les appels de gestionnaire de mise à jour le `Enable` fonction membre de la `CCmdUI` structure via *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
### <a name="remarks"></a>Notes  
 En commençant par le premier élément OLE dans le document, `OnUpdateEditLinksMenu` accède à chaque élément, teste si l’élément est un lien et s’il s’agit d’un lien, Active la commande de liens. Remplacez cette fonction pour modifier le comportement.  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 Appelé par l’infrastructure pour mettre à jour le *ObjectName* commande sur le menu Edition et le sous-menu verbe accédé à partir de la *ObjectName* commande, où *ObjectName* est le nom de l’objet OLE est incorporé dans le document.  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un `CCmdUI` structure qui représente le menu qui a généré la commande de mise à jour. Les appels de gestionnaire de mise à jour le `Enable` fonction membre de la `CCmdUI` structure via *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
### <a name="remarks"></a>Notes  
 `OnUpdateObjectVerbMenu` mises à jour le *ObjectName* interface d’utilisateur de la commande en fonction de la nécessité ou non un objet valide existe dans le document. Si un objet existe, le *ObjectName* commande dans le menu Edition est activée. Lorsque cette commande de menu est sélectionnée, le sous-menu de verbe s’affiche. Le sous-menu verbe contient toutes les commandes de verbe disponibles pour l’objet, telles que la modification, propriétés et ainsi de suite. Remplacez cette fonction pour modifier le comportement.  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 Appelé par l’infrastructure pour déterminer si un élément OLE lié peut être collé à partir du Presse-papiers.  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un `CCmdUI` structure qui représente le menu qui a généré la commande de mise à jour. Les appels de gestionnaire de mise à jour le `Enable` fonction membre de la `CCmdUI` structure via *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
### <a name="remarks"></a>Notes  
 La commande de menu Collage spécial est activée ou désactivée selon que l’élément peut être collé dans le document ou non.  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 Appelé par l’infrastructure pour déterminer si un élément OLE incorporé peut être collé à partir du Presse-papiers.  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCmdUI*  
 Un pointeur vers un `CCmdUI` structure qui représente le menu qui a généré la commande de mise à jour. Les appels de gestionnaire de mise à jour le `Enable` fonction membre de la `CCmdUI` structure via *pCmdUI* pour mettre à jour de l’interface utilisateur.  
  
### <a name="remarks"></a>Notes  
 Le bouton et une commande de menu Coller sont activées ou désactivées selon si l’élément peut être collé dans le document ou non.  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 Appelez cette fonction pour supprimer un élément du document.  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointeur vers l’élément de document à supprimer.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous n’avez pas besoin d’appeler cette fonction explicitement ; elle est appelée par les destructeurs pour `COleClientItem` et `COleServerItem`.  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 Appelez cette fonction pour marquer le document comme modifié si un des éléments OLE contenus ont été modifié.  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>Notes  
 Ainsi, l’infrastructure pour inviter l’utilisateur à enregistrer le document avant de fermer, même si les données natives dans le document n’a pas été modifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC conteneur](../../visual-cpp-samples.md)   
 [Exemple MFC MFCBIND](../../visual-cpp-samples.md)   
 [CDocument (classe)](../../mfc/reference/cdocument-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



