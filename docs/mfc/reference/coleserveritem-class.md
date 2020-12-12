---
description: 'En savoir plus sur : COleServerItem, classe'
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
ms.openlocfilehash: 30f99e6ee62406b47a493781586d8ed8b11a60b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226647"
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
|[COleServerItem :: COleServerItem](#coleserveritem)|Construit un objet `COleServerItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleServerItem :: AddOtherClipboardData](#addotherclipboarddata)|Place des formats de présentation et de conversion dans un `COleDataSource` objet.|
|[COleServerItem :: CopyToClipboard](#copytoclipboard)|Copie l’élément dans le presse-papiers.|
|[COleServerItem ::D oDragDrop](#dodragdrop)|Effectue une opération de glisser-déplacer.|
|[COleServerItem :: GetClipboardData](#getclipboarddata)|Obtient la source de données à utiliser dans le transfert de données (glisser-déplacer ou presse-papiers).|
|[COleServerItem :: GetDocument](#getdocument)|Retourne le document serveur qui contient l’élément.|
|[COleServerItem :: GetEmbedSourceData](#getembedsourcedata)|Obtient les données de CF_EMBEDSOURCE pour un élément OLE.|
|[COleServerItem :: GetItemName](#getitemname)|Retourne le nom de l’élément. Utilisé uniquement pour les éléments liés.|
|[COleServerItem :: GetLinkSourceData](#getlinksourcedata)|Obtient les données de CF_LINKSOURCE pour un élément OLE.|
|[COleServerItem :: GetObjectDescriptorData](#getobjectdescriptordata)|Obtient les données de CF_OBJECTDESCRIPTOR pour un élément OLE.|
|[COleServerItem :: IsConnected](#isconnected)|Indique si l’élément est actuellement attaché à un conteneur actif.|
|[COleServerItem :: IsLinkedItem](#islinkeditem)|Indique si l’élément représente un élément OLE lié.|
|[COleServerItem :: NotifyChanged](#notifychanged)|Met à jour tous les conteneurs avec la mise à jour automatique des liaisons.|
|[COleServerItem :: OnDoVerb](#ondoverb)|Appelé pour exécuter un verbe.|
|[COleServerItem :: OnDraw](#ondraw)|Appelé lorsque le conteneur demande à dessiner l’élément ; implémentation requise.|
|[COleServerItem :: OnDrawEx](#ondrawex)|Appelé pour un dessin d’élément spécialisé.|
|[COleServerItem :: OnGetClipboardData](#ongetclipboarddata)|Appelé par l’infrastructure pour récupérer les données qui seraient copiées dans le presse-papiers.|
|[COleServerItem::OnGetExtent](#ongetextent)|Appelé par l’infrastructure pour récupérer la taille de l’élément OLE.|
|[COleServerItem :: OnInitFromData](#oninitfromdata)|Appelé par l’infrastructure pour initialiser un élément OLE à l’aide du contenu de l’objet de transfert de données spécifié.|
|[COleServerItem :: OnQueryUpdateItems](#onqueryupdateitems)|Appelé pour déterminer si des éléments liés nécessitent une mise à jour.|
|[COleServerItem :: OnRenderData](#onrenderdata)|Récupère des données dans le cadre d’un rendu retardé.|
|[COleServerItem :: OnRenderFileData](#onrenderfiledata)|Récupère des données dans un `CFile` objet dans le cadre d’un rendu retardé.|
|[COleServerItem :: OnRenderGlobalData](#onrenderglobaldata)|Récupère des données dans un HGLOBAL dans le cadre du rendu retardé.|
|[COleServerItem :: OnSetColorScheme](#onsetcolorscheme)|Appelé pour définir le modèle de couleurs de l’élément.|
|[COleServerItem :: OnSetData](#onsetdata)|Appelé pour définir les données de l’élément.|
|[COleServerItem::OnSetExtent](#onsetextent)|Appelée par l’infrastructure pour définir la taille de l’élément OLE.|
|[COleServerItem :: OnUpdate](#onupdate)|Appelée lorsqu’une partie du document dans laquelle l’élément appartient est modifiée.|
|[COleServerItem :: OnUpdateItems](#onupdateitems)|Appelé pour mettre à jour le cache de présentation de tous les éléments dans le document serveur.|
|[COleServerItem :: SetItemName](#setitemname)|Définit le nom de l’élément. Utilisé uniquement pour les éléments liés.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleServerItem :: GetDataSource](#getdatasource)|Obtient l’objet utilisé pour stocker les formats de conversion.|
|[COleServerItem :: OnHide](#onhide)|Appelé par l’infrastructure pour masquer l’élément OLE.|
|[COleServerItem :: OnOpen](#onopen)|Appelé par le Framework pour afficher l’élément OLE dans sa propre fenêtre de niveau supérieur.|
|[COleServerItem :: OnShow](#onshow)|Appelé lorsque le conteneur demande l’affichage de l’élément.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleServerItem :: m_sizeExtent](#m_sizeextent)|Informe le serveur sur la quantité de l’élément OLE visible.|

## <a name="remarks"></a>Notes

Un élément lié peut représenter une partie ou la totalité d’un document serveur. Un élément incorporé représente toujours un document serveur entier.

La `COleServerItem` classe définit plusieurs fonctions membres substituables qui sont appelées par les bibliothèques de liens dynamiques (dll) du système OLE, généralement en réponse aux demandes de l’application conteneur. Ces fonctions membres permettent à l’application conteneur de manipuler l’élément indirectement de différentes façons, par exemple en l’affichant, en exécutant ses verbes ou en extrayant ses données dans différents formats.

Pour utiliser `COleServerItem` , dérivez une classe de celle-ci et implémentez les fonctions membres [OnDraw](#ondraw) et [Serialize](../../mfc/reference/cobject-class.md#serialize) . La `OnDraw` fonction fournit la représentation de métafichier d’un élément, ce qui permet de l’afficher lorsqu’une application de conteneur ouvre un document composé. La `Serialize` fonction de `CObject` fournit la représentation native d’un élément, ce qui permet de transférer un élément incorporé entre les applications serveur et conteneur. [OnGetExtent](#ongetextent) fournit la taille naturelle de l’élément au conteneur, ce qui permet au conteneur de dimensionner l’élément.

Pour plus d’informations sur les serveurs et les rubriques connexes, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md) et « création d’une application conteneur/serveur » dans l’article [conteneurs : fonctionnalités avancées](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a> COleServerItem :: AddOtherClipboardData

Appelez cette fonction pour placer les formats de présentation et de conversion de l’élément OLE dans l' `COleDataSource` objet spécifié.

```cpp
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Paramètres

*pDataSource*<br/>
Pointeur vers l' `COleDataSource` objet dans lequel les données doivent être placées.

### <a name="remarks"></a>Notes

Vous devez avoir implémenté la fonction membre [OnDraw](#ondraw) pour fournir le format de présentation (une image de métafichier) pour l’élément. Pour prendre en charge d’autres formats de conversion, inscrivez-les à l’aide de l’objet [COleDataSource](../../mfc/reference/coledatasource-class.md) renvoyé par [GetDataSource](#getdatasource) et remplacez la fonction membre [OnRenderData](#onrenderdata) pour fournir des données dans les formats que vous souhaitez prendre en charge.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a> COleServerItem :: COleServerItem

Construit un `COleServerItem` objet et l’ajoute à la collection d’éléments de document du document serveur.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*pServerDoc*<br/>
Pointeur vers le document qui contiendra le nouvel élément.

*bAutoDelete*<br/>
Indicateur qui spécifie si l’objet peut être supprimé lorsqu’un lien vers celui-ci est libéré. Affectez la valeur FALSe si l' `COleServerItem` objet fait partie intégrante des données de votre document que vous devez supprimer. Affectez la valeur TRUE si l’objet est une structure secondaire utilisée pour identifier une plage dans les données de votre document qui peut être supprimée par l’infrastructure.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a> COleServerItem :: CopyToClipboard

Appelez cette fonction pour copier l’élément OLE dans le presse-papiers.

```cpp
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Paramètres

*bIncludeLink*<br/>
Affectez la valeur TRUE si les données de liaison doivent être copiées dans le presse-papiers. Affectez la valeur FALSe si votre application serveur ne prend pas en charge les liens.

### <a name="remarks"></a>Notes

La fonction utilise la fonction membre [OnGetClipboardData](#ongetclipboarddata) pour créer un objet [COleDataSource](../../mfc/reference/coledatasource-class.md) contenant les données de l’élément OLE dans les formats pris en charge. La fonction place ensuite l' `COleDataSource` objet dans le presse-papiers à l’aide de la fonction [COleDataSource :: SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) . L' `COleDataSource` objet comprend les données natives de l’élément et sa représentation au format CF_METAFILEPICT, ainsi que les données dans tous les formats de conversion que vous choisissez de prendre en charge. Vous devez avoir implémenté [Serialize](../../mfc/reference/cobject-class.md#serialize) et [OnDraw](#ondraw) pour que cette fonction membre fonctionne.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a> COleServerItem ::D oDragDrop

Appelez la `DoDragDrop` fonction membre pour effectuer une opération de glisser-déplacer.

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
Rectangle de l’élément sur l’écran, en pixels, par rapport à la zone cliente.

*ptOffset*<br/>
Décalage à partir de *lpItemRect* où la position de la souris était au moment de l’opération glisser.

*bIncludeLink*<br/>
Affectez la valeur TRUE si les données de liaison doivent être copiées dans le presse-papiers. Affectez-lui la valeur FALSe si votre application ne prend pas en charge les liens.

*dwEffects*<br/>
Détermine les effets que la source de glissement autorisera dans l’opération glisser (combinaison de copie, déplacement et lien).

*lpRectStartDrag*<br/>
Pointeur vers le rectangle qui définit où le glissement commence réellement. Pour plus d'informations, consultez la section Notes qui suit.

### <a name="return-value"></a>Valeur renvoyée

Valeur de l’énumération DROPEFFECT. S’il est DROPEFFECT_MOVE, les données d’origine doivent être supprimées.

### <a name="remarks"></a>Notes

L’opération de glisser-déplacer ne démarre pas immédiatement. Elle attend que le curseur de la souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu’à ce qu’un nombre spécifié de millisecondes soit écoulé. Si *lpRectStartDrag* a la valeur null, un rectangle par défaut est utilisé afin que l’opération de glisser commence lorsque le curseur de la souris se déplace d’un pixel.

Le délai est spécifié par un paramètre de clé de registre. Vous pouvez modifier le délai en appelant [CWinApp :: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp :: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas de délai, une valeur par défaut de 200 millisecondes est utilisée. Le délai de glissement est stocké comme suit :

- Le délai de glissement de Windows NT est stocké dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini \Windows\DragDelay.

- Le délai de glissement de Windows 3. x est stocké dans le fichier WIN.INI, sous la section [Windows}.

- Le délai de glissement de Windows 95/98 est stocké dans une version mise en cache de WIN.INI.

Pour plus d’informations sur la façon dont les informations sur les retards de glissement sont stockées dans le registre ou le. INI, consultez [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) dans le SDK Windows.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a> COleServerItem :: GetClipboardData

Appelez cette fonction pour remplir l’objet [COleDataSource](../../mfc/reference/coledatasource-class.md) spécifié avec toutes les données qui seraient copiées dans le presse-papiers si vous avez appelé [copytoclipboard](#copytoclipboard) (les mêmes données seraient également transférées si vous avez appelé [DoDragDrop](#dodragdrop)).

```cpp
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Paramètres

*pDataSource*<br/>
Pointeur vers l' `COleDataSource` objet qui recevra les données de l’élément OLE dans tous les formats pris en charge.

*bIncludeLink*<br/>
TRUE si les données de liaison doivent être copiées dans le presse-papiers. FALSe si votre application serveur ne prend pas en charge les liens.

*lpOffset*<br/>
Décalage, en pixels, du curseur de la souris par rapport à l’origine de l’objet.

*lpSize*<br/>
Taille de l’objet en pixels.

### <a name="remarks"></a>Notes

Cette fonction appelle la fonction membre [GetEmbedSourceData](#getembedsourcedata) pour obtenir les données natives de l’élément OLE et appelle la fonction membre [AddOtherClipboardData](#addotherclipboarddata) pour obtenir le format de présentation et tous les formats de conversion pris en charge. Si *bIncludeLink* a la valeur true, la fonction appelle également [GetLinkSourceData](#getlinksourcedata) pour obtenir les données de lien de l’élément.

Substituez cette fonction si vous souhaitez placer les formats dans un `COleDataSource` objet avant ou après les formats fournis par `CopyToClipboard` .

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a> COleServerItem :: GetDataSource

Appelez cette fonction pour récupérer l’objet [COleDataSource](../../mfc/reference/coledatasource-class.md) utilisé pour stocker les formats de conversion pris en charge par l’application serveur.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `COleDataSource` objet utilisé pour stocker les formats de conversion.

### <a name="remarks"></a>Notes

Si vous souhaitez que votre application serveur offre des données dans divers formats au cours des opérations de transfert de données, Inscrivez ces formats avec l' `COleDataSource` objet retourné par cette fonction. Par exemple, si vous souhaitez fournir une représentation CF_TEXT de l’élément OLE pour les opérations du presse-papiers ou du glisser-déplacer, vous devez enregistrer le format avec l' `COleDataSource` objet retourné par cette fonction, puis substituer la `OnRenderXxxData` fonction membre pour fournir les données.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a> COleServerItem :: GetDocument

Appelez cette fonction pour obtenir un pointeur vers le document qui contient l’élément.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le document qui contient l’élément ; NULL si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cela permet d’accéder au document de serveur que vous avez passé comme argument au `COleServerItem` constructeur.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a> COleServerItem :: GetEmbedSourceData

Appelez cette fonction pour obtenir les données de CF_EMBEDSOURCE pour un élément OLE.

```cpp
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) qui recevra les données CF_EMBEDSOURCE pour l’élément OLE.

### <a name="remarks"></a>Notes

Ce format comprend les données natives de l’élément. Vous devez avoir implémenté la `Serialize` fonction membre pour que cette fonction fonctionne correctement.

Le résultat peut ensuite être ajouté à une source de données à l’aide de [COleDataSource :: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [COleServerItem :: OnGetClipboardData](#ongetclipboarddata).

Pour plus d’informations, consultez [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) dans le SDK Windows.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a> COleServerItem :: GetItemName

Appelez cette fonction pour récupérer le nom de l’élément.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom de l'élément.

### <a name="remarks"></a>Notes

En général, vous appelez cette fonction uniquement pour les éléments liés.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a> COleServerItem :: GetLinkSourceData

Appelez cette fonction pour obtenir les données de CF_LINKSOURCE pour un élément OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) qui recevra les données CF_LINKSOURCE pour l’élément OLE.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Ce format comprend le CLSID décrivant le type de l’élément OLE et les informations nécessaires pour localiser le document contenant l’élément OLE.

Le résultat peut ensuite être ajouté à une source de données avec [COleDataSource :: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [OnGetClipboardData](#ongetclipboarddata).

Pour plus d’informations, consultez [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) dans le SDK Windows.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a> COleServerItem :: GetObjectDescriptorData

Appelez cette fonction pour obtenir les données de CF_OBJECTDESCRIPTOR pour un élément OLE.

```cpp
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpOffset*<br/>
Décalage du clic de la souris dans l’angle supérieur gauche de l’élément OLE. Sa valeur peut être NULL.

*lpSize*<br/>
Taille de l’élément OLE. Sa valeur peut être NULL.

*lpStgMedium*<br/>
Pointeur vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) qui recevra les données CF_OBJECTDESCRIPTOR pour l’élément OLE.

### <a name="remarks"></a>Notes

Les informations sont copiées dans la `STGMEDIUM` structure vers laquelle pointe *lpStgMedium*. Ce format comprend les informations nécessaires à la boîte de dialogue Collage spécial.

Pour plus d’informations, consultez [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) dans le SDK Windows.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a> COleServerItem :: IsConnected

Appelez cette fonction pour voir si l’élément OLE est connecté.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément est connecté ; Sinon, 0.

### <a name="remarks"></a>Notes

Un élément OLE est considéré comme connecté si un ou plusieurs conteneurs ont des références à l’élément. Un élément est connecté si son décompte de références est supérieur à 0 ou s’il s’agit d’un élément incorporé.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a> COleServerItem :: IsLinkedItem

Appelez cette fonction pour voir si l’élément OLE est un élément lié.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément est un élément lié ; Sinon, 0.

### <a name="remarks"></a>Notes

Un élément est lié si l’élément est valide et n’est pas retourné dans la liste des éléments incorporés du document. Un élément lié peut être ou non connecté à un conteneur.

Il est courant d’utiliser la même classe pour les éléments liés et incorporés. `IsLinkedItem` vous permet de faire en sorte que les éléments liés se comportent différemment des éléments incorporés, bien que la plupart du temps le code soit courant.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a> COleServerItem :: m_sizeExtent

Ce membre indique au serveur la quantité de l’objet visible dans le document conteneur.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Notes

L’implémentation par défaut de [OnSetExtent](#onsetextent) définit ce membre.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a> COleServerItem :: NotifyChanged

Appelez cette fonction une fois que l’élément lié a été modifié.

```cpp
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect*<br/>
Valeur de l’énumération DVASPECT qui indique l’aspect de l’élément OLE modifié. Ce paramètre peut prendre l’une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

### <a name="remarks"></a>Notes

Si un élément de conteneur est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications conteneur écrites à l’aide de l’bibliothèque MFC (Microsoft Foundation Class), [COleClientItem :: OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelé en réponse.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a> COleServerItem :: OnDoVerb

Appelé par le Framework pour exécuter le verbe spécifié.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Spécifie le verbe à exécuter. Il peut s’agir de l’un des éléments suivants :

|Valeur|Signification|Symbole|
|-----------|-------------|------------|
|0|Primary (verbe)|OLEIVERB_PRIMARY|
|1|Verbe secondaire|(aucune)|
|- 1|Élément d’affichage pour modification|OLEIVERB_SHOW|
|-2|Modifier l’élément dans une fenêtre distincte|OLEIVERB_OPEN|
|-3|Masquer l’élément|OLEIVERB_HIDE|

La valeur-1 est généralement un alias pour un autre verbe. Si la modification ouverte n’est pas prise en charge,-2 a le même effet que-1. Pour obtenir des valeurs supplémentaires, consultez [IOleObject ::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si l’application conteneur a été écrite avec le bibliothèque MFC (Microsoft Foundation Class), cette fonction est appelée lorsque la fonction membre [COleClientItem :: Activate](../../mfc/reference/coleclientitem-class.md#activate) de l' `COleClientItem` objet correspondant est appelée. L’implémentation par défaut appelle la fonction membre [onshow](#onshow) si le verbe principal ou le OLEIVERB_SHOW est spécifié, [OnOpen](#onopen) si le verbe ou le OLEIVERB_OPEN secondaire est spécifié, et [OnHide](#onhide) si OLEIVERB_HIDE est spécifié. L’implémentation par défaut appelle `OnShow` si *iVerb* ne fait pas partie des verbes listés ci-dessus.

Remplacez cette fonction si votre verbe principal n’affiche pas l’élément. Par exemple, si l’élément est un enregistrement audio et que son verbe principal est Play, il n’est pas nécessaire d’afficher l’application serveur pour lire l’élément.

Pour plus d’informations, consultez [IOleObject ::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a> COleServerItem :: OnDraw

Appelé par l’infrastructure pour restituer l’élément OLE dans un métafichier.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers l’objet [CDC](../../mfc/reference/cdc-class.md) sur lequel dessiner l’élément. Le contexte d’affichage est automatiquement connecté au contexte d’affichage des attributs afin que vous puissiez appeler des fonctions d’attribut, même si cela rend le métafichier spécifique à l’appareil.

*rSize*<br/>
Taille, en unités HIMETRIC, dans laquelle dessiner le métafichier.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément a été correctement dessiné ; Sinon, 0.

### <a name="remarks"></a>Notes

La représentation du métafichier de l’élément OLE est utilisée pour afficher l’élément dans l’application conteneur. Si l’application conteneur a été écrite avec le bibliothèque MFC (Microsoft Foundation Class), le métafichier est utilisé par la fonction membre [Draw](../../mfc/reference/coleclientitem-class.md#draw) de l’objet [COleClientItem](../../mfc/reference/coleclientitem-class.md) correspondant. Il n'y a pas d'implémentation par défaut. Vous devez substituer cette fonction pour dessiner l’élément dans le contexte de périphérique spécifié.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a> COleServerItem :: OnDrawEx

Appelé par l’infrastructure pour tout le dessin.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers l’objet [CDC](../../mfc/reference/cdc-class.md) sur lequel dessiner l’élément. Le contrôleur de périphérique est automatiquement connecté au contrôleur de l’attribut, ce qui vous permet d’appeler des fonctions d’attribut, même si cela rend le métafichier spécifique à l’appareil.

*nDrawAspect*<br/>
Valeur de l’énumération DVASPECT. Ce paramètre peut prendre l’une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

*rSize*<br/>
Taille de l’élément en unités HIMETRIC.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément a été correctement dessiné ; Sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle `OnDraw` quand DVASPECT est égal à DVASPECT_CONTENT ; sinon, elle échoue.

Substituez cette fonction pour fournir des données de présentation pour des aspects autres que DVASPECT_CONTENT, tels que DVASPECT_ICON ou DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a> COleServerItem :: OnGetClipboardData

Appelée par l’infrastructure pour obtenir un `COleDataSource` objet contenant toutes les données qui seraient placées dans le presse-papiers par un appel à la fonction membre [copytoclipboard](#copytoclipboard) .

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Paramètres

*bIncludeLink*<br/>
Affectez la valeur TRUE si les données de liaison doivent être copiées dans le presse-papiers. Affectez la valeur FALSe si votre application serveur ne prend pas en charge les liens.

*lpOffset*<br/>
Décalage du curseur de la souris par rapport à l’origine de l’objet, en pixels.

*lpSize*<br/>
Taille de l’objet en pixels.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [COleDataSource](../../mfc/reference/coledatasource-class.md) contenant les données du presse-papiers.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle [GetClipboardData](#getclipboarddata).

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a> COleServerItem :: OnGetExtent

Appelée par l’infrastructure pour récupérer la taille, en unités HIMETRIC, de l’élément OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect*<br/>
Spécifie l’aspect de l’élément OLE dont les limites doivent être récupérées. Ce paramètre peut prendre l’une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

*rSize*<br/>
Référence à un `CSize` objet qui recevra la taille de l’élément OLE.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application conteneur a été écrite avec le bibliothèque MFC (Microsoft Foundation Class), cette fonction est appelée lorsque la fonction membre [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) de l' `COleClientItem` objet correspondant est appelée. L'implémentation par défaut n'exécute aucune opération. Vous devez l’implémenter vous-même. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors du traitement d’une demande pour la taille de l’élément OLE.

## <a name="coleserveritemonhide"></a><a name="onhide"></a> COleServerItem :: OnHide

Appelé par l’infrastructure pour masquer l’élément OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Notes

Les appels par défaut `COleServerDoc::OnShowDocument( FALSE )` . La fonction informe également le conteneur que l’élément OLE a été masqué. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors du masquage d’un élément OLE.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a> COleServerItem :: OnInitFromData

Appelé par l’infrastructure pour initialiser un élément OLE à l’aide du contenu de *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Pointeur vers un objet de données OLE qui contient des données dans différents formats pour l’initialisation de l’élément OLE.

*bCreation*<br/>
TRUE si la fonction est appelée pour initialiser un élément OLE qui vient d’être créé par une application de conteneur. FALSe si la fonction est appelée pour remplacer le contenu d’un élément OLE déjà existant.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si *bCreation* a la valeur true, cette fonction est appelée si un conteneur implémente l’insertion d’un nouvel objet basé sur la sélection actuelle. Les données sélectionnées sont utilisées lors de la création du nouvel élément OLE. Par exemple, lors de la sélection d’une plage de cellules dans un programme de feuille de calcul, puis de l’utilisation de l’option Insérer un nouvel objet pour créer un graphique basé sur les valeurs de la plage sélectionnée. L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour choisir un format acceptable parmi ceux proposés par *pDataObject* et initialiser l’élément OLE en fonction des données fournies. Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez [IOleObject :: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) dans le SDK Windows.

## <a name="coleserveritemonopen"></a><a name="onopen"></a> COleServerItem :: OnOpen

Appelée par l’infrastructure pour afficher l’élément OLE dans une instance distincte de l’application serveur, plutôt que sur place.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut active la première fenêtre frame qui affiche le document qui contient l’élément OLE ; Si l’application est un mini-serveur, l’implémentation par défaut affiche la fenêtre principale. La fonction informe également le conteneur que l’élément OLE a été ouvert.

Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de l’ouverture d’un élément OLE. Cela est particulièrement courant avec les éléments liés dans lesquels vous souhaitez définir la sélection sur le lien lorsqu’il est ouvert.

Pour plus d’informations, consultez [IOleClientSite :: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) dans la SDK Windows.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a> COleServerItem :: OnQueryUpdateItems

Appelé par l’infrastructure pour déterminer si des éléments liés dans le document serveur actuel sont obsolètes.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le document contient des éléments nécessitant des mises à jour ; 0 si tous les éléments sont à jour.

### <a name="remarks"></a>Notes

Un élément est obsolète si son document source a été modifié mais que l’élément lié n’a pas été mis à jour pour refléter les modifications apportées au document.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a> COleServerItem :: OnRenderData

Appelé par le Framework pour récupérer des données dans le format spécifié.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en spécifiant le format dans lequel les informations sont demandées.

*lpStgMedium*<br/>
Pointe vers une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) dans laquelle les données doivent être retournées.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) ou [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) pour un rendu retardé. L’implémentation par défaut de cette fonction appelle [OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata), respectivement, si le support de stockage fourni est un fichier ou une mémoire. Si aucun de ces formats n’est fourni, l’implémentation par défaut retourne 0 et ne fait rien.

Si *lpStgMedium* ->  *TYMED* est TYMED_NULL, STGMEDIUM doit être alloué et rempli comme spécifié par *lpFormatEtc->TYMED*. Si ce n’est pas TYMED_NULL, STGMEDIUM doit être renseigné avec les données.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vos données sont de taille petite et fixe, remplacez `OnRenderGlobalData` . Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez `OnRenderFileData` .

Pour plus d’informations, consultez [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)et [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) dans le SDK Windows.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a> COleServerItem :: OnRenderFileData

Appelé par le Framework pour récupérer des données dans le format spécifié lorsque le support de stockage est un fichier.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en spécifiant le format dans lequel les informations sont demandées.

*pFile*<br/>
Pointe vers un `CFile` objet dans lequel les données doivent être restituées.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pour un rendu retardé. L’implémentation par défaut de cette fonction retourne simplement FALSe.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata).

Pour plus d’informations, consultez [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a> COleServerItem :: OnRenderGlobalData

Appelé par le Framework pour récupérer des données dans le format spécifié lorsque le support de stockage spécifié est une mémoire globale.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en spécifiant le format dans lequel les informations sont demandées.

*phGlobal*<br/>
Pointe vers un handle vers la mémoire globale dans laquelle les données doivent être retournées. Si aucune mémoire n’a été allouée, ce paramètre peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) pour un rendu retardé. L’implémentation par défaut de cette fonction retourne simplement FALSe.

Si *phGlobal* a la valeur null, un nouveau HGLOBAL doit être alloué et retourné dans *phGlobal*. Dans le cas contraire, le HGLOBAL spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le HGLOBAL ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réalloué à une plus grande taille.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata).

Pour plus d’informations, consultez [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a> COleServerItem :: OnSetColorScheme

Appelé par l’infrastructure pour spécifier une palette de couleurs à utiliser lors de la modification de l’élément OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Paramètres

*lpLogPalette*<br/>
Pointeur vers une structure Windows [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) .

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la palette de couleurs est utilisée ; Sinon, 0.

### <a name="remarks"></a>Notes

Si l’application conteneur a été écrite à l’aide de la bibliothèque MFC (Microsoft Foundation Class), cette fonction est appelée lorsque la fonction [IOleObject :: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) de l' `COleClientItem` objet correspondant est appelée. L’implémentation par défaut retourne FALSe. Remplacez cette fonction si vous souhaitez utiliser la palette recommandée. L’application serveur n’est pas obligée d’utiliser la palette suggérée.

Pour plus d’informations, consultez [IOleObject :: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) dans le SDK Windows.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a> COleServerItem :: OnSetData

Appelé par l’infrastructure pour remplacer les données de l’élément OLE par les données spécifiées.

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
Pointeur vers une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) dans laquelle les données résident.

*bRelease*<br/>
Indique qui a la propriété du support de stockage après avoir effectué l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées pour le compte du support de stockage. Pour ce faire, l’appelant définit *bRelease*. Si *bRelease* est différent de zéro, l’élément de serveur prend la propriété, en libérant le support une fois qu’il a fini de l’utiliser. Quand *bRelease* a la valeur 0, l’appelant conserve la propriété et l’élément de serveur peut utiliser le support de stockage uniquement pendant la durée de l’appel.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’élément de serveur ne prend pas possession des données tant qu’il n’a pas été obtenu. Autrement dit, il ne prend pas la propriété s’il retourne 0. Si la source de données prend possession, elle libère le support de stockage en appelant la fonction [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

L'implémentation par défaut n'exécute aucune opération. Substituez cette fonction pour remplacer les données de l’élément OLE par les données spécifiées. Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)et [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) dans le SDK Windows.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a> COleServerItem :: OnSetExtent

Appelée par l’infrastructure pour indiquer à l’élément OLE la quantité d’espace disponible dans le document conteneur.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Paramètres

*nDrawAspect*<br/>
Spécifie l’aspect de l’élément OLE dont les limites sont spécifiées. Ce paramètre peut prendre l’une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

*size*<br/>
Une structure [CSize](../../atl-mfc-shared/reference/csize-class.md) spécifiant la nouvelle taille de l’élément OLE.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application de conteneur a été écrite avec le bibliothèque MFC (Microsoft Foundation Class), cette fonction est appelée lorsque la [fonction membre de la](../../mfc/reference/coleclientitem-class.md#setextent) méthode de création de l' `COleClientItem` objet correspondant est appelée. L’implémentation par défaut définit le membre [m_sizeExtent](#m_sizeextent) à la taille spécifiée si *nDrawAspect* est DVASPECT_CONTENT ; Sinon, elle retourne 0. Substituez cette fonction pour effectuer un traitement spécial lorsque vous modifiez la taille de l’élément.

## <a name="coleserveritemonshow"></a><a name="onshow"></a> COleServerItem :: OnShow

Appelé par l’infrastructure pour indiquer à l’application serveur d’afficher l’élément OLE sur place.

```
virtual void OnShow();
```

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée lorsque l’utilisateur de l’application conteneur crée un élément ou exécute un verbe, tel que Edit, qui requiert l’affichage de l’élément. L’implémentation par défaut tente l’activation sur place. En cas d’échec, la fonction appelle la `OnOpen` fonction membre pour afficher l’élément OLE dans une fenêtre distincte.

Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’un élément OLE est affiché.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a> COleServerItem :: OnUpdate

Appelé par le Framework lorsqu’un élément a été modifié.

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

*lHint*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Pointeur vers un objet qui stocke des informations sur la modification.

*nDrawAspect*<br/>
Valeur de l’énumération DVASPECT. Ce paramètre peut avoir l’une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle [NotifyChanged](#notifychanged), indépendamment de l’indicateur ou de l’expéditeur.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a> COleServerItem :: OnUpdateItems

Appelé par l’infrastructure pour mettre à jour tous les éléments du document serveur.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pour tous les `COleClientItem` objets dans le document.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a> COleServerItem :: SetItemName

Appelez cette fonction lorsque vous créez un élément lié pour définir son nom.

```cpp
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
Pointeur vers le nouveau nom de l’élément.

### <a name="remarks"></a>Notes

Le nom doit être unique dans le document. Quand une application serveur est appelée pour modifier un élément lié, l’application utilise ce nom pour Rechercher l’élément. Vous n’avez pas besoin d’appeler cette fonction pour les éléments incorporés.

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem, classe](../../mfc/reference/cdocitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
