---
title: Classe de COleDataSource | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
dev_langs:
- C++
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3b5060c850a1fcdba089b732d019f958f2e7410
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038553"
---
# <a name="coledatasource-class"></a>Classe de COleDataSource
Agit comme un cache dans lequel une application place les données qu’elle proposera pendant les opérations de transfert de données, par exemple les opérations du Presse-papiers ou de glisser-déposer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|Construit un objet `COleDataSource`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|Propose des données dans un format spécifié à l’aide un **STGMEDIUM** structure.|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Propose des données dans un format spécifié à l’aide un `HGLOBAL`.|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|Offre des données dans un format spécifié à l’aide de rendu retardé.|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Propose des données dans un format spécifié dans un `CFile` pointeur.|  
|[COleDataSource::DelaySetData](#delaysetdata)|Appelé pour tous les formats pris en charge dans `OnSetData`.|  
|[COleDataSource::DoDragDrop](#dodragdrop)|Effectue des opérations de glisser-déplacer avec une source de données.|  
|[COleDataSource::Empty](#empty)|Vide le `COleDataSource` objet de données.|  
|[COleDataSource::FlushClipboard](#flushclipboard)|Restitue toutes les données dans le Presse-papiers.|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Vérifie que les données placées dans le Presse-papiers soient toujours active.|  
|[COleDataSource::OnRenderData](#onrenderdata)|Récupère les données dans le cadre de rendu retardé.|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Récupère des données dans un `CFile` dans le cadre de rendu retardé.|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Récupère des données dans un `HGLOBAL` dans le cadre de rendu retardé.|  
|[COleDataSource::OnSetData](#onsetdata)|Appelé pour remplacer les données dans le `COleDataSource` objet.|  
|[COleDataSource::SetClipboard](#setclipboard)|Place un `COleDataSource` objet dans le Presse-papiers.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer des sources de données OLE directement. Vous pouvez également le [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md) classes créent des sources de données OLE en réponse à leurs `CopyToClipboard` et `DoDragDrop` fonctions membres. Consultez [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) pour une brève description. Remplacer la `OnGetClipboardData` fonction membre de votre classe client d’élément article ou de serveur pour ajouter des formats de Presse-papiers supplémentaires aux données dans la source de données OLE créé pour le `CopyToClipboard` ou `DoDragDrop` fonction membre.  
  
 Chaque fois que vous souhaitez préparer les données pour un transfert, vous devez créer un objet de cette classe et le remplir avec vos données à l’aide de la méthode la plus appropriée pour vos données. La méthode, il est inséré dans une source de données est directement affectée par indique si les données sont fournies immédiatement (rendu immédiat) ou à la demande (rendu retardé). Pour chaque format de Presse-papiers dans lequel vous fournissez des données en passant le format de Presse-papiers pour être utilisé (et éventuellement un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure), appelez [DelayRenderData](#delayrenderdata).  
  
 Pour plus d’informations sur les sources de données et de transfert de données, consultez l’article [des objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md). En outre, l’article [rubriques du Presse-papiers](../../mfc/clipboard.md) décrit le mécanisme de Presse-papiers OLE.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="cachedata"></a>  COleDataSource::CacheData  
 Appelez cette fonction pour spécifier un format dans lequel données sont proposées pendant les données des opérations de transfert.  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de Presse-papiers dans lequel les données doit être proposé. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpStgMedium*  
 Pointe vers un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure contenant les données dans le format spécifié.  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données doit être proposé. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="remarks"></a>Notes  
 Vous devez fournir les données, car cette fonction fournit à l’aide de rendu immédiat. Les données sont mis en cache jusqu'à ce que nécessaire.  
  
 Spécifiez les données à l’aide un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure. Vous pouvez également utiliser le `CacheGlobalData` fonction membre si la quantité de données que vous fournissez est assez petite pour être transféré à l’aide de manière efficace un `HGLOBAL`.  
  
 Après l’appel à `CacheData` le **ptd** membre `lpFormatEtc` et le contenu de `lpStgMedium` sont détenus par l’objet de données, pas par l’appelant.  
  
 Pour utiliser le rendu retardé, appelez le [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) fonction membre. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour plus d’informations, consultez la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structures dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData  
 Appelez cette fonction pour spécifier un format dans lequel données sont proposées pendant les données des opérations de transfert.  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de Presse-papiers dans lequel les données doit être proposé. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *hGlobal*  
 Handle vers le bloc de mémoire globale qui contient les données dans le format spécifié.  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données doit être proposé. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="remarks"></a>Notes  
 Cette fonction fournit les données à l’aide de rendu immédiate, vous devez fournir les données lors de l’appel de la fonction ; les données sont mis en cache jusqu'à ce que nécessaire. Utilisez le `CacheData` fonction membre si vous fournissez une grande quantité de données ou si vous avez besoin d’un support de stockage structuré.  
  
 Pour utiliser le rendu retardé, appelez le [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) fonction membre. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="coledatasource"></a>  COleDataSource::COleDataSource  
 Construit un objet `COleDataSource`.  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData  
 Appelez cette fonction pour spécifier un format dans lequel données sont proposées pendant les données des opérations de transfert.  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de Presse-papiers dans lequel les données doit être proposé. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données doit être proposé. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="remarks"></a>Notes  
 Cette fonction fournit les données à l’aide de rendu retardé, les données ne sont pas fournies immédiatement. Le [se](#onrenderdata) ou [OnRenderGlobalData](#onrenderglobaldata) fonction membre est appelée pour demander les données.  
  
 Utilisez cette fonction si vous ne souhaitez pas fournir de vos données grâce à une `CFile` objet. Si vous vous apprêtez à fournir les données via un `CFile` de l’objet, appelez le [DelayRenderFileData](#delayrenderfiledata) fonction membre. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour utiliser le rendu immédiat, appelez le [CacheData](#cachedata) ou [CacheGlobalData](#cacheglobaldata) fonction membre.  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData  
 Appelez cette fonction pour spécifier un format dans lequel données sont proposées pendant les données des opérations de transfert.  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de Presse-papiers dans lequel les données doit être proposé. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données doit être proposé. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="remarks"></a>Notes  
 Cette fonction fournit les données à l’aide de rendu retardé, les données ne sont pas fournies immédiatement. Le [OnRenderFileData](#onrenderfiledata) fonction membre est appelée pour demander les données.  
  
 Utilisez cette fonction si vous vous apprêtez à utiliser un `CFile` objet pour fournir les données. Si vous ne souhaitez pas utiliser un `CFile` de l’objet, appelez le [DelayRenderData](#delayrenderdata) fonction membre. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour utiliser le rendu immédiat, appelez le [CacheData](#cachedata) ou [CacheGlobalData](#cacheglobaldata) fonction membre.  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData  
 Appelez cette fonction pour prendre en charge la modification du contenu de la source de données.  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de Presse-papiers dans lequel les données doit être placé. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données doit être remplacé. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="remarks"></a>Notes  
 [OnSetData](#onsetdata) sera appelé par le framework lorsque cela se produit. Il est utilisé uniquement lorsque le framework retourne la source de données à partir de [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` n’est pas appelée, votre `OnSetData` fonction ne sera jamais appelée. `DelaySetData` doit être appelée pour chaque Presse-papiers ou **FORMATETC** format pris en charge.  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop  
 Appelez le `DoDragDrop` fonction membre pour effectuer une opération de glisser-déplacer pour cette source de données, en général dans un [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) gestionnaire.  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwEffects*  
 Glisser-déplacer les opérations autorisées sur cette source de données. Peut être une ou plusieurs des opérations suivantes :  
  
- `DROPEFFECT_COPY` Une opération de copie peut être effectuée.  
  
- `DROPEFFECT_MOVE` Une opération de déplacement peut être effectuée.  
  
- `DROPEFFECT_LINK` Un lien entre les données déplacées et les données d’origine a pu être établi.  
  
- `DROPEFFECT_SCROLL` Indique qu’une opération de glissement de défilement peut se produire.  
  
 *lpRectStartDrag*  
 Pointeur vers le rectangle qui définit où commence l’opération glisser. Pour plus d'informations, consultez la section Notes qui suit.  
  
 *pDropSource*  
 Pointe vers une source de déplacement. Si **NULL** ensuite une implémentation par défaut de [COleDropSource](../../mfc/reference/coledropsource-class.md) sera utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Effet généré par l’opération de glisser-déplacer ; dans le cas contraire `DROPEFFECT_NONE` si l’opération commence jamais, car l’utilisateur a relâché le bouton de la souris avant de quitter le rectangle fourni.  
  
### <a name="remarks"></a>Notes  
 L’opération de glisser-déposer ne commence pas immédiatement. Il attend jusqu'à ce que le curseur de la souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu'à ce qu’un nombre spécifié de millisecondes écoulées. Si *lpRectStartDrag* est **NULL**, la taille du rectangle est un pixel.  
  
 Délai d’attente est spécifié par un paramètre de clé de Registre. Vous pouvez modifier le délai d’attente en appelant [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas de délai d’attente, 200 millisecondes comme valeur par défaut est utilisée. Faites glisser retarder l’heure est stockée comme suit :  
  
-   Retarder l’heure de glissement de Windows NT est stocké dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Retarder l’heure de Windows 3.x glisser est stocké dans le fichier WIN. Fichier INI, la section [Windows}.  
  
-   Retarder l’heure de Windows 95/98 glisser est stocké dans une version mise en cache de Windows. INI.  
  
 Pour plus d’informations sur la façon de faire glisser les informations de délai sont stockées dans le Registre ou le. Fichier INI, consultez [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez l’article [glisser -déplacer : implémentation d’une Source de Drop](../../mfc/drag-and-drop-implementing-a-drop-source.md).  
  
##  <a name="empty"></a>  COleDataSource::Empty  
 Appelez cette fonction pour vider le `COleDataSource` objet de données.  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>Notes  
 Les deux mises en cache et les formats de rendu de délai sont vidées afin qu’elles puissent être réutilisées.  
  
 Pour plus d’informations, consultez [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) dans le Kit de développement logiciel Windows.  
  
##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard  
 Restitue les données dans le Presse-papiers, puis vous permet de coller des données à partir du Presse-papiers une fois que votre application s’arrête.  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>Notes  
 Utilisez [l’activation du Presse-papiers](#setclipboard) pour placer des données dans le Presse-papiers.  
  
##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner  
 Détermine si les données dans le Presse-papiers a changé depuis [l’activation du Presse-papiers](#setclipboard) dernier appel et, dans ce cas, identifie le propriétaire actuel.  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La source de données dans le Presse-papiers, ou **NULL** si aucune n’est dans le Presse-papiers, ou si le Presse-papiers n’est pas détenu par l’application appelante.  
  
##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData  
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
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction appelle [OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata) si le support de stockage fourni est un fichier ou la mémoire, respectivement. Si aucune de ces formats sont fournis, l’implémentation par défaut retourne 0 et ne rien faire. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Si *lpStgMedium*-> *tymed* est **TYMED_NULL**, le **STGMEDIUM** doit être alloué et rempli comme spécifié par *lpFormatEtc -> tymed*. Si elle n’est pas **TYMED_NULL**, le **STGMEDIUM** devrait normalement être en place avec les données.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez substituer l’une des autres versions de cette fonction à la place. Si vos données soient petite et une taille fixe, substituez `OnRenderGlobalData`. Si vos données sont dans un fichier, ou de taille variable, substituez `OnRenderFileData`.  
  
 Pour plus d’informations, consultez la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structures, les [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) type énumération, et [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) dans le SDK Windows.  
  
##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData  
 Appelé par l’infrastructure pour récupérer des données dans le format spécifié lorsque le support de stockage spécifié est un fichier.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format dans lequel les informations sont demandées.  
  
 *pFile*  
 Pointe vers un [CFile](../../mfc/reference/cfile-class.md) objet dans lequel les données doivent être rendus.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](#delayrenderdata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction retourne simplement **FALSE**.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [se](#onrenderdata). Si vos données sont dans un fichier, ou de taille variable, substituez `OnRenderFileData`. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure et [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) dans le Kit de développement logiciel Windows.  
  
##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData  
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
 Pointe vers un handle de mémoire globale dans laquelle les données sont à retourner. Si un n’a pas encore été alloué, ce paramètre peut être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le format spécifié est un auparavant placé dans le `COleDataSource` à l’aide de l’objet le [DelayRenderData](#delayrenderdata) fonction membre pour le rendu retardé. L’implémentation par défaut de cette fonction retourne simplement **FALSE**.  
  
 Si *phGlobal* est **NULL**, puis une nouvelle `HGLOBAL` doit être allouée et retournée dans *phGlobal*. Dans le cas contraire, le `HGLOBAL` spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le `HGLOBAL` ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réaffecté à une plus grande taille.  
  
 Il s’agit d’une avancée substituable. Remplacez cette fonction pour fournir vos données dans le format demandé et le support. En fonction de vos données, vous souhaiterez substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [se](#onrenderdata). Si vos données sont dans un fichier, ou de taille variable, substituez [OnRenderFileData](#onrenderfiledata). Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour plus d’informations, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure et [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) dans le Kit de développement logiciel Windows.  
  
##  <a name="onsetdata"></a>  COleDataSource::OnSetData  
 Appelé par l’infrastructure pour définir ou remplacer les données dans le `COleDataSource` objet au format spécifié.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui spécifie le format dans lequel les données sont remplacées.  
  
 *lpStgMedium*  
 Pointe vers le [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure contenant les données qui remplacent le contenu actuel de la `COleDataSource` objet.  
  
 *bRelease*  
 Indique qui a la propriété du support de stockage de la fin de l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées pour le compte au support de stockage. L’appelant en définissant ne *bRelease*. Si *bRelease* est différent de zéro, la source de données prend possession, la libération du support lorsqu’il est terminé. Lorsque *bRelease* est 0, l’appelant conserve la propriété et la source de données peut utiliser le support de stockage uniquement pendant la durée de l’appel.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La source de données ne prend pas la propriété des données jusqu'à ce qu’il a obtenu avec succès. Autrement dit, il ne prend pas possession si `OnSetData` retourne 0. Si la source de données prend la propriété, il libère le support de stockage en appelant le [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) (fonction).  
  
 L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour remplacer les données dans le format spécifié. Il s’agit d’une avancée substituable.  
  
 Pour plus d’informations, consultez la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structures et [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) et [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) fonctions dans le SDK Windows.  
  
##  <a name="setclipboard"></a>  COleDataSource::SetClipboard  
 Place les données contenues dans le `COleDataSource` objet dans le Presse-papiers après l’appel d’une des fonctions suivantes : [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), ou [DelayRenderFileData](#delayrenderfiledata).  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDataObject, classe](../../mfc/reference/coledataobject-class.md)
