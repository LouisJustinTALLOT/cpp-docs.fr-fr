---
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
ms.openlocfilehash: 8746be43e3f2a31558904323392983b183d4f198
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753896"
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
|[COleDataSource::COleDataSource](#coledatasource)|Construit un objet `COleDataSource`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Offre des données dans `STGMEDIUM` un format spécifié à l’aide d’une structure.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Offre des données dans un format spécifié à l’aide d’un HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Offre des données dans un format spécifié à l’aide d’un rendu retardé.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Offre des données dans `CFile` un format spécifié dans un pointeur.|
|[COleDataSource::DelaySetData](#delaysetdata)|Appelé pour chaque format `OnSetData`qui est pris en charge dans .|
|[COleDataSource::DoDragDrop](#dodragdrop)|Effectue des opérations de drag-and-drop avec une source de données.|
|[COleDataSource::Vide](#empty)|Vide l’objet `COleDataSource` des données.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Rend toutes les données sur le Clipboard.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Vérifie que les données placées sur le Clipboard sont toujours là.|
|[COleDataSource::OnRenderData](#onrenderdata)|Récupère les données dans le cadre du rendu retardé.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Récupère les données `CFile` dans un cadre du rendu retardé.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Récupère les données dans un HGLOBAL dans le cadre du rendu retardé.|
|[COleDataSource::OnSetData](#onsetdata)|Appelé pour remplacer les `COleDataSource` données dans l’objet.|
|[COleDataSource::SetClipboard](#setclipboard)|Place `COleDataSource` un objet sur le Clipboard.|

## <a name="remarks"></a>Notes

Vous pouvez créer directement des sources de données OLE. Alternativement, les classes [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md) créent des `CopyToClipboard` `DoDragDrop` sources de données OLE en réponse à leurs fonctions et à leurs fonctions de membre. Voir [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) pour une brève description. Remplacez `OnGetClipboardData` la fonction membre de votre élément client ou de la classe d’élément serveur pour `CopyToClipboard` `DoDragDrop` ajouter des formats Clipboard supplémentaires aux données de la source de données OLE créée pour la fonction ou la fonction membre.

Chaque fois que vous souhaitez préparer des données pour un transfert, vous devez créer un objet de cette classe et les remplir de vos données en utilisant la méthode la plus appropriée pour vos données. La façon dont elles sont insérées dans une source de données est directement affectée par la question de savoir si les données sont fournies immédiatement (rendu immédiat) ou à la demande (rendu retardé). Pour chaque format Clipboard dans lequel vous fournissez des données en passant le format Clipboard à utiliser (et une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en option), appelez [DelayRenderData](#delayrenderdata).

Pour plus d’informations sur les sources de données et le transfert de données, consultez l’article [Data Objects and Data Sources (OLE)](../../mfc/data-objects-and-data-sources-ole.md). En outre, l’article [Clipboard Topics](../../mfc/clipboard.md) décrit le mécanisme OLE Clipboard.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleDataSource::CacheData

Appelez cette fonction pour spécifier un format dans lequel les données sont offertes lors des opérations de transfert de données.

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format Clipboard dans lequel les données doivent être offertes. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgMedium*<br/>
Indique une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) contenant les données dans le format spécifié.

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être offertes. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les `FORMATETC` valeurs par défaut sont utilisées pour les autres champs de la structure.

### <a name="remarks"></a>Notes

Vous devez fournir les données, car cette fonction les fournit en utilisant le rendu immédiat. Les données sont mises en cache jusqu’à ce qu’elles soient nécessaires.

Fournir les données à l’aide d’une structure [STGMEDIUM.](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) Vous pouvez également `CacheGlobalData` utiliser la fonction membre si la quantité de données que vous fournissez est assez faible pour être transférée efficacement à l’aide d’un HGLOBAL.

Après l’appel `ptd` au `lpFormatEtc` `CacheData` membre et le contenu de *lpStgMedium* sont la propriété de l’objet de données, pas par l’appelant.

Pour utiliser le rendu retardé, appelez la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData.](#delayrenderfiledata) Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData

Appelez cette fonction pour spécifier un format dans lequel les données sont offertes lors des opérations de transfert de données.

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format Clipboard dans lequel les données doivent être offertes. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*hGlobal (en)*<br/>
Gérer le bloc mémoire global contenant les données dans le format spécifié.

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être offertes. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les `FORMATETC` valeurs par défaut sont utilisées pour les autres champs de la structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide d’un rendu immédiat, vous devez donc fournir les données lors de l’appel de la fonction; les données sont mises en cache jusqu’à ce qu’elles soient nécessaires. Utilisez `CacheData` la fonction membre si vous fournissez une grande quantité de données ou si vous avez besoin d’un support de stockage structuré.

Pour utiliser le rendu retardé, appelez la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData.](#delayrenderfiledata) Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleDataSource::COleDataSource

Construit un objet `COleDataSource`.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleDataSource::DelayRenderData

Appelez cette fonction pour spécifier un format dans lequel les données sont offertes lors des opérations de transfert de données.

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format Clipboard dans lequel les données doivent être offertes. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être offertes. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les `FORMATETC` valeurs par défaut sont utilisées pour les autres champs de la structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide de rendu retardé, de sorte que les données ne sont pas fournies immédiatement. La fonction membre [OnRenderData](#onrenderdata) ou [OnRenderGlobalData](#onrenderglobaldata) est appelée à demander les données.

Utilisez cette fonction si vous n’allez `CFile` pas fournir vos données à travers un objet. Si vous devez fournir les `CFile` données via un objet, appelez la fonction membre [DelayRenderFileData.](#delayrenderfiledata) Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour utiliser le rendu immédiat, appelez la fonction membre [CacheData](#cachedata) ou [CacheGlobalData.](#cacheglobaldata)

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData

Appelez cette fonction pour spécifier un format dans lequel les données sont offertes lors des opérations de transfert de données.

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format Clipboard dans lequel les données doivent être offertes. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être offertes. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les `FORMATETC` valeurs par défaut sont utilisées pour les autres champs de la structure.

### <a name="remarks"></a>Notes

Cette fonction fournit les données à l’aide de rendu retardé, de sorte que les données ne sont pas fournies immédiatement. La fonction membre [OnRenderFileData](#onrenderfiledata) est appelée à demander les données.

Utilisez cette fonction si vous `CFile` allez utiliser un objet pour fournir les données. Si vous n’utilisez `CFile` pas d’objet, appelez la fonction membre [DelayRenderData.](#delayrenderdata) Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour utiliser le rendu immédiat, appelez la fonction membre [CacheData](#cachedata) ou [CacheGlobalData.](#cacheglobaldata)

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleDataSource::DelaySetData

Appelez cette fonction pour soutenir la modification du contenu de la source de données.

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format Clipboard dans lequel les données doivent être placées. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être remplacées. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les `FORMATETC` valeurs par défaut sont utilisées pour les autres champs de la structure.

### <a name="remarks"></a>Notes

[OnSetData](#onsetdata) sera appelé par le cadre lorsque cela se produira. Ceci n’est utilisé que lorsque le cadre renvoie la source de données de [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Si `DelaySetData` ce n’est pas appelé, votre `OnSetData` fonction ne sera jamais appelée. `DelaySetData`devrait être appelé pour `FORMATETC` chaque Clipboard ou format que vous soutenez.

Pour plus d’informations, consultez la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleDataSource::DoDragDrop

Appelez `DoDragDrop` la fonction membre pour effectuer une opération de drag-and-drop pour cette source de données, généralement dans un [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) gestionnaire.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Paramètres

*dwEffects dwEffects*<br/>
Opérations de drag-and-drop qui sont autorisées sur cette source de données. Peut être un ou plusieurs des éléments suivants :

- DROPEFFECT_COPY Une opération de copie pourrait être effectuée.

- DROPEFFECT_MOVE Une opération de déménagement pourrait être effectuée.

- DROPEFFECT_LINK Un lien entre les données supprimées et les données originales pourrait être établi.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll pourrait se produire.

*lpRectStartDrag*<br/>
Pointeur vers le rectangle qui définit où la traînée commence réellement. Pour plus d'informations, consultez la section Notes qui suit.

*pDropSource (en)*<br/>
Points à une source de goutte. Si NULL, une implémentation par défaut de [COleDropSource](../../mfc/reference/coledropsource-class.md) sera utilisée.

### <a name="return-value"></a>Valeur de retour

Effet de chute généré par l’opération de drag-and-drop; sinon DROPEFFECT_NONE si l’opération ne commence jamais parce que l’utilisateur a libéré le bouton de la souris avant de quitter le rectangle fourni.

### <a name="remarks"></a>Notes

L’opération de drag-and-drop ne démarre pas immédiatement. Il attend que le curseur de souris quitte le rectangle spécifié par *lpRectStartDrag* ou jusqu’à ce qu’un nombre spécifié de millisecondes soient passés. Si *lpRectStartDrag* est NULL, la taille du rectangle est d’un pixel.

Le délai est spécifié par un paramètre de clé de registre. Vous pouvez modifier le délai en appelant [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) ou [CWinApp:WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Si vous ne spécifiez pas le délai, une valeur par défaut de 200 millisecondes est utilisée. Le temps de retard de traînée est stocké comme suit :

- Windows NT Drag delay time est stocké dans HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-NT-CurrentVersion-IniFileMapping.win.ini-Windows-DragDelay.

- Windows 3.x Le délai de drag est stocké dans le WIN. Fichier INI, sous la section [Windows».

- Windows 95/98 Le délai de drag est stocké dans une version mise en cache de WIN. Ini.

Pour plus d’informations sur la façon dont les informations sur les retards de traînée sont stockées dans le registre ou le . Fichier INI, voir [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) in the Windows SDK.

Pour plus d’informations, voir l’article [OLE glisser et déposer](../../mfc/drag-and-drop-ole.md).

## <a name="coledatasourceempty"></a><a name="empty"></a>COleDataSource::Vide

Appelez cette fonction `COleDataSource` pour vider l’objet des données.

```cpp
void Empty();
```

### <a name="remarks"></a>Notes

Les formats de rendu de mise en cache et de retard sont vidés afin qu’ils puissent être réutilisés.

Pour plus d’informations, voir [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) dans windows SDK.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleDataSource::FlushClipboard

Rend les données qui se trouve sur le Clipboard, puis vous permet de coller les données du Clipboard après la fermeture de votre application.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Notes

Utilisez [SetClipboard](#setclipboard) pour mettre des données sur le Clipboard.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner

Détermine si les données du Clipboard ont changé depuis que [SetClipboard](#setclipboard) a été appelée pour la dernière fois et, dans l’affirmative, identifie le propriétaire actuel.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Valeur de retour

La source de données actuellement sur le Clipboard, ou NULL s’il n’y a rien sur le Clipboard ou si le Clipboard n’est pas la propriété de l’application d’appel.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleDataSource::OnRenderData

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

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet à l’aide de la fonction membre [DelayRenderData](#delayrenderdata) ou [DelayRenderFileData](#delayrenderfiledata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction fera appel [à OnRenderFileData](#onrenderfiledata) ou [OnRenderGlobalData](#onrenderglobaldata) si le support de stockage fourni est soit un fichier ou une mémoire, respectivement. Si aucun de ces formats n’est fourni, alors la mise en œuvre par défaut retournera 0 et ne fera rien. Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Si *lpStgMedium*-> *tymed* est TYMED_NULL, `STGMEDIUM` le doit être alloué et rempli comme spécifié par *lpFormatEtc->tymed*. S’il n’est pas `STGMEDIUM` TYMED_NULL, il faut remplir les données.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous pouvez remplacer l’une des autres versions de cette fonction à la place. Si vos données sont petites et `OnRenderGlobalData`fixes en taille, remplacez . Si vos données sont dans un fichier, ou `OnRenderFileData`sont de taille variable, remplacez .

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) et [FORMATETC,](/windows/win32/api/objidl/ns-objidl-formatetc) le type d’énumération [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) et [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData

Appelé par le cadre pour récupérer les données dans le format spécifié lorsque le support de stockage spécifié est un fichier.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) précisant le format dans lequel l’information est demandée.

*pFile (en)*<br/>
Indique un objet [CFile](../../mfc/reference/cfile-class.md) dans lequel les données doivent être rendues.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet en utilisant la fonction membre [DelayRenderData](#delayrenderdata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction renvoie simplement FALSE.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous voudrez peut-être passer outre l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données sont dans un fichier, ou `OnRenderFileData`sont de taille variable, remplacez . Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, voir la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData

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
Indique une poignée à la mémoire globale dans laquelle les données doivent être retournées. Si l’on n’a pas encore été attribué, ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le format spécifié est un `COleDataSource` format précédemment placé dans l’objet en utilisant la fonction membre [DelayRenderData](#delayrenderdata) pour le rendu retardé. La mise en œuvre par défaut de cette fonction renvoie simplement FALSE.

Si *phGlobal* est NULL, alors un nouveau HGLOBAL devrait être attribué et retourné en *phGlobal*. Dans le cas contraire, le HGLOBAL spécifié par *phGlobal* doit être rempli avec les données. La quantité de données placées dans le HGLOBAL ne doit pas dépasser la taille actuelle du bloc de mémoire. En outre, le bloc ne peut pas être réaffecté à une plus grande taille.

C’est un avancé primordial. Remplacez cette fonction pour fournir vos données dans le format et le support demandés. Selon vos données, vous pouvez remplacer l’une des autres versions de cette fonction à la place. Si vous souhaitez gérer plusieurs supports de stockage, remplacez [OnRenderData](#onrenderdata). Si vos données sont dans un fichier, ou sont de taille variable, remplacez [OnRenderFileData](#onrenderfiledata). Pour plus d’informations sur le rendu retardé tel que géré par MFC, voir l’article [Data Objects and Data Sources: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Pour plus d’informations, voir la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleDataSource::OnSetData

Appelé par le cadre pour définir `COleDataSource` ou remplacer les données dans l’objet dans le format spécifié.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) spécifiant le format dans lequel les données sont remplacées.

*lpStgMedium*<br/>
Indique la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) contenant les données qui `COleDataSource` remplaceront le contenu actuel de l’objet.

*bRelease (en)*<br/>
Indique qui a la propriété du support de stockage après avoir rempli l’appel de fonction. L’appelant décide qui est responsable de la libération des ressources allouées au nom du support de stockage. L’appelant le fait en définissant *bRelease*. Si *bRelease* n’est pas zéro, la source de données s’en charge, libérant le support lorsqu’il a fini de l’utiliser. Lorsque *bRelease* est 0, l’appelant conserve la propriété et la source de données ne peut utiliser le support de stockage que pour la durée de l’appel.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La source de données ne s’approprie pas les données tant qu’elle n’a pas réussi à les obtenir. Autrement dit, il ne `OnSetData` prend pas possession si les déclarations 0. Si la source de données s’en charge, elle libère le support de stockage en appelant la fonction [ReleaseStgMedium.](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

L'implémentation par défaut n'exécute aucune opération. Remplacer cette fonction pour remplacer les données dans le format spécifié. C’est un avancé primordial.

Pour plus d’informations, consultez les structures [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et le [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) et [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) fonctions dans le SDK Windows.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleDataSource::SetClipboard

Met les données `COleDataSource` contenues dans l’objet sur le Clipboard après avoir appelé l’une des fonctions suivantes: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), ou [DelayRenderFileData](#delayrenderfiledata).

```cpp
void SetClipboard();
```

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject, classe](../../mfc/reference/coledataobject-class.md)
