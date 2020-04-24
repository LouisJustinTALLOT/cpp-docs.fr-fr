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
ms.openlocfilehash: 1500035cb8be3036678090918154829aace48d2f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753875"
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
|[COleDocument::AddItem](#additem)|Ajoute un élément à la liste des éléments conservés par le document.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Définit l’appareil d’impression cible pour tous les éléments clients du document.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Les documents sont stockés à l’aide du format de fichier OLE Structured Storage.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Retourne l’article OLE qui est actuellement actif sur place.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Obtient le prochain article client pour itérer.|
|[COleDocument::GetNextItem](#getnextitem)|Obtient le prochain élément de document pour itérer.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Obtient le prochain élément serveur pour itérer.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Renvoie l’élément OLE sélectionné principal dans le document.|
|[COleDocument::GetStartPosition](#getstartposition)|Obtient la position initiale pour commencer l’itération.|
|[COleDocument::HasBlankItems](#hasblankitems)|Vérifie les éléments vierges dans le document.|
|[COleDocument::OnShowViews](#onshowviews)|Appelé lorsque le document devient visible ou invisible.|
|[COleDocument::RemoveItem](#removeitem)|Supprime un élément de la liste des éléments conservés par le document.|
|[COleDocument::Mise à jourModifiedFlag](#updatemodifiedflag)|Indique que le document est modifié si l’un des éléments OLE contenus a été modifié.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Gère les événements dans la commande de menu Change Icon.|
|[COleDocument::OnEditConvert](#oneditconvert)|Gère la conversion d’un objet intégré ou lié d’un type à l’autre.|
|[COleDocument::OnEditLinks](#oneditlinks)|Gère les événements de la commande Links sur le menu Edit.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Envoie un message postal avec le document ci-joint.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Appelé par le cadre pour mettre à jour l’interface utilisateur de commande pour l’option de menu Edit/Change Icon.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Appelé par le cadre pour mettre à jour l’interface utilisateur de commande pour l’option de menu Edit/Links.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Appelé par le cadre pour mettre à jour l’interface utilisateur de commande pour l’option de menu Edit/ *ObjectName* et le sous-mois Verb accessible à partir d’Edit/ *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Appelé par le cadre pour mettre à jour l’interface utilisateur de commande pour l’option de menu spécial Pâte.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Appelé par le cadre pour mettre à jour l’interface utilisateur de commande pour l’option de menu Pâte.|

## <a name="remarks"></a>Notes

`COleDocument`est dérivé `CDocument`de , qui permet à vos applications OLE d’utiliser l’architecture de document /vue fournie par la Microsoft Foundation Class Library.

`COleDocument`traite un document comme une collection d’objets [CDocItem](../../mfc/reference/cdocitem-class.md) pour manipuler des éléments OLE. Les applications de conteneurs et de serveurs nécessitent une telle architecture parce que leurs documents doivent être en mesure de contenir des éléments OLE. Les classes [COleServerItem](../../mfc/reference/coleserveritem-class.md) et [COleClientItem,](../../mfc/reference/coleclientitem-class.md) toutes deux dérivées de `CDocItem`, gèrent les interactions entre les applications et les éléments OLE.

Si vous écrivez une simple application de `COleDocument`conteneur, retirez votre classe de documents de . Si vous écrivez une application de conteneurs qui prend en charge la liaison vers les éléments intégrés contenus par ses documents, dérivez votre classe de documents de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Si vous écrivez une application serveur ou un conteneur/serveur de combinaison, dérivez votre classe de documents de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc`et `COleServerDoc` sont `COleDocument`dérivés de , de sorte `COleDocument` `CDocument`que ces classes héritent de tous les services disponibles dans et .

Pour `COleDocument`utiliser , en tirer une classe et ajouter des fonctionnalités pour gérer les données non-OLE de l’application ainsi que les éléments intégrés ou liés. Si vous `CDocItem`définissez les classes dérivées pour stocker les données natives de l’application, vous pouvez utiliser la implémentation par défaut définie par `COleDocument` le stockage de vos données OLE et non-OLE. Vous pouvez également concevoir vos propres structures de données pour stocker vos données non-OLE séparément des éléments OLE. Pour plus d’informations, voir l’article [Containers: Compound Files](../../mfc/containers-compound-files.md)..

`CDocument`prend en charge l’envoi de votre document par la poste si le support postal (MAPI) est présent. `COleDocument`a mis à jour [OnFileSendMail](#onfilesendmail) pour traiter correctement les documents composés. Pour plus d’informations, voir les articles [MAPI](../../mfc/mapi.md) et [MAPI Support dans MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::AddItem

Appelez cette fonction pour ajouter un élément au document.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur sur l’élément document ajouté.

### <a name="remarks"></a>Notes

Vous n’avez pas besoin d’appeler cette `COleClientItem` `COleServerItem` fonction explicitement quand il est appelé par le ou le constructeur qui accepte un pointeur à un document.

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Appelez cette fonction pour modifier l’appareil d’impression cible pour tous les éléments [COleClientItem](../../mfc/reference/coleclientitem-class.md) intégrés dans le document de conteneur de votre application.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Paramètres

*Ptd*<br/>
Pointeur `DVTARGETDEVICE` vers une structure de données, qui contient des informations sur le nouvel appareil d’impression-cible. Sa valeur peut être NULL.

*Ppd*<br/>
Pointeur `PRINTDLG` vers une structure de données, qui contient des informations sur le nouvel appareil d’impression-cible. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction met à jour l’appareil d’impression cible pour tous les éléments, mais ne rafraîchit pas le cache de présentation pour ces éléments. Pour mettre à jour le cache de présentation pour un élément, appelez [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Les arguments de cette fonction contiennent des informations qu’OLE utilise pour identifier le dispositif cible. La structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) contient des informations que Windows utilise pour initialiser la boîte de dialogue imprimée commune. Après que l’utilisateur ferme la boîte de dialogue, Windows renvoie des informations sur les sélections de l’utilisateur dans cette structure. Le `m_pd` membre d’un objet [CPrintDialog](../../mfc/reference/cprintdialog-class.md) est une `PRINTDLG` structure.

Pour plus d’informations, voir la structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) dans le SDK Windows.

Pour plus d’informations, voir la structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) dans le SDK Windows.

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument

Construit un objet `COleDocument`.

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Appelez cette fonction si vous souhaitez stocker le document à l’aide du format composé-fichier.

```cpp
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Précise si la prise en charge des fichiers composé est activée ou désactivée.

### <a name="remarks"></a>Notes

C’est ce qu’on appelle également le stockage structuré. Vous appelez généralement cette fonction du `COleDocument`constructeur de votre classe dérivée. Pour plus d’informations sur les documents [composés,](../../mfc/containers-compound-files.md)voir l’article Containers: Compound Files ..

Si vous n’appelez pas cette fonction de membre, les documents seront stockés dans un format de fichier non structuré (« plat »).

Une fois que la prise en charge du fichier composé est activée ou désactivée pour un document, le paramètre ne doit pas être modifié au cours de la durée de vie du document.

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Appelez cette fonction pour obtenir l’élément OLE qui est actuellement activé en place dans la fenêtre de cadre contenant la vue identifiée par *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers la fenêtre qui affiche le document de conteneur.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’élément OLE actif unique et en place; NULL s’il n’y a pas d’élément OL ACTUELLEMENT dans l’état « actif sur place ».

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments clients de votre document.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Une référence à une valeur POSITION `GetNextClientItem`fixée par un appel précédent à ; la valeur initiale est `GetStartPosition` retournée par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le prochain élément client dans le document, ou NULL s’il n’y a plus d’éléments clients.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur du *pos* est définie pour l’élément suivant dans le document, qui peut ou non être un élément client.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments de votre document.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Une référence à une valeur POSITION `GetNextItem`fixée par un appel précédent à ; la valeur initiale est `GetStartPosition` retournée par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément de document à la position spécifiée.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur du *pos* est définie à la valeur POSITION de l’élément suivant dans le document. Si l’élément récupéré est le dernier élément du document, la nouvelle valeur de *pos* est NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Appelez cette fonction à plusieurs reprises pour accéder à chacun des éléments serveur de votre document.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Une référence à une valeur POSITION `GetNextServerItem`fixée par un appel précédent à ; la valeur initiale est `GetStartPosition` retournée par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’élément serveur suivant dans le document, ou NULL s’il n’y a plus d’éléments serveur.

### <a name="remarks"></a>Notes

Après chaque appel, la valeur de *pos* est définie pour l’élément suivant dans le document, qui peut ou non être un élément serveur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Appelé par le cadre pour récupérer l’élément OLE actuellement sélectionné dans la vue spécifiée.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Paramètres

*pView (en)*<br/>
Pointeur vers l’objet de vue actif affichant le document.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément OLE unique et sélectionné; NULL si aucun élément OLE n’est sélectionné ou si plus d’un est sélectionné.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut recherche la liste des éléments OLE contenus pour un seul élément sélectionné et y renvoie un pointeur. S’il n’y a pas d’élément sélectionné, ou s’il y a plus d’un élément sélectionné, la fonction renvoie NULL. Vous devez remplacer `CView::IsSelected` la fonction de membre dans votre classe de vue pour que cette fonction fonctionne. Remplacer cette fonction si vous avez votre propre méthode de stockage contenu articles OLE.

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition

Appelez cette fonction pour obtenir la position du premier élément dans le document.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui peut être utilisée pour commencer à itérer à travers les éléments du document; NULL si le document n’a pas d’éléments.

### <a name="remarks"></a>Notes

Passer la valeur `GetNextItem`retournée `GetNextClientItem`à `GetNextServerItem`, , ou .

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::HasBlankItems

Appelez cette fonction pour déterminer si le document contient des éléments vierges.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le document contient des éléments vierges; sinon 0.

### <a name="remarks"></a>Notes

Un élément vierge est celui dont le rectangle est vide.

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Affiche la boîte de dialogue OLE Change Icon et modifie l’icône représentant l’élément OL actuellement sélectionné à l’icône que l’utilisateur sélectionne dans la boîte de dialogue.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Notes

`OnEditChangeIcon`crée et `COleChangeIconDialog` lance une boîte de dialogue Change Icon.

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert

Affiche la boîte de dialogue OLE Convert et convertit ou active l’élément OLE actuellement sélectionné en fonction des sélections des utilisateurs dans la boîte de dialogue.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Notes

`OnEditConvert`crée et `COleConvertDialog` lance une boîte de dialogue Convert.

Un exemple de conversion est la conversion d’un document Microsoft Word en un document WordPad.

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks

Affiche la boîte de dialogue OLE Edit/Links.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Notes

`OnEditLinks`crée et `COleLinksDialog` lance une boîte de dialogue Links qui permet à l’utilisateur de changer les objets liés.

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Envoie un message via l’hébergeur de courrier résident (le cas échéant) avec le document comme pièce jointe.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Notes

`OnFileSendMail`appels `OnSaveDocument` à sérialiser (enregistrer) des documents sans titre et modifiés à un fichier temporaire, qui est ensuite envoyé par courrier électronique. Si le document n’a pas été modifié, un fichier temporaire n’est pas nécessaire; l’original est envoyé. `OnFileSendMail`charge MAPI32. DLL s’il n’a pas déjà été chargé.

Contrairement à `OnFileSendMail` la `CDocument`mise en œuvre de , cette fonction gère les fichiers composés correctement.

Pour plus d’informations, consultez les [articles MAPI Topics](../../mfc/mapi.md) and [MAPI Support in MFC.](../../mfc/mapi-support-in-mfc.md)

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews

Le cadre appelle cette fonction après les changements de visibilité du document.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Paramètres

*bVisible*<br/>
Indique si le document est devenu visible ou invisible.

### <a name="remarks"></a>Notes

La version par défaut de cette fonction ne fait rien. Remplacez-le si votre application doit effectuer un traitement spécial lorsque la visibilité du document change.

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Appelé par le cadre pour mettre à jour la commande Change Icon sur le menu Edit.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur `CCmdUI` vers une structure qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de `Enable` mise à `CCmdUI` jour appelle la fonction membre de la structure par *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

`OnUpdateEditChangeIcon`met à jour l’interface utilisateur de la commande en fonction de l’existence ou non d’une icône valide dans le document. Remplacer cette fonction pour changer le comportement.

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Appelé par le cadre pour mettre à jour la commande Links sur le menu Edit.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur `CCmdUI` vers une structure qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de `Enable` mise à `CCmdUI` jour appelle la fonction membre de la structure par *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

En commençant par le premier élément `OnUpdateEditLinksMenu` OLE dans le document, accède à chaque élément, teste si l’élément est un lien, et, s’il s’agit d’un lien, permet la commande Links. Remplacer cette fonction pour changer le comportement.

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Appelé par le cadre pour mettre à jour la commande *ObjectName* sur le menu Edit et le sous-mois Verb accessible à partir de la commande *ObjectName,* où *ObjectName* est le nom de l’objet OLE intégré dans le document.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur `CCmdUI` vers une structure qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de `Enable` mise à `CCmdUI` jour appelle la fonction membre de la structure par *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

`OnUpdateObjectVerbMenu`met à jour l’interface utilisateur de la commande *ObjectName* en fonction de l’existence ou non d’un objet valide dans le document. En cas d’existence d’un objet, la commande ObjectName sur le menu Edit est *activée.* Lorsque cette commande de menu est sélectionnée, le sous-mois Verb est affiché. Le sous-mois Verb contient toutes les commandes de verbe disponibles pour l’objet, tels que Edit, Propriétés, et ainsi de suite. Remplacer cette fonction pour changer le comportement.

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Appelé par le cadre pour déterminer si un élément OLE lié peut être collé à partir du Clipboard.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur `CCmdUI` vers une structure qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de `Enable` mise à `CCmdUI` jour appelle la fonction membre de la structure par *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

La commande de menu spécial Pâte est activée ou désactivée selon que l’élément peut être collé dans le document ou non.

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Appelé par le cadre pour déterminer si un élément OLE intégré peut être collé à partir du Clipboard.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur `CCmdUI` vers une structure qui représente le menu qui a généré la commande de mise à jour. Le gestionnaire de `Enable` mise à `CCmdUI` jour appelle la fonction membre de la structure par *pCmdUI* pour mettre à jour l’interface utilisateur.

### <a name="remarks"></a>Notes

La commande et le bouton du menu Pâte sont activés ou désactivés selon que l’élément peut être collé dans le document ou non.

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::RemoveItem

Appelez cette fonction pour supprimer un élément du document.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur sur l’élément document à supprimer.

### <a name="remarks"></a>Notes

En général, vous n’avez pas besoin d’appeler cette fonction explicitement; il est appelé par les `COleClientItem` `COleServerItem`destructeurs pour et .

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::Mise à jourModifiedFlag

Appelez cette fonction pour marquer le document tel qu’il est modifié si l’un des éléments OLE contenus a été modifié.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Notes

Cela permet au cadre d’inciter l’utilisateur à enregistrer le document avant la fermeture, même si les données natives du document n’ont pas été modifiées.

## <a name="see-also"></a>Voir aussi

[CONTENEUR d’échantillon de MFC](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
