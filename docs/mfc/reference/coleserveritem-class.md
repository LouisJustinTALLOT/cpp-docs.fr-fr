---
title: Classe COleServerItem | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a05553843c4478109c0fe63dd79f08b2116f58c7
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039243"
---
# <a name="coleserveritem-class"></a>Classe COleServerItem
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
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Place des formats de présentation et de conversion dans un `COleDataSource` objet.|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copie l’élément dans le Presse-papiers.|  
|[COleServerItem::DoDragDrop](#dodragdrop)|Effectue une opération de glisser-déplacer.|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtient la source de données pour une utilisation dans le transfert de données (glisser-déplacer ou le Presse-papiers).|  
|[COleServerItem::GetDocument](#getdocument)|Retourne le document serveur qui contient l’élément.|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtient le **CF_EMBEDSOURCE** les données pour un élément OLE.|  
|[COleServerItem::GetItemName](#getitemname)|Retourne le nom de l’élément. Utilisé pour les éléments liés.|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtient le **CF_LINKSOURCE** les données pour un élément OLE.|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtient le **CF_OBJECTDESCRIPTOR** les données pour un élément OLE.|  
|[COleServerItem::IsConnected](#isconnected)|Indique si l’élément est actuellement attaché à un conteneur actif.|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indique si l’élément représente un élément OLE lié.|  
|[COleServerItem::NotifyChanged](#notifychanged)|Met à jour tous les conteneurs avec mise à jour automatique des liens.|  
|[COleServerItem::OnDoVerb](#ondoverb)|Appelé pour exécuter un verbe.|  
|[COleServerItem::OnDraw](#ondraw)|Appelé lorsque le conteneur demande pour dessiner l’élément ; implémentation requise.|  
|[COleServerItem::OnDrawEx](#ondrawex)|Appelé pour le dessin de l’élément spécialisé.|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Appelé par l’infrastructure pour obtenir les données qui doivent être copiées dans le Presse-papiers.|  
|[COleServerItem::OnGetExtent](#ongetextent)|Appelé par l’infrastructure pour récupérer la taille de l’élément OLE.|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|Appelé par l’infrastructure pour initialiser un élément OLE en utilisant le contenu de l’objet de transfert de données spécifié.|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Appelé pour déterminer si des éléments liés nécessitent une mise à jour.|  
|[COleServerItem::OnRenderData](#onrenderdata)|Récupère les données dans le cadre de rendu retardé.|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Récupère des données dans un `CFile` objet en tant que partie du rendu retardé.|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Récupère des données dans un `HGLOBAL` dans le cadre de rendu retardé.|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Appelé pour définir le jeu de couleurs de l’élément.|  
|[COleServerItem::OnSetData](#onsetdata)|Appelé pour définir les données de l’article.|  
|[COleServerItem::OnSetExtent](#onsetextent)|Appelé par l’infrastructure pour définir la taille de l’élément OLE.|  
|[COleServerItem::OnUpdate](#onupdate)|Appelé lorsqu’une partie du document, l’élément appartienne dans est modifié.|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|Appelé pour mettre à jour le cache de présentation de tous les éléments dans le document serveur.|  
|[COleServerItem::SetItemName](#setitemname)|Définit le nom de l’élément. Utilisé pour les éléments liés.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|Obtient l’objet utilisé pour stocker les formats de conversion.|  
|[COleServerItem::OnHide](#onhide)|Appelé par l’infrastructure pour masquer l’élément OLE.|  
|[COleServerItem::OnOpen](#onopen)|Appelé par l’infrastructure pour afficher l’élément OLE dans sa propre fenêtre de niveau supérieur.|  
|[COleServerItem::OnShow](#onshow)|Appelé lorsque le conteneur demande pour l’afficher.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informe le serveur sur la quantité de l’élément OLE est visible.|  
  
## <a name="remarks"></a>Notes  
 Un élément lié peut représenter tout ou partie d’un document serveur. Un élément incorporé représente toujours un document serveur tout entier.  
  
 La `COleServerItem` classe définit plusieurs fonctions membres substituables appelées par les bibliothèques de liens dynamiques du système OLE (DLL), généralement en réponse aux demandes à partir de l’application conteneur. Ces fonctions membres autorisent l’application de conteneur manipuler l’élément indirectement de différentes manières, telles que par son affichage, l’exécution de ses verbes ou récupère ses données dans divers formats.  
  
 Pour utiliser `COleServerItem`, dériver une classe et implémenter la [OnDraw](#ondraw) et [Serialize](../../mfc/reference/cobject-class.md#serialize) fonctions membres. Le `OnDraw` fonction fournit la représentation du métafichier d’un élément, ce qui permet à afficher lorsqu’une application conteneur ouvre un document composé. Le `Serialize` fonction de `CObject` fournit la représentation native d’un élément, ce qui permet un élément incorporé à transférer entre les applications serveur et le conteneur. [OnGetExtent](#ongetextent) fournit la taille physique de l’élément dans le conteneur, l’activation du conteneur à la taille de l’élément.  
  
 Pour plus d’informations sur les serveurs et les rubriques connexes, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md) et « Création d’une Application conteneur/serveur » dans l’article [conteneurs : fonctionnalités avancées](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData  
 Appelez cette fonction pour placer les formats de présentation et de conversion pour l’élément OLE spécifié `COleDataSource` objet.  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataSource*  
 Pointeur vers le `COleDataSource` de l’objet dans lequel les données doivent être placées.  
  
### <a name="remarks"></a>Notes  
 Vous devez avoir implémenté le [OnDraw](#ondraw) fonction membre pour fournir le format de présentation (une image de métafichier) pour l’élément. Pour prendre en charge d’autres formats de conversion, les enregistrer à l’aide de la [COleDataSource](../../mfc/reference/coledatasource-class.md) objet retourné par [GetDataSource](#getdatasource) et remplacez le [se](#onrenderdata) fonction membre fournir des données dans les formats que vous souhaitez prendre en charge.  
  
##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem  
 Construit un `COleServerItem` de l’objet et l’ajoute à la collection du document serveur des éléments de document.  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Paramètres  
 *pServerDoc*  
 Pointeur vers le document qui contiendra le nouvel élément.  
  
 *bAutoDelete*  
 Indicateur précisant si l’objet peut être supprimé lors de la libération d’un lien vers celui-ci. Affectez la valeur **FALSE** si le `COleServerItem` objet fait partie intégrante des données de votre document que vous devez le supprimer. Affectez la valeur **TRUE** si l’objet est une structure secondaire utilisée pour identifier une plage de données de votre document qui peuvent être supprimées par l’infrastructure.  
  
##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard  
 Appelez cette fonction pour copier l’élément OLE dans le Presse-papiers.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bIncludeLink*  
 Affectez la valeur **TRUE** si la liaison de données doit être copié dans le Presse-papiers. Affectez la valeur **FALSE** si votre application serveur ne prend pas en charge les liens.  
  
### <a name="remarks"></a>Notes  
 La fonction utilise le [OnGetClipboardData](#ongetclipboarddata) fonction membre pour créer un [COleDataSource](../../mfc/reference/coledatasource-class.md) objet contenant les données de l’élément OLE dans les formats pris en charge. La fonction place ensuite la `COleDataSource` objet dans le Presse-papiers à l’aide de la [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) (fonction). Le `COleDataSource` objet inclut des données natives de l’élément et sa représentation sous forme de `CF_METAFILEPICT` format, ainsi que les données dans les formats de conversion que vous choisissez pour prendre en charge. Vous devez avoir implémenté [Serialize](../../mfc/reference/cobject-class.md#serialize) et [OnDraw](#ondraw) pour cette fonction membre à utiliser.  
  
##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop  
 Appelez le `DoDragDrop` fonction membre pour effectuer une opération de glisser-déplacer.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpRectItem*  
 Rectangle de l’élément à l’écran, en pixels, par rapport à la zone cliente.  
  
 *ptOffset*  
 Le décalage à partir de *lpItemRect* où la position de la souris était au moment de l’opération glisser.  
  
 *bIncludeLink*  
 Affectez la valeur **TRUE** si la liaison de données doit être copié dans le Presse-papiers. Affectez-lui la valeur **FALSE** si votre application ne prend pas en charge les liens.  
  
 *dwEffects*  
 Détermine les effets de la source de glissement autorisera dans l’opération de glissement (il s’agit d’une combinaison de copier, déplacer et lien).  
  
 *lpRectStartDrag*  
 Pointeur vers le rectangle qui définit où commence l’opération glisser. Pour plus d'informations, consultez la section Notes qui suit.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de l'énumération `DROPEFFECT`. S’il est `DROPEFFECT_MOVE`, les données d’origine doivent être supprimées.  
  
### <a name="remarks"></a>Notes  
 L’opération de glisser-déposer ne commence pas immédiatement. Il attend jusqu'à ce que le curseur de la souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu'à ce qu’un nombre spécifié de millisecondes écoulées. Si *lpRectStartDrag* est **NULL**, un rectangle par défaut est utilisé afin que l’opération glisser commence lorsque le curseur de souris déplace d’un pixel.  
  
 Délai d’attente est spécifié par un paramètre de clé de Registre. Vous pouvez modifier le délai d’attente en appelant [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas de délai d’attente, 200 millisecondes comme valeur par défaut est utilisée. Faites glisser retarder l’heure est stockée comme suit :  
  
-   Retarder l’heure de glissement de Windows NT est stocké dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Retarder l’heure de Windows 3.x glisser est stocké dans le fichier WIN. Fichier INI, la section [Windows}.  
  
-   Retarder l’heure de Windows 95/98 glisser est stocké dans une version mise en cache de Windows. INI.  
  
 Pour plus d’informations sur la façon de faire glisser les informations de délai sont stockées dans le Registre ou le. Fichier INI, consultez [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) dans le Kit de développement logiciel Windows.  
  
##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData  
 Appelez cette fonction pour remplir spécifié [COleDataSource](../../mfc/reference/coledatasource-class.md) objet avec toutes les données qui doivent être copiés dans le Presse-papiers, si vous avez appelé [CopyToClipboard](#copytoclipboard) (les mêmes données seraient également être transférées si vous appelé [DoDragDrop](#dodragdrop)).  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataSource*  
 Pointeur vers le `COleDataSource` objet qui recevra les données de l’élément OLE dans tous les formats pris en charge.  
  
 *bIncludeLink*  
 **TRUE** si la liaison de données doit être copié dans le Presse-papiers. **FALSE** si votre application serveur ne prend pas en charge les liens.  
  
 *lpOffset*  
 Offset, en pixels, de la souris à l’origine de l’objet.  
  
 *lpSize*  
 La taille de l’objet en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette fonction appelle le [GetEmbedSourceData](#getembedsourcedata) fonction membre pour obtenir les données natives pour l’élément OLE et appelle le [AddOtherClipboardData](#addotherclipboarddata) fonction membre pour obtenir le format de présentation et les prise en charge des formats de conversion. Si *bIncludeLink* est **TRUE**, la fonction appelle également [GetLinkSourceData](#getlinksourcedata) pour obtenir les données de lien pour l’élément.  
  
 Remplacez cette fonction si vous souhaitez placer des formats dans un `COleDataSource` objet avant ou après les formats fournis par `CopyToClipboard`.  
  
##  <a name="getdatasource"></a>  COleServerItem::GetDataSource  
 Appelez cette fonction pour obtenir le [COleDataSource](../../mfc/reference/coledatasource-class.md) objet utilisé pour stocker les formats de conversion qui prend en charge de l’application serveur.  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `COleDataSource` objet utilisé pour stocker les formats de conversion.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez que votre application serveur envoient des données dans divers formats lors du transfert de données operations, inscrire ces formats avec la `COleDataSource` objet retourné par cette fonction. Par exemple, si vous souhaitez fournir un **CF_TEXT** représentation de l’élément OLE pour les opérations du Presse-papiers ou glisser-déplacer, vous pouvez enregistrer le format avec le `COleDataSource` objet cette fonction retourne et que vous remplacez ensuite le  **OnRenderXxxData** fonction membre pour fournir les données.  
  
##  <a name="getdocument"></a>  COleServerItem::GetDocument  
 Appelez cette fonction pour obtenir un pointeur vers le document qui contient l’élément.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le document qui contient l’élément ; **NULL** si l’élément n’est pas partie d’un document.  
  
### <a name="remarks"></a>Notes  
 Cela permet d’accéder au document serveur que vous avez transmise en tant qu’argument à la `COleServerItem` constructeur.  
  
##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData  
 Appelez cette fonction pour obtenir le **CF_EMBEDSOURCE** les données pour un élément OLE.  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpStgMedium*  
 Pointeur vers le [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure qui recevra le **CF_EMBEDSOURCE** les données de l’élément OLE.  
  
### <a name="remarks"></a>Notes  
 Ce format comprend des données natives de l’élément. Vous devez avoir implémenté le `Serialize` fonction membre pour cette fonction fonctionne correctement.  
  
 Le résultat peut ensuite être ajouté à une source de données à l’aide de [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [COleServerItem::OnGetClipboardData](#ongetclipboarddata).  
  
 Pour plus d’informations, consultez [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) dans le Kit de développement logiciel Windows.  
  
##  <a name="getitemname"></a>  COleServerItem::GetItemName  
 Appelez cette fonction pour obtenir le nom de l’élément.  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nom de l'élément.  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous appelez cette fonction uniquement pour les éléments liés.  
  
##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData  
 Appelez cette fonction pour obtenir le `CF_LINKSOURCE` les données pour un élément OLE.  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpStgMedium*  
 Pointeur vers le [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure qui recevra le `CF_LINKSOURCE` les données de l’élément OLE.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ce format inclut le CLSID décrivant le type de l’élément OLE et les informations nécessaires pour accéder au document contenant l’élément OLE.  
  
 Le résultat peut ensuite être ajouté à une source de données avec [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Cette fonction est appelée automatiquement par [OnGetClipboardData](#ongetclipboarddata).  
  
 Pour plus d’informations, consultez [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) dans le Kit de développement logiciel Windows.  
  
##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData  
 Appelez cette fonction pour obtenir le **CF_OBJECTDESCRIPTOR** les données pour un élément OLE.  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpOffset*  
 Décalage de la souris, cliquez sur à partir de l’angle supérieur gauche de l’élément OLE. Peut être **NULL**.  
  
 *lpSize*  
 Taille de l’élément OLE. Peut être **NULL**.  
  
 *lpStgMedium*  
 Pointeur vers le [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure qui recevra le **CF_OBJECTDESCRIPTOR** les données de l’élément OLE.  
  
### <a name="remarks"></a>Notes  
 Les informations sont copiées dans le **STGMEDIUM** structure vers laquelle pointe *lpStgMedium*. Ce format inclut les informations requises pour la boîte de dialogue Collage spécial.  
  
 Pour plus d’informations, consultez [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) dans le Kit de développement logiciel Windows.  
  
##  <a name="isconnected"></a>  COleServerItem::IsConnected  
 Appelez cette fonction pour voir si l’élément OLE est connecté.  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément est connecté ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un élément OLE est considéré comme connecté si un ou plusieurs conteneurs ont des références à l’élément. Un élément est connecté si son décompte de références est supérieur à 0 ou s’il s’agit d’un élément incorporé.  
  
##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem  
 Appelez cette fonction pour voir si l’élément OLE est un élément lié.  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément est un élément lié ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un élément est lié si l’élément est valide et qu’il n’est pas retourné dans la liste du document des éléments incorporés. Un élément lié peut ou ne peut pas être connecté à un conteneur.  
  
 Il est courant d’utiliser la même classe pour les éléments liés et incorporés. `IsLinkedItem` permet de rendre des éléments liés se comportent différemment dans les éléments incorporés, bien que le nombre de fois où le code est courant.  
  
##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent  
 Ce membre indique au serveur de la part de l’objet est visible dans le document conteneur.  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de [OnSetExtent](#onsetextent) définit ce membre.  
  
##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged  
 Appelez cette fonction une fois que l’élément lié a été modifié.  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawAspect*  
 Une valeur à partir de la `DVASPECT` énumération qui indique quelle partie de l’élément OLE a été modifié. Ce paramètre peut prendre une des valeurs suivantes :  
  
- `DVASPECT_CONTENT` Élément est représenté de façon à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- `DVASPECT_THUMBNAIL` Élément est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- `DVASPECT_ICON` Élément est représenté par une icône.  
  
- `DVASPECT_DOCPRINT` Élément est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
### <a name="remarks"></a>Notes  
 Si un élément de conteneur est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications conteneur écrites à l’aide de la bibliothèque Microsoft Foundation Class, [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée en réponse.  
  
##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb  
 Appelé par le framework pour exécuter le verbe spécifié.  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>Paramètres  
 *iVerb*  
 Spécifie le verbe à exécuter. Il peut prendre l’une des opérations suivantes :  
  
|Value|Signification|Symbole|  
|-----------|-------------|------------|  
|0|Primary (verbe)|`OLEIVERB_PRIMARY`|  
|1|Verbe secondaire|(Aucun)|  
|- 1|Élément d’affichage pour la modification|`OLEIVERB_SHOW`|  
|- 2|Modifier l’élément dans une fenêtre distincte|`OLEIVERB_OPEN`|  
|- 3|Masquer l’élément|`OLEIVERB_HIDE`|  
  
 La valeur-1 est généralement un alias pour un autre mot. Si la modification ouverte n’est pas prise en charge, -2 a le même effet que -1. Pour les valeurs supplémentaires, consultez [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Si l’application conteneur a été écrit avec la bibliothèque Microsoft Foundation Class, cette fonction est appelée lorsque le [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) fonction membre correspondantes `COleClientItem` objet est appelé. L’implémentation par défaut appelle la [OnShow](#onshow) fonction membre si le verbe principal ou `OLEIVERB_SHOW` est spécifié, [OnOpen](#onopen) si le verbe secondaire ou `OLEIVERB_OPEN` est spécifié et [OnHide](#onhide) si `OLEIVERB_HIDE` est spécifié. L’implémentation par défaut appelle `OnShow` si `iVerb` n’est pas un des verbes répertoriés ci-dessus.  
  
 Remplacez cette fonction si votre primary (verbe) n’affiche pas l’élément. Par exemple, si l’élément est un enregistrement audio et son verbe principal est Play, il serait inutile afficher l’application de serveur pour lire l’élément.  
  
 Pour plus d’informations, consultez [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) dans le Kit de développement logiciel Windows.  
  
##  <a name="ondraw"></a>  COleServerItem::OnDraw  
 Appelé par l’infrastructure pour restituer l’élément OLE dans un métafichier.  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Un pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet sur lequel dessiner l’élément. Le contexte d’affichage est automatiquement connecté au contexte d’affichage de l’attribut, vous pouvez appeler des fonctions de l’attribut, bien que cela donc rendrait le métafichier spécifique au périphérique.  
  
 *rSize*  
 Taille, en **HIMETRIC** unités, dans lequel dessiner le métafichier.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été dessiné avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La représentation du métafichier de l’élément OLE est utilisée pour afficher l’élément dans l’application conteneur. Si l’application conteneur a été écrit avec la bibliothèque Microsoft Foundation Class, le métafichier est utilisé par le [dessiner](../../mfc/reference/coleclientitem-class.md#draw) fonction membre correspondantes [COleClientItem](../../mfc/reference/coleclientitem-class.md) objet. Il n'y a pas d'implémentation par défaut. Vous devez substituer cette fonction pour dessiner l’élément dans le contexte de périphérique spécifié.  
  
##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx  
 Appelé par l’infrastructure pour tout le dessin.  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Un pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet sur lequel dessiner l’élément. Le contrôleur de domaine est automatiquement connecté à l’attribut de contrôleur de domaine, vous pouvez appeler des fonctions de l’attribut, bien que cela donc rendrait le métafichier spécifique au périphérique.  
  
 *nDrawAspect*  
 Valeur de l'énumération `DVASPECT`. Ce paramètre peut prendre une des valeurs suivantes :  
  
- `DVASPECT_CONTENT` Élément est représenté de façon à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- `DVASPECT_THUMBNAIL` Élément est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- `DVASPECT_ICON` Élément est représenté par une icône.  
  
- `DVASPECT_DOCPRINT` Élément est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
 `rSize`  
 Taille de l’élément dans **HIMETRIC** unités.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été dessiné avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut appelle `OnDraw` lorsque `DVASPECT` est égal à `DVASPECT_CONTENT`; sinon, elle échoue.  
  
 Remplacez cette fonction pour fournir des données de présentation pour les aspects autre que `DVASPECT_CONTENT`, tel que `DVASPECT_ICON` ou `DVASPECT_THUMBNAIL`.  
  
##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData  
 Appelé par l’infrastructure pour obtenir un `COleDataSource` objet contenant toutes les données sont placées dans le Presse-papiers par un appel à la [CopyToClipboard](#copytoclipboard) fonction membre.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *bIncludeLink*  
 Affectez la valeur **TRUE** si la liaison de données doit être copié dans le Presse-papiers. Affectez la valeur **FALSE** si votre application serveur ne prend pas en charge les liens.  
  
 *lpOffset*  
 Le décalage de la souris à l’origine de l’objet en pixels.  
  
 *lpSize*  
 La taille de l’objet en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [COleDataSource](../../mfc/reference/coledatasource-class.md) objet contenant les données du Presse-papiers.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction appelle [exception de GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent  
 Appelée par l’infrastructure pour récupérer la taille, dans **HIMETRIC** unités, de l’élément OLE.  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawAspect*  
 Spécifie l’aspect de l’élément OLE dont les limites doivent être récupérés. Ce paramètre peut prendre une des valeurs suivantes :  
  
- `DVASPECT_CONTENT` Élément est représenté de façon à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- `DVASPECT_THUMBNAIL` Élément est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- `DVASPECT_ICON` Élément est représenté par une icône.  
  
- `DVASPECT_DOCPRINT` Élément est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
 *rSize*  
 Référence à un `CSize` objet qui reçoit la taille de l’élément OLE.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’application conteneur a été écrit avec la bibliothèque Microsoft Foundation Class, cette fonction est appelée lorsque le [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) fonction membre correspondantes `COleClientItem` objet est appelé. L'implémentation par défaut n'exécute aucune opération. Vous devez implémenter vous-même. Remplacez cette fonction si vous souhaitez exécuter un traitement spécial lors de la gestion d’une demande pour la taille de l’élément OLE.  
  
##  <a name="onhide"></a>  COleServerItem::OnHide  
 Appelé par l’infrastructure pour masquer l’élément OLE.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Notes  
 Les appels par défaut **COleServerDoc::OnShowDocument (FALSE)**. La fonction signale également le conteneur que l’élément OLE a été masquée. Remplacez cette fonction si vous souhaitez exécuter un traitement spécial lorsque vous masquez un élément OLE.  
  
##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData  
 Appelé par l’infrastructure pour initialiser un élément OLE en utilisant le contenu de *pDataObject*.  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDataObject*  
 Pointeur vers un objet de données OLE contenant des données dans divers formats d’initialisation de l’élément OLE.  
  
 *bCreation*  
 **TRUE** si la fonction est appelée pour initialiser un élément OLE nouvellement créé par une application conteneur. **FALSE** si la fonction est appelée pour remplacer le contenu d’un élément OLE déjà existant.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si *bCreation* est **TRUE**, cette fonction est appelée si un conteneur implémente l’insertion d’un objet en fonction de la sélection actuelle. Les données sélectionnées sont utilisées lors de la création du nouvel élément OLE. Par exemple, lorsque la sélection d’une plage de cellules dans un tableur et ensuite à l’aide de l’insertion d’un objet pour créer un graphique basés sur les valeurs dans la plage sélectionnée. L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour choisir un format acceptable parmi celles proposées par *pDataObject* et initialiser l’élément OLE selon les données fournies. Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) dans le Kit de développement logiciel Windows.  
  
##  <a name="onopen"></a>  COleServerItem::OnOpen  
 Appelé par l’infrastructure pour afficher l’élément OLE dans une instance distincte de l’application serveur, plutôt qu’en place.  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut active la première fenêtre frame affichant le document qui contient l’élément OLE ; Si l’application est un mini-serveur, l’implémentation par défaut montre la fenêtre principale. La fonction signale également le conteneur que l’élément OLE a été ouvert.  
  
 Remplacez cette fonction si vous souhaitez exécuter un traitement spécial lors de l’ouverture d’un élément OLE. Cela est particulièrement courant avec les éléments liés dans lequel vous souhaitez définir la sélection pour le lien lorsqu’il est ouvert.  
  
 Pour plus d’informations, consultez [IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) dans le Kit de développement logiciel Windows.  
  
##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems  
 Appelé par l’infrastructure pour déterminer si des éléments liés dans le document serveur actuel sont obsolètes.  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le document contient des éléments devant être mises à jour ; 0 si tous les éléments sont à jour.  
  
### <a name="remarks"></a>Notes  
 Un élément est obsolète si son document source a été modifié, mais que l’élément lié n’a pas été mis à jour pour refléter les modifications dans le document.  
  
##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData  
 Appelé par l’infrastructure pour récupérer des données dans le format spécifié.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format dans lequel les informations sont demandées.  
  
 *lpStgMedium*  
 Pointe vers un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure dans laquelle les données sont à retourner.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) ou [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction appelle [OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata), respectivement, si le support de stockage fourni est un fichier ou la mémoire. Si aucune de ces formats n’est fourni, l’implémentation par défaut retourne la valeur 0 et n’exécute aucune opération.  
  
 Si *lpStgMedium*-> *tymed* est **TYMED_NULL**, le **STGMEDIUM** doit allouée et remplis comme spécifié par *lpFormatEtc -> tymed*. Si ce n’est pas **TYMED_NULL**, le **STGMEDIUM** devrait normalement être en place avec les données.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez substituer l’une des autres versions de cette fonction à la place. Si vos données soient petite et une taille fixe, substituez `OnRenderGlobalData`. Si vos données sont dans un fichier, ou de taille variable, substituez `OnRenderFileData`.  
  
 Pour plus d’informations, consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), et [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) dans le Kit de développement logiciel Windows.  
  
##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData  
 Appelé par l’infrastructure pour récupérer des données dans le format spécifié lorsque le support de stockage est un fichier.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format dans lequel les informations sont demandées.  
  
 *pFile*  
 Pointe vers un `CFile` objet dans lequel les données doivent être rendus.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction retourne simplement **FALSE**.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [se](#onrenderdata). Si vos données sont dans un fichier, ou de taille variable, substituez [OnRenderFileData](#onrenderfiledata).  
  
 Pour plus d’informations, consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData  
 Appelé par l’infrastructure pour récupérer des données dans le format spécifié lorsque le support de stockage spécifié est la mémoire globale.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format dans lequel les informations sont demandées.  
  
 *phGlobal*  
 Pointe vers un handle de mémoire globale dans laquelle les données sont à retourner. Si aucune mémoire n’a été allouée, ce paramètre peut être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction retourne simplement **FALSE**.  
  
 Si *phGlobal* est **NULL**, puis une nouvelle `HGLOBAL` doit être allouée et retournée dans *phGlobal*. Dans le cas contraire, le `HGLOBAL` spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le `HGLOBAL` ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réaffecté à une plus grande taille.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [se](#onrenderdata). Si vos données sont dans un fichier, ou de taille variable, substituez [OnRenderFileData](#onrenderfiledata).  
  
 Pour plus d’informations, consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme  
 Appelé par l’infrastructure pour spécifier une palette de couleurs à utiliser lors de la modification de l’élément OLE.  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpLogPalette*  
 Pointeur vers un Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la palette de couleurs est utilisée ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’application conteneur a été écrit à l’aide de la bibliothèque Microsoft Foundation Class, cette fonction est appelée lorsque le [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) fonction correspondantes `COleClientItem` objet est appelé. L’implémentation par défaut retourne **FALSE**. Remplacez cette fonction si vous souhaitez utiliser la palette recommandée. L’application serveur n’est pas requis pour utiliser la palette suggérée.  
  
 Pour plus d’informations, consultez [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) dans le Kit de développement logiciel Windows.  
  
##  <a name="onsetdata"></a>  COleServerItem::OnSetData  
 Appelé par l’infrastructure pour remplacer les données de l’élément OLE avec les données spécifiées.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointeur vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format des données.  
  
 *lpStgMedium*  
 Pointeur vers un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure dans laquelle les données résident.  
  
 *bRelease*  
 Indique qui a la propriété du support de stockage de la fin de l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées pour le compte au support de stockage. L’appelant en définissant ne *bRelease*. Si *bRelease* est différent de zéro, l’élément serveur prend possession, la libération du support lorsqu’il est terminé. Lorsque *bRelease* est 0, l’appelant conserve la propriété et l’élément de serveur peut utiliser le support de stockage uniquement pendant la durée de l’appel.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’élément du serveur ne prend pas la propriété des données jusqu'à ce qu’il a obtenu avec succès. Autrement dit, il ne prend pas la propriété si elle retourne 0. Si la source de données prend la propriété, il libère le support de stockage en appelant le [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) (fonction).  
  
 L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour remplacer les données de l’élément OLE avec les données spécifiées. Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), et [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) dans le Kit de développement logiciel Windows.  
  
##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent  
 Appelé par le framework pour indiquer l’élément OLE à la quantité d’espace est disponible à ce dernier dans le document conteneur.  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawAspect*  
 Spécifie l’aspect de l’élément OLE dont les limites sont spécifiés. Ce paramètre peut prendre une des valeurs suivantes :  
  
- `DVASPECT_CONTENT` Élément est représenté de façon à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- `DVASPECT_THUMBNAIL` Élément est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- `DVASPECT_ICON` Élément est représenté par une icône.  
  
- `DVASPECT_DOCPRINT` Élément est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
 *size*  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) structure qui spécifie la nouvelle taille de l’élément OLE.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’application conteneur a été écrit avec la bibliothèque Microsoft Foundation Class, cette fonction est appelée lorsque le [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) fonction membre correspondantes `COleClientItem` objet est appelé. L’implémentation par défaut définit les [m_sizeExtent](#m_sizeextent) membre à la taille spécifiée si *nDrawAspect* est `DVASPECT_CONTENT`; sinon, elle retourne 0. Remplacez cette fonction pour effectuer un traitement spécial lorsque vous modifiez la taille de l’élément.  
  
##  <a name="onshow"></a>  COleServerItem::OnShow  
 Appelé par le framework pour indiquer à l’application de serveur pour afficher l’élément OLE sur place.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée lorsque l’utilisateur de l’application conteneur crée un élément ou exécute un verbe, comme modifier, ce qui requiert l’élément à afficher. L’implémentation par défaut tente l’activation sur place. Si cela échoue, la fonction appelle la `OnOpen` fonction membre pour afficher l’élément OLE dans une fenêtre distincte.  
  
 Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’un élément OLE est indiqué.  
  
##  <a name="onupdate"></a>  COleServerItem::OnUpdate  
 Appelé par l’infrastructure lorsqu’un élément a été modifié.  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pSender*  
 Pointeur vers l’élément qui a modifié le document. Peut être **NULL**.  
  
 *lHint*  
 Contient des informations sur la modification.  
  
 *pHint*  
 Pointeur vers un objet stockant les informations sur la modification.  
  
 *nDrawAspect*  
 Valeur de l'énumération `DVASPECT`. Ce paramètre peut avoir l’une des valeurs suivantes :  
  
- `DVASPECT_CONTENT` Élément est représenté de façon à ce qu’il peut être affiché en tant qu’objet incorporé à l’intérieur de son conteneur.  
  
- `DVASPECT_THUMBNAIL` Élément est rendu dans une représentation sous forme de « miniature » afin qu’il peut être affiché dans un outil de navigation.  
  
- `DVASPECT_ICON` Élément est représenté par une icône.  
  
- `DVASPECT_DOCPRINT` Élément est représenté comme s’il était imprimé à l’aide de la commande Imprimer dans le menu fichier.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut appelle [NotifyChanged](#notifychanged), quel que soit l’expéditeur ou l’indicateur.  
  
##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems  
 Appelé par l’infrastructure pour mettre à jour tous les éléments dans le document serveur.  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut appelle [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) pour toutes les `COleClientItem` objets du document.  
  
##  <a name="setitemname"></a>  COleServerItem::SetItemName  
 Appelez cette fonction lorsque vous créez un élément lié pour définir son nom.  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszItemName*  
 Pointeur vers le nouveau nom de l’élément.  
  
### <a name="remarks"></a>Notes  
 Le nom doit être unique dans le document. Lorsqu’une application serveur est appelée pour modifier un élément lié, l’application utilise ce nom pour rechercher l’élément. Vous n’avez pas besoin d’appeler cette fonction pour les éléments incorporés.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Classe de CDocItem](../../mfc/reference/cdocitem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Classe de COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
