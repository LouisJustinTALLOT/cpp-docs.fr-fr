---
title: COleDocument, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421099"
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
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Définit l’appareil cible d’impression pour tous les éléments clients dans le document.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Fait en sorte que les documents soient stockés à l’aide du format de fichier de stockage structuré OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Retourne l’élément OLE qui est actuellement actif sur place.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Obtient l’élément client suivant pour l’itération.|
|[COleDocument::GetNextItem](#getnextitem)|Obtient l’élément de document suivant pour l’itération.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Obtient l’élément de serveur suivant pour l’itération.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Retourne l’élément OLE sélectionné dans le document.|
|[COleDocument::GetStartPosition](#getstartposition)|Obtient la position initiale à laquelle commencer l’itération.|
|[COleDocument::HasBlankItems](#hasblankitems)|Recherche les éléments vides dans le document.|
|[COleDocument::OnShowViews](#onshowviews)|Appelé lorsque le document devient visible ou invisible.|
|[COleDocument::RemoveItem](#removeitem)|Supprime un élément de la liste des éléments gérés par le document.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Marque le document comme modifié si l’un des éléments OLE qu’il contient a été modifié.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Gère les événements dans la commande de menu changer d’icône.|
|[COleDocument::OnEditConvert](#oneditconvert)|Gère la conversion d’un objet incorporé ou lié d’un type en un autre.|
|[COleDocument::OnEditLinks](#oneditlinks)|Gère les événements dans la commande liens du menu Edition.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Envoie un message électronique avec le document joint.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Appelée par l’infrastructure pour mettre à jour l’interface utilisateur de la commande pour l’option de menu modifier/modifier l’icône.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Appelée par l’infrastructure pour mettre à jour l’interface utilisateur de la commande pour l’option de menu modifier/lier.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Appelée par l’infrastructure pour mettre à jour l’interface utilisateur de la commande pour l’option de menu Edit/ *ObjectName* et le sous-menu de verbes accessible à partir de Edit/ *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Appelée par l’infrastructure pour mettre à jour l’interface utilisateur de la commande pour l’option de menu Collage spécial.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Appelée par l’infrastructure pour mettre à jour l’interface utilisateur de la commande pour l’option de menu coller.|

## <a name="remarks"></a>Notes

`COleDocument` est dérivée de `CDocument`, ce qui permet à vos applications OLE d’utiliser l’architecture document/vue fournie par le bibliothèque MFC (Microsoft Foundation Class).

`COleDocument` traite un document comme une collection d’objets [CDocItem](../../mfc/reference/cdocitem-class.md) pour gérer des éléments OLE. Les applications conteneur et serveur requièrent une telle architecture, car leurs documents doivent pouvoir contenir des éléments OLE. Les classes [COleServerItem](../../mfc/reference/coleserveritem-class.md) et [COleClientItem](../../mfc/reference/coleclientitem-class.md) , dérivées de `CDocItem`, gèrent les interactions entre les applications et les éléments OLE.

Si vous écrivez une application de conteneur simple, dérivez votre classe de document de `COleDocument`. Si vous écrivez une application de conteneur qui prend en charge la liaison aux éléments incorporés contenus dans ses documents, dérivez votre classe de document à partir de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Si vous écrivez une application serveur ou un conteneur/serveur mixte, dérivez votre classe de document à partir de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` et `COleServerDoc` sont dérivés de `COleDocument`, ces classes héritent donc de tous les services disponibles dans `COleDocument` et `CDocument`.

Pour utiliser `COleDocument`, dérivez une classe de celle-ci et ajoutez des fonctionnalités permettant de gérer les données non-OLE de l’application, ainsi que les éléments incorporés ou liés. Si vous définissez des classes dérivées de `CDocItem`pour stocker les données natives de l’application, vous pouvez utiliser l’implémentation par défaut définie par `COleDocument` pour stocker vos données OLE et non-OLE. Vous pouvez également concevoir vos propres structures de données pour le stockage de vos données non-OLE séparément des éléments OLE. Pour plus d’informations, consultez l’article [Containers : Fichiers composés](../../mfc/containers-compound-files.md)..

`CDocument` prend en charge l’envoi de votre document par courrier électronique si la prise en charge de la messagerie (MAPI) est présente. `COleDocument` a mis à jour [OnFileSendMail](#onfilesendmail) pour gérer correctement les documents composés. Pour plus d’informations, consultez les Articles prise en charge [MAPI](../../mfc/mapi.md) et [MAPI dans MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Configuration requise

**En-tête :** AFXOLE. h

##  <a name="additem"></a>  COleDocument::AddItem

Appelez cette fonction pour ajouter un élément au document.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément de document en cours d’ajout.

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’appeler cette fonction explicitement quand elle est appelée par le constructeur `COleClientItem` ou `COleServerItem` qui accepte un pointeur vers un document.

##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice

Appelez cette fonction pour modifier l’appareil cible d’impression pour tous les éléments [COleClientItem](../../mfc/reference/coleclientitem-class.md) incorporés dans le document conteneur de votre application.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Paramètres

*ptd*<br/>
Pointeur vers une structure de données `DVTARGETDEVICE`, qui contient des informations sur le nouvel appareil cible d’impression. Peut avoir la valeur NULL.

*ppd*<br/>
Pointeur vers une structure de données `PRINTDLG`, qui contient des informations sur le nouvel appareil cible d’impression. Peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction met à jour l’appareil cible d’impression pour tous les éléments, mais n’actualise pas le cache de présentation pour ces éléments. Pour mettre à jour le cache de présentation d’un élément, appelez [COleClientItem :: UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Les arguments de cette fonction contiennent des informations utilisées par OLE pour identifier l’appareil cible. La structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) contient des informations que Windows utilise pour initialiser la boîte de dialogue d’impression courante. Une fois que l’utilisateur a fermé la boîte de dialogue, Windows retourne des informations sur les sélections de l’utilisateur dans cette structure. Le membre `m_pd` d’un objet [CPrintDialog](../../mfc/reference/cprintdialog-class.md) est une structure `PRINTDLG`.

Pour plus d’informations, consultez la structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) dans le SDK Windows.

Pour plus d’informations, consultez la structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) dans le SDK Windows.

##  <a name="coledocument"></a>  COleDocument::COleDocument

Construit un objet `COleDocument`.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile

Appelez cette fonction si vous souhaitez stocker le document à l’aide du format de fichier composé.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Spécifie si la prise en charge des fichiers composés est activée ou désactivée.

### <a name="remarks"></a>Notes

C’est ce que l’on appelle également le stockage structuré. En général, vous appelez cette fonction à partir du constructeur de votre classe dérivée de `COleDocument`. Pour plus d’informations sur les documents composés, consultez l’article [Containers : Fichiers composés](../../mfc/containers-compound-files.md)..

Si vous n’appelez pas cette fonction membre, les documents sont stockés dans un format de fichier non structuré (« plat »).

Une fois que la prise en charge des fichiers composés est activée ou désactivée pour un document, le paramètre ne doit pas être modifié pendant la durée de vie du document.

##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem

Appelez cette fonction pour obtenir l’élément OLE actuellement activé sur place dans la fenêtre frame contenant la vue identifiée par *pwnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui affiche le document conteneur.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément OLE actif unique, sur place ; NULL s’il n’existe aucun élément OLE actuellement dans l’état « actif sur place ».

##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments du client dans votre document.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Référence à une valeur de POSITION définie par un appel précédent à `GetNextClientItem`; la valeur initiale est retournée par la fonction membre `GetStartPosition`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément client suivant dans le document, ou NULL s’il n’y a plus d’éléments client.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur *pos* est définie pour l’élément suivant dans le document, qui peut être ou non un élément client.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>  COleDocument::GetNextItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments de votre document.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Référence à une valeur de POSITION définie par un appel précédent à `GetNextItem`; la valeur initiale est retournée par la fonction membre `GetStartPosition`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément de document à la position spécifiée.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur de *pos* est définie sur la valeur de position de l’élément suivant dans le document. Si l’élément récupéré est le dernier élément du document, la nouvelle valeur de *pos* est null.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments de serveur de votre document.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Référence à une valeur de POSITION définie par un appel précédent à `GetNextServerItem`; la valeur initiale est retournée par la fonction membre `GetStartPosition`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément de serveur suivant dans le document, ou NULL s’il n’y a plus d’éléments de serveur.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur *pos* est définie pour l’élément suivant dans le document, qui peut être ou non un élément de serveur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem

Appelé par l’infrastructure pour récupérer l’élément OLE actuellement sélectionné dans la vue spécifiée.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView*<br/>
Pointeur vers l’objet de vue actif affichant le document.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément OLE unique sélectionné ; NULL si aucun élément OLE n’est sélectionné ou si plusieurs éléments sont sélectionnés.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche un seul élément sélectionné dans la liste des éléments OLE contenus et retourne un pointeur vers celui-ci. Si aucun élément n’est sélectionné ou si plusieurs éléments sont sélectionnés, la fonction retourne la valeur NULL. Vous devez substituer la fonction membre `CView::IsSelected` dans votre classe d’affichage pour que cette fonction fonctionne. Remplacez cette fonction si vous avez votre propre méthode de stockage des éléments OLE contenus.

##  <a name="getstartposition"></a>  COleDocument::GetStartPosition

Appelez cette fonction pour récupérer la position du premier élément dans le document.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui peut être utilisée pour commencer l’itération dans les éléments du document ; NULL si le document n’a pas d’éléments.

### <a name="remarks"></a>Notes

Transmettez la valeur retournée à `GetNextItem`, `GetNextClientItem`ou `GetNextServerItem`.

##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems

Appelez cette fonction pour déterminer si le document contient des éléments vides.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document contient des éléments vides ; Sinon, 0.

### <a name="remarks"></a>Notes

Un élément vide est un élément dont le rectangle est vide.

##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon

Affiche la boîte de dialogue icône de modification OLE et remplace l’icône qui représente l’élément OLE actuellement sélectionné par l’icône que l’utilisateur sélectionne dans la boîte de dialogue.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Notes

`OnEditChangeIcon` crée et lance une boîte de dialogue `COleChangeIconDialog` changer d’icône.

##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert

Affiche la boîte de dialogue OLE Convert et convertit ou active l’élément OLE actuellement sélectionné en fonction des sélections de l’utilisateur dans la boîte de dialogue.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Notes

`OnEditConvert` crée et lance une boîte de dialogue `COleConvertDialog` convertir.

Un exemple de conversion consiste à convertir un document Microsoft Word en un document WordPad.

##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks

Affiche la boîte de dialogue OLE modifier/lier.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Notes

`OnEditLinks` crée et lance une boîte de dialogue `COleLinksDialog` des liens qui permet à l’utilisateur de modifier les objets liés.

##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail

Envoie un message via l’hôte de messagerie résident (le cas échéant) avec le document en tant que pièce jointe.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Notes

`OnFileSendMail` appelle `OnSaveDocument` pour sérialiser (enregistrer) les documents sans titre et modifiés dans un fichier temporaire, qui est ensuite envoyé par courrier électronique. Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire. l’original est envoyé. `OnFileSendMail` charge MAPI32. DLL s’il n’a pas déjà été chargé.

Contrairement à l’implémentation de `OnFileSendMail` pour `CDocument`, cette fonction gère correctement les fichiers composés.

Pour plus d’informations, consultez les [rubriques MAPI](../../mfc/mapi.md) et la [prise en charge MAPI dans](../../mfc/mapi-support-in-mfc.md) les articles MFC.

##  <a name="onshowviews"></a>  COleDocument::OnShowViews

L’infrastructure appelle cette fonction une fois que l’état de visibilité du document a été modifié.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Paramètres

*bVisible*<br/>
Indique si le document est devenu visible ou invisible.

### <a name="remarks"></a>Notes

La version par défaut de cette fonction ne fait rien. Remplacez-la si votre application doit effectuer un traitement spécial lorsque la visibilité du document change.

##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon

Appelée par l’infrastructure pour mettre à jour la commande changer d’icône dans le menu Edition.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers une structure `CCmdUI` qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre `Enable` de la structure `CCmdUI` par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

`OnUpdateEditChangeIcon` met à jour l’interface utilisateur de la commande selon qu’il existe ou non une icône valide dans le document. Substituez cette fonction pour modifier le comportement.

##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu

Appelée par l’infrastructure pour mettre à jour la commande des liens dans le menu Edition.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers une structure `CCmdUI` qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre `Enable` de la structure `CCmdUI` par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

En commençant par le premier élément OLE du document, `OnUpdateEditLinksMenu` accède à chaque élément, vérifie si l’élément est un lien et, s’il s’agit d’un lien, active la commande links. Substituez cette fonction pour modifier le comportement.

##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu

Appelée par l’infrastructure pour mettre à jour la commande *ObjectName* dans le menu Edition et le sous-menu de verbes accessible à partir de la commande *ObjectName* , où *ObjectName* est le nom de l’objet OLE incorporé dans le document.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers une structure `CCmdUI` qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre `Enable` de la structure `CCmdUI` par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

`OnUpdateObjectVerbMenu` met à jour l’interface utilisateur de la commande *ObjectName* selon qu’il existe ou non un objet valide dans le document. Si un objet existe, la commande *ObjectName* est activée dans le menu Edition. Quand cette commande de menu est sélectionnée, le sous-menu de verbes s’affiche. Le sous-menu de verbes contient toutes les commandes de verbe disponibles pour l’objet, telles que la modification, les propriétés, etc. Substituez cette fonction pour modifier le comportement.

##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu

Appelé par l’infrastructure pour déterminer si un élément OLE lié peut être collé à partir du presse-papiers.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers une structure `CCmdUI` qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre `Enable` de la structure `CCmdUI` par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

La commande de menu Collage spécial est activée ou désactivée, selon que l’élément peut ou non être collé dans le document.

##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu

Appelé par l’infrastructure pour déterminer si un élément OLE incorporé peut être collé à partir du presse-papiers.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers une structure `CCmdUI` qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de mise à jour appelle la fonction membre `Enable` de la structure `CCmdUI` par le biais de *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

La commande et le bouton de menu coller sont activés ou désactivés selon que l’élément peut ou non être collé dans le document.

##  <a name="removeitem"></a>  COleDocument::RemoveItem

Appelez cette fonction pour supprimer un élément du document.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément de document à supprimer.

### <a name="remarks"></a>Notes

En général, vous n’avez pas besoin d’appeler cette fonction explicitement ; elle est appelée par les destructeurs pour `COleClientItem` et `COleServerItem`.

##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag

Appelez cette fonction pour marquer le document comme modifié si l’un des éléments OLE contenus a été modifié.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Notes

Cela permet à l’infrastructure d’inviter l’utilisateur à enregistrer le document avant de se fermer, même si les données natives du document n’ont pas été modifiées.

## <a name="see-also"></a>Voir aussi

[CONTENEUR d’exemples MFC](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
