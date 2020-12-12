---
description: 'En savoir plus sur : COleDataSource Class'
title: COleDataSource, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 1fc6dd8a7df1d8b841c4f95a14c2bd1708c94fd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227323"
---
# <a name="coledatasource-class"></a>COleDataSource, classe

Agit comme un cache dans lequel une application place les données qu’elle proposera pendant les opérations de transfert de données, par exemple les opérations du Presse-papiers ou de glisser-déposer.

## <a name="syntax"></a>Syntaxe

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDataSource :: COleDataSource](#coledatasource)|Construit un objet `COleDataSource`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDataSource :: CacheData](#cachedata)|Fournit des données dans un format spécifié à l’aide d’une `STGMEDIUM` structure.|
|[COleDataSource :: CacheGlobalData](#cacheglobaldata)|Fournit des données dans un format spécifié à l’aide d’un HGLOBAL.|
|[COleDataSource ::D elayRenderData](#delayrenderdata)|Offre des données dans un format spécifié à l’aide d’un rendu retardé.|
|[COleDataSource ::D elayRenderFileData](#delayrenderfiledata)|Fournit des données dans un format spécifié dans un `CFile` pointeur.|
|[COleDataSource ::D elaySetData](#delaysetdata)|Appelé pour chaque format pris en charge dans `OnSetData` .|
|[COleDataSource ::D oDragDrop](#dodragdrop)|Effectue des opérations de glisser-déplacer avec une source de données.|
|[COleDataSource :: Empty](#empty)|Vide l' `COleDataSource` objet de données.|
|[COleDataSource :: FlushClipboard](#flushclipboard)|Génère le rendu de toutes les données dans le presse-papiers.|
|[COleDataSource :: GetClipboardOwner](#getclipboardowner)|Vérifie que les données placées dans le presse-papiers sont toujours là.|
|[COleDataSource :: OnRenderData](#onrenderdata)|Récupère des données dans le cadre d’un rendu retardé.|
|[COleDataSource :: OnRenderFileData](#onrenderfiledata)|Récupère des données dans un dans le `CFile` cadre d’un rendu retardé.|
|[COleDataSource :: OnRenderGlobalData](#onrenderglobaldata)|Récupère des données dans un HGLOBAL dans le cadre du rendu retardé.|
|[COleDataSource :: OnSetData](#onsetdata)|Appelé pour remplacer les données dans l' `COleDataSource` objet.|
|[COleDataSource :: SetClipboard](#setclipboard)|Place un `COleDataSource` objet dans le presse-papiers.|

## <a name="remarks"></a>Notes

Vous pouvez créer directement des sources de données OLE. Les classes [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md) créent également des sources de données OLE en réponse à leurs `CopyToClipboard` `DoDragDrop` fonctions membres et. Consultez [COleServerItem :: copytoclipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) pour obtenir une brève description. Substituez la `OnGetClipboardData` fonction membre de votre classe d’élément client ou d’élément de serveur pour ajouter des formats de presse-papiers supplémentaires aux données de la source de données OLE créée pour la `CopyToClipboard` `DoDragDrop` fonction membre ou.

Chaque fois que vous souhaitez préparer des données pour un transfert, vous devez créer un objet de cette classe et le remplir avec vos données à l’aide de la méthode la plus appropriée pour vos données. La façon dont il est inséré dans une source de données est directement affectée par le fait que les données soient fournies immédiatement (rendu immédiat) ou à la demande (rendu retardé). Pour chaque format de presse-papiers dans lequel vous fournissez des données en passant le format de presse-papiers à utiliser (et une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) facultative), appelez [DelayRenderData](#delayrenderdata).

Pour plus d’informations sur les sources de données et le transfert de données, consultez l’article [objets de données et sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md). En outre, les rubriques de l’article [presse-papiers](../../mfc/clipboard.md) décrivent le mécanisme OLE Clipboard.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a> COleDataSource :: CacheData

Appelez cette fonction pour spécifier un format dans lequel les données sont proposées pendant les opérations de transfert de données.

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format du presse-papiers dans lequel les données doivent être proposées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpStgMedium*<br/>
Pointe vers une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) contenant les données au format spécifié.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être proposées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="remarks"></a>Notes

Vous devez fournir les données, car cette fonction les fournit en utilisant le rendu immédiat. Les données sont mises en cache jusqu’à ce que cela soit nécessaire.

Fournissez les données à l’aide d’une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) . Vous pouvez également utiliser la `CacheGlobalData` fonction membre si la quantité de données que vous fournissez est suffisamment petite pour être transférée efficacement à l’aide d’un HGLOBAL.

Après l’appel au `CacheData` `ptd` membre de `lpFormatEtc` et le contenu de *lpStgMedium* sont détenus par l’objet de données, et non par l’appelant.

Pour utiliser le rendu retardé, appelez la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) . Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a> COleDataSource :: CacheGlobalData

Appelez cette fonction pour spécifier un format dans lequel les données sont proposées pendant les opérations de transfert de données.

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format du presse-papiers dans lequel les données doivent être proposées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*hGlobal*<br/>
Handle du bloc de mémoire globale contenant les données dans le format spécifié.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être proposées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide du rendu immédiat. vous devez donc fournir les données lors de l’appel de la fonction ; les données sont mises en cache jusqu’à ce que cela soit nécessaire. Utilisez la `CacheData` fonction membre si vous fournissez une grande quantité de données ou si vous avez besoin d’un support de stockage structuré.

Pour utiliser le rendu retardé, appelez la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) . Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a> COleDataSource :: COleDataSource

Construit un objet `COleDataSource`.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a> COleDataSource ::D elayRenderData

Appelez cette fonction pour spécifier un format dans lequel les données sont proposées pendant les opérations de transfert de données.

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format du presse-papiers dans lequel les données doivent être proposées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être proposées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide d’un rendu retardé, donc les données ne sont pas fournies immédiatement. La fonction membre [OnRenderData](#onrenderdata) ou [OnRenderGlobalData](#onrenderglobaldata) est appelée pour demander les données.

Utilisez cette fonction si vous n’allez pas fournir vos données par le biais d’un `CFile` objet. Si vous prévoyez de fournir les données à l’aide d’un `CFile` objet, appelez la fonction membre [DelayRenderFileData](#delayrenderfiledata) . Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour utiliser le rendu immédiat, appelez la fonction membre [CacheData](#cachedata) ou [CacheGlobalData](#cacheglobaldata) .

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a> COleDataSource ::D elayRenderFileData

Appelez cette fonction pour spécifier un format dans lequel les données sont proposées pendant les opérations de transfert de données.

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format du presse-papiers dans lequel les données doivent être proposées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être proposées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide d’un rendu retardé, donc les données ne sont pas fournies immédiatement. La fonction membre [OnRenderFileData](#onrenderfiledata) est appelée pour demander les données.

Utilisez cette fonction si vous prévoyez d’utiliser un `CFile` objet pour fournir les données. Si vous n’allez pas utiliser un `CFile` objet, appelez la fonction membre [DelayRenderData](#delayrenderdata) . Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour utiliser le rendu immédiat, appelez la fonction membre [CacheData](#cachedata) ou [CacheGlobalData](#cacheglobaldata) .

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a> COleDataSource ::D elaySetData

Appelez cette fonction pour prendre en charge la modification du contenu de la source de données.

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format du presse-papiers dans lequel les données doivent être placées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être remplacées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="remarks"></a>Notes

[OnSetData](#onsetdata) sera appelé par l’infrastructure lorsque cela se produit. Utilisé uniquement lorsque le Framework retourne la source de données à partir de [COleServerItem :: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` n’est pas appelé, votre `OnSetData` fonction ne sera jamais appelée. `DelaySetData` doit être appelé pour chaque presse-papiers ou `FORMATETC` format que vous prenez en charge.

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a> COleDataSource ::D oDragDrop

Appelez la `DoDragDrop` fonction membre pour effectuer une opération de glisser-déplacer pour cette source de données, généralement dans un gestionnaire [CWnd :: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) .

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Paramètres

*dwEffects*<br/>
Opérations de glisser-déplacer autorisées sur cette source de données. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_COPY une opération de copie a pu être effectuée.

- DROPEFFECT_MOVE une opération de déplacement a pu être effectuée.

- DROPEFFECT_LINK un lien entre les données déplacées et les données d’origine peuvent être établies.

- DROPEFFECT_SCROLL indique qu’une opération de glissement de défilement peut se produire.

*lpRectStartDrag*<br/>
Pointeur vers le rectangle qui définit où le glissement commence réellement. Pour plus d'informations, consultez la section Notes qui suit.

*pDropSource*<br/>
Pointe vers une source de déplacement. Si la valeur est NULL, une implémentation par défaut de [COleDropSource](../../mfc/reference/coledropsource-class.md) sera utilisée.

### <a name="return-value"></a>Valeur renvoyée

Effet de déplacement généré par l’opération de glisser-déplacer ; sinon DROPEFFECT_NONE si l’opération ne commence jamais parce que l’utilisateur a relâché le bouton de la souris avant de quitter le rectangle fourni.

### <a name="remarks"></a>Notes

L’opération de glisser-déplacer ne démarre pas immédiatement. Elle attend que le curseur de la souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu’à ce qu’un nombre spécifié de millisecondes soit écoulé. Si *lpRectStartDrag* a la valeur null, la taille du rectangle est d’un pixel.

Le délai est spécifié par un paramètre de clé de registre. Vous pouvez modifier le délai en appelant [CWinApp :: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp :: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas de délai, une valeur par défaut de 200 millisecondes est utilisée. Le délai de glissement est stocké comme suit :

- Le délai de glissement de Windows NT est stocké dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini \Windows\DragDelay.

- Le délai de glissement de Windows 3. x est stocké dans le fichier WIN.INI, sous la section [Windows}.

- Le délai de glissement de Windows 95/98 est stocké dans une version mise en cache de WIN.INI.

Pour plus d’informations sur la façon dont les informations sur les retards de glissement sont stockées dans le registre ou le. INI, consultez [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) dans le SDK Windows.

Pour plus d’informations, consultez l’article [glisser-déplacer OLE](../../mfc/drag-and-drop-ole.md).

## <a name="coledatasourceempty"></a><a name="empty"></a> COleDataSource :: Empty

Appelez cette fonction pour vider l' `COleDataSource` objet de données.

```cpp
void Empty();
```

### <a name="remarks"></a>Notes

Les formats de rendu mis en cache et différés sont vidés afin de pouvoir être réutilisés.

Pour plus d’informations, consultez [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) dans le SDK Windows.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a> COleDataSource :: FlushClipboard

Affiche les données qui se trouvent dans le presse-papiers, puis vous permet de coller des données à partir du presse-papiers après l’arrêt de votre application.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Notes

Utilisez [SetClipboard](#setclipboard) pour placer des données dans le presse-papiers.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a> COleDataSource :: GetClipboardOwner

Détermine si les données du presse-papiers ont changé depuis le dernier appel à [SetClipboard](#setclipboard) et, le cas échéant, identifie le propriétaire actuel.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Valeur renvoyée

Source de données actuellement dans le presse-papiers, ou NULL s’il n’y a rien dans le presse-papiers ou si le presse-papiers n’est pas détenu par l’application appelante.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a> COleDataSource :: OnRenderData

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

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) pour un rendu retardé. L’implémentation par défaut de cette fonction appellera [OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata) si le support de stockage fourni est un fichier ou une mémoire, respectivement. Si aucun de ces formats n’est fourni, l’implémentation par défaut retourne 0 et ne fait rien. Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Si *lpStgMedium* ->  *TYMED* est TYMED_NULL, `STGMEDIUM` doit être alloué et rempli comme spécifié par *lpFormatEtc->TYMED*. S’il n’est pas TYMED_NULL, `STGMEDIUM` doit être renseigné avec les données.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vos données sont de taille petite et fixe, remplacez `OnRenderGlobalData` . Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez `OnRenderFileData` .

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , le type d’énumération [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) et [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a> COleDataSource :: OnRenderFileData

Appelé par le Framework pour récupérer des données dans le format spécifié lorsque le support de stockage spécifié est un fichier.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en spécifiant le format dans lequel les informations sont demandées.

*pFile*<br/>
Pointe vers un objet [CFile](../../mfc/reference/cfile-class.md) dans lequel les données doivent être restituées.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](#delayrenderdata) pour un rendu retardé. L’implémentation par défaut de cette fonction retourne simplement FALSe.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez `OnRenderFileData` . Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a> COleDataSource :: OnRenderGlobalData

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
Pointe vers un handle vers la mémoire globale dans laquelle les données doivent être retournées. Si aucun n’a encore été alloué, ce paramètre peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un précédemment placé dans l' `COleDataSource` objet à l’aide de la fonction membre [DelayRenderData](#delayrenderdata) pour un rendu retardé. L’implémentation par défaut de cette fonction retourne simplement FALSe.

Si *phGlobal* a la valeur null, un nouveau HGLOBAL doit être alloué et retourné dans *phGlobal*. Dans le cas contraire, le HGLOBAL spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le HGLOBAL ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réalloué à une plus grande taille.

Il s’agit d’un substituable avancé. Substituez cette fonction pour fournir vos données au format et au support demandés. Selon vos données, vous souhaiterez peut-être substituer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données se trouvent dans un fichier ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata). Pour plus d’informations sur le rendu retardé comme géré par MFC, consultez l’article [objets de données et sources de données : manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a> COleDataSource :: OnSetData

Appelé par l’infrastructure pour définir ou remplacer les données dans l' `COleDataSource` objet dans le format spécifié.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en spécifiant le format dans lequel les données sont remplacées.

*lpStgMedium*<br/>
Pointe vers la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) contenant les données qui remplaceront le contenu actuel de l' `COleDataSource` objet.

*bRelease*<br/>
Indique qui a la propriété du support de stockage après avoir effectué l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées pour le compte du support de stockage. Pour ce faire, l’appelant définit *bRelease*. Si *bRelease* est différent de zéro, la source de données prend possession, en libérant le support une fois qu’il a fini de l’utiliser. Quand *bRelease* a la valeur 0, l’appelant conserve la propriété et la source de données ne peut utiliser le support de stockage que pendant la durée de l’appel.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La source de données ne prend pas possession des données tant qu’elle n’a pas été obtenue. Autrement dit, il ne prend pas possession de la `OnSetData` valeur si retourne 0. Si la source de données prend possession, elle libère le support de stockage en appelant la fonction [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

L'implémentation par défaut n'exécute aucune opération. Substituez cette fonction pour remplacer les données au format spécifié. Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et les fonctions [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) et [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a> COleDataSource :: SetClipboard

Place les données contenues dans l' `COleDataSource` objet dans le presse-papiers après l’appel de l’une des fonctions suivantes : [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)ou [DelayRenderFileData](#delayrenderfiledata).

```cpp
void SetClipboard();
```

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject, classe](../../mfc/reference/coledataobject-class.md)
