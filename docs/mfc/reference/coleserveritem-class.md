---
title: COleServerItem, classe
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: 5373075cf6dfc54e6e2368e46f48f317fcec64d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376113"
---
# <a name="coleserveritem-class"></a>COleServerItem, classe

Fournit l'interface serveur aux éléments OLE.

## <a name="syntax"></a>Syntaxe

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Construit un objet `COleServerItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Place les formats de `COleDataSource` présentation et de conversion dans un objet.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copie l’article au Clipboard.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Effectue une opération de drag-and-drop.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtient la source de données pour une utilisation dans le transfert de données (drag and drop ou Clipboard).|
|[COleServerItem::GetDocument](#getdocument)|Retourne le document serveur qui contient l’élément.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtient les données CF_EMBEDSOURCE pour un élément OLE.|
|[COleServerItem::GetItemName](#getitemname)|Retourne le nom de l’article. Utilisé uniquement pour les articles liés.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtient les données CF_LINKSOURCE pour un élément OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtient les données CF_OBJECTDESCRIPTOR pour un élément OLE.|
|[COleServerItem::IsConnected](#isconnected)|Indique si l’article est actuellement attaché à un conteneur actif.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indique si l’élément représente un élément OLE lié.|
|[COleServerItem::NotifyChanged](#notifychanged)|Mise à jour de tous les conteneurs avec mise à jour automatique de lien.|
|[COleServerItem::OnDoVerb](#ondoverb)|Appelé pour exécuter un verbe.|
|[COleServerItem::OnDraw](#ondraw)|Appelé lorsque le conteneur demande de dessiner l’article; mise en œuvre requise.|
|[COleServerItem::OnDrawEx](#ondrawex)|Appelé pour le dessin d’objets spécialisés.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Appelé par le cadre pour obtenir les données qui seraient copiées sur le Clipboard.|
|[COleServerItem::OnGetExtent](#ongetextent)|Appelé par le cadre pour récupérer la taille de l’élément OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Appelé par le cadre pour initialiser un élément OLE en utilisant le contenu de l’objet de transfert de données spécifié.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Appelé pour déterminer si des éléments liés doivent être mis à jour.|
|[COleServerItem::OnRenderData](#onrenderdata)|Récupère les données dans le cadre du rendu retardé.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Récupère des données `CFile` dans un objet dans le cadre du rendu retardé.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Récupère les données dans un HGLOBAL dans le cadre du rendu retardé.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Appelé pour définir le schéma de couleurs de l’article.|
|[COleServerItem::OnSetData](#onsetdata)|Appelé pour définir les données de l’élément.|
|[COleServerItem::OnSetExtent](#onsetextent)|Appelé par le cadre pour définir la taille de l’élément OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Appelé quand une partie du document l’élément appartient à est changé.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Appelé à mettre à jour le cache de présentation de tous les éléments du document serveur.|
|[COleServerItem::SetItemName](#setitemname)|Définit le nom de l’élément. Utilisé uniquement pour les articles liés.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Utilise l’objet pour stocker les formats de conversion.|
|[COleServerItem::OnHide](#onhide)|Appelé par le cadre pour cacher l’article OLE.|
|[COleServerItem::OnOpen](#onopen)|Appelé par le cadre pour afficher l’élément OLE dans sa propre fenêtre de haut niveau.|
|[COleServerItem::OnShow](#onshow)|Appelé lorsque le conteneur demande de montrer l’article.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informe le serveur sur la quantité visible de l’élément OLE.|

## <a name="remarks"></a>Notes

Un élément lié peut représenter une partie ou la totalité d’un document serveur. Un élément intégré représente toujours un document serveur entier.

La `COleServerItem` classe définit plusieurs fonctions de membre primordiales qui sont appelées par les bibliothèques de liaison dynamique du système OLE (DLL), généralement en réponse aux demandes de l’application de conteneurs. Ces fonctions membres permettent à l’application de conteneur de manipuler indirectement l’article de diverses manières, par exemple en l’affichant, en exécutant ses verbes ou en récupérant ses données dans différents formats.

Pour `COleServerItem`utiliser , en tirer une classe et mettre en œuvre les fonctions des membres [OnDraw](#ondraw) et [Serialize.](../../mfc/reference/cobject-class.md#serialize) La `OnDraw` fonction fournit la représentation métaafile d’un élément, ce qui lui permet d’être affiché lorsqu’une application de conteneur ouvre un document composé. La `Serialize` fonction `CObject` de fournit la représentation native d’un élément, permettant un élément intégré d’être transféré entre le serveur et les applications de conteneur. [OnGetExtent](#ongetextent) fournit la taille naturelle de l’article au conteneur, permettant au conteneur de tailler l’article.

Pour plus d’informations sur les serveurs et les sujets connexes, voir l’article [Serveurs: Implémenter un serveur](../../mfc/servers-implementing-a-server.md) et "Créer une application conteneur/serveur" dans l’article [Containers: Advanced Features](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData

Appelez cette fonction pour placer les formats de présentation `COleDataSource` et de conversion pour l’élément OLE dans l’objet spécifié.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Paramètres

*pDataSource (en)*<br/>
Pointeur `COleDataSource` vers l’objet dans lequel les données doivent être placées.

### <a name="remarks"></a>Notes

Vous devez avoir implémenté la fonction membre [OnDraw](#ondraw) pour fournir le format de présentation (une image métaafile) pour l’élément. Pour prendre en charge d’autres formats de conversion, enregistrez-les à l’aide de [l’objet COleDataSource](../../mfc/reference/coledatasource-class.md) retourné par [GetDataSource](#getdatasource) et remplacez la fonction membre [OnRenderData](#onrenderdata) pour fournir des données dans les formats que vous souhaitez prendre en charge.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem

Construit un `COleServerItem` objet et l’ajoute à la collection d’éléments de document du document du document serveur.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*pServerDoc*<br/>
Pointeur vers le document qui contiendra le nouvel élément.

*bAutoDelete*<br/>
Indicateur indiquant si l’objet peut être supprimé lorsqu’un lien vers lui est libéré. Définissez ceci à `COleServerItem` FALSE si l’objet fait partie intégrante des données de votre document que vous devez supprimer. Définissez ceci à TRUE si l’objet est une structure secondaire utilisée pour identifier une plage dans les données de votre document qui peut être supprimée par le cadre.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard

Appelez cette fonction pour copier l’article OLE au Clipboard.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Paramètres

*bIncludeLink*<br/>
Définissez ceci à TRUE si les données de lien doivent être copiées sur le Clipboard. Définissez ceci à FALSE si votre application serveur ne prend pas en charge les liens.

### <a name="remarks"></a>Notes

La fonction utilise la fonction membre [OnGetClipboardData](#ongetclipboarddata) pour créer un objet [COleDataSource](../../mfc/reference/coledatasource-class.md) contenant les données de l’élément OLE dans les formats pris en charge. La fonction place `COleDataSource` ensuite l’objet sur le Clipboard en utilisant la fonction [COleDataSource::SetClipboard.](../../mfc/reference/coledatasource-class.md#setclipboard) L’objet `COleDataSource` comprend les données natives de l’élément et sa représentation dans CF_METAFILEPICT format, ainsi que les données dans tous les formats de conversion que vous choisissez de prendre en charge. Vous devez avoir implémenté [Serialize](../../mfc/reference/cobject-class.md#serialize) et [OnDraw](#ondraw) pour que cette fonction de membre fonctionne.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop

Appelez `DoDragDrop` la fonction membre pour effectuer une opération de drag-and-drop.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Paramètres

*lpRectItem*<br/>
Rectangle de l’élément à l’écran, en pixels, par rapport à la zone client.

*ptOffset (en anglais)*<br/>
Le décalage de *lpItemRect* où la position de la souris était au moment de la traînée.

*bIncludeLink*<br/>
Définissez ceci à TRUE si les données de lien doivent être copiées sur le Clipboard. Définissez-le à FALSE si votre application ne prend pas en charge les liens.

*dwEffects dwEffects*<br/>
Détermine les effets que la source de drague permettra dans le fonctionnement de la traînée (une combinaison de copier, déplacer et lien).

*lpRectStartDrag*<br/>
Pointeur vers le rectangle qui définit où la traînée commence réellement. Pour plus d'informations, consultez la section Notes qui suit.

### <a name="return-value"></a>Valeur de retour

Une valeur de l’énumération DROPEFFECT. S’il est DROPEFFECT_MOVE, les données d’origine doivent être supprimées.

### <a name="remarks"></a>Notes

L’opération de drag-and-drop ne démarre pas immédiatement. Il attend que le curseur de souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu’à ce qu’un nombre spécifié de millisecondes soient passés. Si *lpRectStartDrag* est NULL, un rectangle par défaut est utilisé de sorte que la traînée commence lorsque le curseur de souris se déplace d’un pixel.

Le délai est spécifié par un paramètre de clé de registre. Vous pouvez modifier le délai en appelant [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp:WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas le délai, une valeur par défaut de 200 millisecondes est utilisée. Le temps de retard de traînée est stocké comme suit :

- Windows NT Drag delay time est stocké dans HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-NT-CurrentVersion-IniFileMapping.win.ini-Windows-DragDelay.

- Windows 3.x Le délai de drag est stocké dans le WIN. Fichier INI, sous la section [Windows».

- Windows 95/98 Le délai de drag est stocké dans une version mise en cache de WIN. Ini.

Pour plus d’informations sur la façon dont les informations sur les retards de traînée sont stockées dans le registre ou le . Fichier INI, voir [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) in the Windows SDK.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData

Appelez cette fonction pour remplir l’objet [COleDataSource](../../mfc/reference/coledatasource-class.md) spécifié avec toutes les données qui seraient copiées sur le Clipboard si vous avez appelé [CopyToClipboard](#copytoclipboard) (les mêmes données seraient également transférées si vous appeliez [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Paramètres

*pDataSource (en)*<br/>
Pointeur `COleDataSource` vers l’objet qui recevra les données de l’élément OLE dans tous les formats pris en charge.

*bIncludeLink*<br/>
VRAI si les données de lien doivent être copiées sur le Clipboard. FALSE si votre application serveur ne prend pas en charge les liens.

*lpOffset (en anglais)*<br/>
Le décalage, en pixels, du curseur de souris de l’origine de l’objet.

*lpSize*<br/>
La taille de l’objet en pixels.

### <a name="remarks"></a>Notes

Cette fonction appelle la fonction membre [GetEmbedSourceData](#getembedsourcedata) pour obtenir les données natives pour l’élément OLE et appelle la fonction membre [AddOtherClipboardData](#addotherclipboarddata) pour obtenir le format de présentation et tous les formats de conversion pris en charge. Si *bIncludeLink* est VRAI, la fonction appelle également [GetLinkSourceData](#getlinksourcedata) pour obtenir les données de lien pour l’élément.

Remplacer cette fonction si vous souhaitez mettre `COleDataSource` des formats dans un `CopyToClipboard`objet avant ou après ces formats fournis par .

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource

Appelez cette fonction pour obtenir l’objet [COleDataSource](../../mfc/reference/coledatasource-class.md) utilisé pour stocker les formats de conversion que l’application serveur prend en charge.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `COleDataSource` sur l’objet utilisé pour stocker les formats de conversion.

### <a name="remarks"></a>Notes

Si vous souhaitez que votre application serveur offre des données dans une variété `COleDataSource` de formats lors des opérations de transfert de données, enregistrez ces formats avec l’objet retourné par cette fonction. Par exemple, si vous souhaitez fournir une représentation CF_TEXT de l’article OLE pour les opérations Clipboard `COleDataSource` ou drag-and-drop, vous `OnRenderXxxData` enregistrez le format avec l’objet que cette fonction retourne, puis passer outre la fonction membre pour fournir les données.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument

Appelez cette fonction pour obtenir un pointeur sur le document qui contient l’élément.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le document qui contient l’élément; NULL si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cela permet l’accès au document serveur que `COleServerItem` vous avez transmis comme argument au constructeur.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData

Appelez cette fonction pour obtenir les données CF_EMBEDSOURCE pour un élément OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) qui recevra les données CF_EMBEDSOURCE pour l’article OLE.

### <a name="remarks"></a>Notes

Ce format comprend les données natives de l’élément. Vous devez avoir `Serialize` mis en œuvre la fonction membre pour que cette fonction fonctionne correctement.

Le résultat peut ensuite être ajouté à une source de données en utilisant [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Pour plus d’informations, voir [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans le SDK Windows.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName

Appelez cette fonction pour obtenir le nom de l’élément.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de l'élément.

### <a name="remarks"></a>Notes

Vous n’appelez généralement cette fonction que pour les éléments liés.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData

Appelez cette fonction pour obtenir les données CF_LINKSOURCE pour un élément OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) qui recevra les données CF_LINKSOURCE pour l’article OLE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Ce format comprend le CLSID décrivant le type de l’élément OLE et les informations nécessaires pour localiser le document contenant l’élément OLE.

Le résultat peut ensuite être ajouté à une source de données avec [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [OnGetClipboardData](#ongetclipboarddata).

Pour plus d’informations, voir [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans le SDK Windows.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData

Appelez cette fonction pour obtenir les données CF_OBJECTDESCRIPTOR pour un élément OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpOffset (en anglais)*<br/>
Décalage du clic de souris à partir du coin supérieur gauche de l’élément OLE. Sa valeur peut être NULL.

*lpSize*<br/>
Taille de l’article OLE. Sa valeur peut être NULL.

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) qui recevra les données CF_OBJECTDESCRIPTOR pour l’article OLE.

### <a name="remarks"></a>Notes

L’information est copiée dans la `STGMEDIUM` structure pointée par *lpStgMedium*. Ce format comprend l’information nécessaire pour le dialogue spécial Pâte.

Pour plus d’informations, voir [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans le SDK Windows.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::IsConnected

Appelez cette fonction pour voir si l’élément OLE est connecté.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément est connecté; sinon 0.

### <a name="remarks"></a>Notes

Un élément OLE est considéré comme connecté si un ou plusieurs conteneurs ont des références à l’article. Un élément est connecté si son nombre de références est supérieur à 0 ou s’il s’agit d’un élément intégré.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem

Appelez cette fonction pour voir si l’élément OLE est un élément lié.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément est un élément lié; sinon 0.

### <a name="remarks"></a>Notes

Un élément est lié si l’élément est valide et n’est pas retourné dans la liste des éléments intégrés du document. Un élément lié peut ou non être connecté à un conteneur.

Il est courant d’utiliser la même classe pour les éléments liés et intégrés. `IsLinkedItem`vous permet de faire des éléments liés se comportent différemment des éléments intégrés, bien que de nombreuses fois le code est commun.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent

Ce membre indique au serveur quelle quantité de l’objet est visible dans le document de conteneur.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut [d’OnSetExtent](#onsetextent) définit ce membre.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyChanged

Appelez cette fonction après que l’élément lié a été modifié.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect (en anglais seulement)*<br/>
Une valeur du recensement DVASPECT qui indique quel aspect de l’élément OLE a changé. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

### <a name="remarks"></a>Notes

Si un élément de conteneur est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications de conteneurs écrites à l’aide de la Microsoft Foundation Class Library, [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelé en réponse.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServerItem::OnDoVerb

Appelé par le cadre pour exécuter le verbe spécifié.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Spécifie le verbe à exécuter. Il peut être l’un des suivants:

|Valeur|Signification|Symbole|
|-----------|-------------|------------|
|0|Primary (verbe)|OLEIVERB_PRIMARY|
|1|Verbe secondaire|(aucune)|
|- 1|Afficher l’élément pour l’édition|OLEIVERB_SHOW|
|- 2|Modifier l’élément dans une fenêtre séparée|OLEIVERB_OPEN|
|- 3|Masquer l’article|OLEIVERB_HIDE|

La valeur -1 est généralement un alias pour un autre verbe. Si l’édition ouverte n’est pas prise en charge, -2 a le même effet que -1. Pour plus de valeurs, voir [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si l’application de conteneur a été écrite avec la bibliothèque de classe de fondation Microsoft, `COleClientItem` cette fonction est appelée lorsque le [COleClientItem: :Activer](../../mfc/reference/coleclientitem-class.md#activate) la fonction membre de l’objet correspondant est appelé. La implémentation par défaut appelle la fonction membre [OnShow](#onshow) si le verbe principal ou OLEIVERB_SHOW est spécifié, [OnOpen](#onopen) si le verbe secondaire ou OLEIVERB_OPEN est spécifié, et [OnHide](#onhide) si OLEIVERB_HIDE est spécifié. L’implémentation par défaut appelle `OnShow` si *iVerb* n’est pas l’un des verbes énumérés ci-dessus.

Remplacez cette fonction si votre verbe principal n’affiche pas l’élément. Par exemple, si l’élément est un enregistrement sonore et son verbe principal est Play, vous n’auriez pas à afficher l’application serveur pour lire l’élément.

Pour plus d’informations, voir [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServerItem::OnDraw

Appelé par le cadre pour rendre l’élément OLE dans un métaafile.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur à l’objet [CDC](../../mfc/reference/cdc-class.md) sur lequel dessiner l’élément. Le contexte d’affichage est automatiquement connecté au contexte d’affichage d’attribut de sorte que vous pouvez appeler des fonctions d’attribut, bien que cela rendrait l’appareil métadafile spécifique.

*rSize (en)*<br/>
Taille, dans les unités HIMETRIC, dans lequel dessiner le metafile.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été tiré avec succès; sinon 0.

### <a name="remarks"></a>Notes

La représentation métaafile de l’élément OLE est utilisée pour afficher l’élément dans l’application de conteneur. Si l’application de conteneur a été écrite avec la bibliothèque de classe Microsoft Foundation, le metafile est utilisé par la fonction [membre Draw](../../mfc/reference/coleclientitem-class.md#draw) de l’objet [COleClientItem](../../mfc/reference/coleclientitem-class.md) correspondant. Il n'y a pas d'implémentation par défaut. Vous devez remplacer cette fonction pour dessiner l’élément dans le contexte de l’appareil spécifié.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawEx

Appelé par le cadre pour tout le dessin.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur à l’objet [CDC](../../mfc/reference/cdc-class.md) sur lequel dessiner l’élément. Le DC est automatiquement connecté à l’attribut DC afin que vous puissiez appeler des fonctions d’attribut, bien que cela rendrait l’appareil métaafile spécifique.

*nDrawAspect (en anglais seulement)*<br/>
Une valeur de l’énumération DVASPECT. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

*rSize (en)*<br/>
Taille de l’article dans les unités HIMETRIC.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été tiré avec succès; sinon 0.

### <a name="remarks"></a>Notes

La mise `OnDraw` en œuvre par défaut passe lorsque DVASPECT est égal à DVASPECT_CONTENT; sinon il échoue.

Remplacer cette fonction pour fournir des données de présentation pour des aspects autres que DVASPECT_CONTENT, tels que DVASPECT_ICON ou DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData

Appelé par le cadre `COleDataSource` pour obtenir un objet contenant toutes les données qui seraient placées sur le Clipboard par un appel à la fonction membre [CopyToClipboard.](#copytoclipboard)

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Paramètres

*bIncludeLink*<br/>
Définissez ceci à TRUE si les données de lien doivent être copiées sur le Clipboard. Définissez ceci à FALSE si votre application serveur ne prend pas en charge les liens.

*lpOffset (en anglais)*<br/>
Le décalage du curseur de souris de l’origine de l’objet en pixels.

*lpSize*<br/>
La taille de l’objet en pixels.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [COleDataSource](../../mfc/reference/coledatasource-class.md) contenant les données Clipboard.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction appelle [GetClipboardData](#getclipboarddata).

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent

Appelé par le cadre pour récupérer la taille, en unités HIMETRIC, de l’élément OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect (en anglais seulement)*<br/>
Spécifie l’aspect de l’article OLE dont les limites doivent être récupérées. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

*rSize (en)*<br/>
Référence à `CSize` un objet qui recevra la taille de l’article OLE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application de conteneur a été écrite avec la bibliothèque de classe microsoft `COleClientItem` Foundation, cette fonction est appelée lorsque la fonction membre [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) de l’objet correspondant est appelée. L'implémentation par défaut n'exécute aucune opération. Vous devez le mettre en œuvre vous-même. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lors de la manipulation d’une demande pour la taille de l’article OLE.

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide

Appelé par le cadre pour cacher l’article OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Notes

Les appels `COleServerDoc::OnShowDocument( FALSE )`par défaut . La fonction informe également le conteneur que l’article OLE a été caché. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de la dissimulation d’un article OLE.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData

Appelé par le cadre pour initialiser un élément OLE en utilisant le contenu de *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Pointeur vers un objet de données OLE contenant des données dans différents formats pour l’initialisation de l’élément OLE.

*bCréation*<br/>
VRAI si la fonction est appelée à initialiser un élément OLE nouvellement créé par une application de conteneur. FALSE si la fonction est appelée pour remplacer le contenu d’un élément OLE déjà existant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si *bCreation* est VRAI, cette fonction est appelée si un conteneur implémente Insérez un nouvel objet basé sur la sélection actuelle. Les données sélectionnées sont utilisées lors de la création du nouvel élément OLE. Par exemple, lors de la sélection d’une gamme de cellules dans un programme de feuilles de calcul, puis en utilisant l’insert Nouveau objet pour créer un graphique basé sur les valeurs de la gamme sélectionnée. L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour choisir un format acceptable parmi ceux offerts par *pDataObject* et initialiser l’élément OLE en fonction des données fournies. C’est un avancé primordial.

Pour plus d’informations, voir [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) in the Windows SDK.

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen

Appelé par le cadre pour afficher l’élément OLE dans un cas distinct de l’application serveur, plutôt que en place.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut active la première fenêtre de cadre affichant le document qui contient l’élément OLE; si l’application est un mini-serveur, l’implémentation par défaut affiche la fenêtre principale. La fonction informe également le conteneur que l’article OLE a été ouvert.

Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lors de l’ouverture d’un élément OLE. Ceci est particulièrement commun avec les éléments liés où vous souhaitez définir la sélection au lien lorsqu’il est ouvert.

Pour plus d’informations, voir [IOleClientSite::OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) dans le Windows SDK.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems

Appelé par le cadre pour déterminer si les éléments liés dans le document serveur actuel sont obsolètes.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a des éléments nécessitant des mises à jour; 0 si tous les articles sont à jour.

### <a name="remarks"></a>Notes

Un élément est périmé si son document source a été modifié, mais l’élément lié n’a pas été mis à jour pour refléter les modifications apportées au document.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderData

Appelé par le cadre pour récupérer les données dans le format spécifié.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) précisant le format dans lequel l’information est demandée.

*lpStgMedium*<br/>
Indique une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans laquelle les données doivent être retournées.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet à l’aide de la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) ou [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction appelle [OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata), respectivement, si le support de stockage fourni est soit un fichier ou une mémoire. Si aucun de ces formats n’est fourni, la implémentation par défaut renvoie 0 et ne fait rien.

Si *lpStgMedium*-> *tymed* est TYMED_NULL, le STGMEDIUM doit être attribué et rempli comme le précise *lpFormatEtc->attaché*. Si ce n’est pas TYMED_NULL, le STGMEDIUM doit être rempli en place avec les données.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous pouvez remplacer l’une des autres versions de cette fonction à la place. Si vos données sont petites et `OnRenderGlobalData`fixes en taille, remplacez . Si vos données sont dans un fichier, ou `OnRenderFileData`sont de taille variable, remplacez .

Pour plus d’informations, voir [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc), et [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) dans le Windows SDK.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData

Appelé par le cadre pour récupérer les données dans le format spécifié lorsque le support de stockage est un fichier.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) précisant le format dans lequel l’information est demandée.

*pFile (en)*<br/>
Indique un `CFile` objet dans lequel les données doivent être rendues.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet en utilisant la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction renvoie simplement FALSE.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous voudrez peut-être passer outre l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données sont dans un fichier, ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata).

Pour plus d’informations, voir [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData

Appelé par le cadre pour récupérer les données dans le format spécifié lorsque le support de stockage spécifié est la mémoire globale.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) précisant le format dans lequel l’information est demandée.

*phGlobal*<br/>
Indique une poignée à la mémoire globale dans laquelle les données doivent être retournées. Si aucune mémoire n’a été allouée, ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet en utilisant la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction renvoie simplement FALSE.

Si *phGlobal* est NULL, alors un nouveau HGLOBAL devrait être attribué et retourné en *phGlobal*. Dans le cas contraire, le HGLOBAL spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le HGLOBAL ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réaffecté à une plus grande taille.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous pouvez remplacer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données sont dans un fichier, ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata).

Pour plus d’informations, voir [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme

Appelé par le cadre pour spécifier une palette de couleurs à utiliser lors de l’édition de l’élément OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Paramètres

*lpLogPalette*<br/>
Pointeur vers une structure [LogPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si la palette de couleurs est utilisée; sinon 0.

### <a name="remarks"></a>Notes

Si l’application de conteneur a été écrite à l’aide de la Microsoft Foundation Class Library, `COleClientItem` cette fonction s’appelle lorsque la fonction [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) fonction de l’objet correspondant est appelé. La implémentation par défaut renvoie FALSE. Remplacez cette fonction si vous souhaitez utiliser la palette recommandée. L’application serveur n’est pas nécessaire pour utiliser la palette suggérée.

Pour plus d’informations, voir [IOleObject:SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) dans le Windows SDK.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServerItem::OnSetData

Appelé par le cadre pour remplacer les données de l’élément OLE par les données spécifiées.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointeur vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) spécifiant le format des données.

*lpStgMedium*<br/>
Pointeur vers une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans laquelle les données résident.

*bRelease (en)*<br/>
Indique qui a la propriété du support de stockage après avoir rempli l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées au nom du support de stockage. L’appelant le fait en définissant *bRelease*. Si *bRelease* n’est paszero, l’élément serveur prend possession, libérant le support quand il a fini de l’utiliser. Lorsque *bRelease* est 0, l’appelant conserve la propriété et l’élément serveur ne peut utiliser le support de stockage que pour la durée de l’appel.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’élément serveur ne s’approprie pas les données tant qu’il n’a pas réussi à l’obtenir. Autrement dit, il n’en prend pas la propriété si elle retourne 0. Si la source de données s’en charge, elle libère le support de stockage en appelant la fonction [ReleaseStgMedium.](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

L'implémentation par défaut n'exécute aucune opération. Remplacer cette fonction pour remplacer les données de l’élément OLE par les données spécifiées. C’est un avancé primordial.

Pour plus d’informations, voir [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc), et [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) dans le Windows SDK.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::OnSetExtent

Appelé par le cadre pour indiquer à l’élément OLE combien d’espace est disponible pour elle dans le document de conteneur.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect (en anglais seulement)*<br/>
Spécifie l’aspect de l’article OLE dont les limites sont spécifiées. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

*Taille*<br/>
Une structure [de taille cSize](../../atl-mfc-shared/reference/csize-class.md) spécifiant la nouvelle taille de l’article OLE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application de conteneur a été écrite avec la bibliothèque de classe Microsoft `COleClientItem` Foundation, cette fonction est appelée lorsque la fonction [membre SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) de l’objet correspondant est appelée. La mise en œuvre par défaut définit le [m_sizeExtent](#m_sizeextent) membre à la taille spécifiée si *nDrawAspect* est DVASPECT_CONTENT; sinon il revient 0. Remplacer cette fonction pour effectuer un traitement spécial lorsque vous modifiez la taille de l’article.

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow

Appelé par le cadre pour instruire l’application serveur pour afficher l’élément OLE en place.

```
virtual void OnShow();
```

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée lorsque l’utilisateur de l’application de conteneur crée un élément ou exécute un verbe, tel que Edit, qui nécessite que l’élément soit affiché. L’implémentation par défaut tente l’activation place. Si cela échoue, la `OnOpen` fonction appelle la fonction membre pour afficher l’élément OLE dans une fenêtre séparée.

Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’un élément OLE est affiché.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate

Appelé par le cadre lorsqu’un élément a été modifié.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Pointeur vers l’élément qui a modifié le document. Sa valeur peut être NULL.

*lHint (en anglais)*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Pointeur vers un objet stockant des informations sur la modification.

*nDrawAspect (en anglais seulement)*<br/>
Une valeur de l’énumération DVASPECT. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle [NotifyChanged](#notifychanged), quel que soit l’indice ou l’expéditeur.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems

Appelé par le cadre pour mettre à jour tous les éléments du document serveur.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Notes

La implémentation par `COleClientItem` défaut appelle [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pour tous les objets du document.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::SetItemName

Appelez cette fonction lorsque vous créez un élément lié pour définir son nom.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName (en)*<br/>
Pointeur vers le nouveau nom de l’élément.

### <a name="remarks"></a>Notes

Le nom doit être unique dans le document. Lorsqu’une application serveur est appelée pour modifier un élément lié, l’application utilise ce nom pour trouver l’élément. Vous n’avez pas besoin d’appeler cette fonction pour les éléments intégrés.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem, classe](../../mfc/reference/cdocitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
