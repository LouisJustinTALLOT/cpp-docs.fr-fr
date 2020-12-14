---
description: 'En savoir plus sur : classe CRecentDockSiteInfo'
title: CRecentDockSiteInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::CleanUp
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDefaultPaneDivider
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedPercent
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedRect
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentListOfPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentPaneContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentTabContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::Init
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::IsRecentLeftPane
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SaveListOfRecentPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SetInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::StoreDockInfo
helpviewer_keywords:
- CRecentDockSiteInfo [MFC], CleanUp
- CRecentDockSiteInfo [MFC], GetRecentDefaultPaneDivider
- CRecentDockSiteInfo [MFC], GetRecentDockedPercent
- CRecentDockSiteInfo [MFC], GetRecentDockedRect
- CRecentDockSiteInfo [MFC], GetRecentListOfPanes
- CRecentDockSiteInfo [MFC], GetRecentPaneContainer
- CRecentDockSiteInfo [MFC], GetRecentTabContainer
- CRecentDockSiteInfo [MFC], Init
- CRecentDockSiteInfo [MFC], IsRecentLeftPane
- CRecentDockSiteInfo [MFC], SaveListOfRecentPanes
- CRecentDockSiteInfo [MFC], SetInfo
- CRecentDockSiteInfo [MFC], StoreDockInfo
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
ms.openlocfilehash: e33ef48be2b091477200f15a31c194d845693399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343095"
---
# <a name="crecentdocksiteinfo-class"></a>CRecentDockSiteInfo, classe

La `CRecentDockSiteInfo` classe est une classe d’assistance qui stocke des informations d’État récentes pour la [classe CPane](../../mfc/reference/cpane-class.md).

## <a name="syntax"></a>Syntaxe

```
class CRecentDockSiteInfo : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRecentDockSiteInfo::CleanUp](#cleanup)||
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](#getrecentdefaultpanedivider)||
|[CRecentDockSiteInfo::GetRecentDockedPercent](#getrecentdockedpercent)||
|[CRecentDockSiteInfo::GetRecentDockedRect](#getrecentdockedrect)||
|[CRecentDockSiteInfo::GetRecentListOfPanes](#getrecentlistofpanes)||
|[CRecentDockSiteInfo::GetRecentPaneContainer](#getrecentpanecontainer)||
|[CRecentDockSiteInfo::GetRecentTabContainer](#getrecenttabcontainer)||
|[CRecentDockSiteInfo::Init](#init)||
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||
|[CRecentDockSiteInfo :: Operator =](#operator_eq)||
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||
|[CRecentDockSiteInfo::SetInfo](#setinfo)||
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||

## <a name="remarks"></a>Notes

`CRecentDockSiteInfo` est une classe de gestion de données. Elle suit le dernier état d'un `CPane` au fil de ses transitions entre les états ancré et flottant. Quand un utilisateur double-clique sur un volet ancrable flottant, il devient ancré. Un double-clic sur le volet ancré rétablit ses emplacement, taille et état précédents. De même, quand le volet est à nouveau ancré, il retrouve son emplacement d'ancrage précédent. Telles sont les possibilités offertes par cette classe de données. Comme les membres de cette classe stockent les informations d'état du volet ancré, ils ne doivent pas être directement modifiés par votre application.

Un objet `CRecentDockSiteInfo` est créé à chaque création d'un volet. Chaque `CPane` objet possède une variable membre, [CPane :: m_recentDockInfo](../../mfc/reference/cpane-class.md#m_recentdockinfo), pour stocker ces informations.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrecentDockSiteInfo. h

## <a name="crecentdocksiteinfocleanup"></a><a name="cleanup"></a> CRecentDockSiteInfo :: CleanUp

```cpp
void CleanUp();
```

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfocrecentdocksiteinfo"></a><a name="crecentdocksiteinfo"></a> CRecentDockSiteInfo::CRecentDockSiteInfo

```
CRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Paramètres

dans *pBar*<br/>

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecentdefaultpanedivider"></a><a name="getrecentdefaultpanedivider"></a> CRecentDockSiteInfo::GetRecentDefaultPaneDivider

```
CPaneDivider* GetRecentDefaultPaneDivider();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecentdockedpercent"></a><a name="getrecentdockedpercent"></a> CRecentDockSiteInfo::GetRecentDockedPercent

```
int GetRecentDockedPercent(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecentdockedrect"></a><a name="getrecentdockedrect"></a> CRecentDockSiteInfo::GetRecentDockedRect

```
CRect& GetRecentDockedRect(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecentlistofpanes"></a><a name="getrecentlistofpanes"></a> CRecentDockSiteInfo::GetRecentListOfPanes

```
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecentpanecontainer"></a><a name="getrecentpanecontainer"></a> CRecentDockSiteInfo::GetRecentPaneContainer

```
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfogetrecenttabcontainer"></a><a name="getrecenttabcontainer"></a> CRecentDockSiteInfo::GetRecentTabContainer

```
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfoinit"></a><a name="init"></a> CRecentDockSiteInfo :: init

```cpp
void Init();
```

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfoisrecentleftpane"></a><a name="isrecentleftpane"></a> CRecentDockSiteInfo::IsRecentLeftPane

```
BOOL IsRecentLeftPane(BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfooperator-"></a><a name="operator_eq"></a> CRecentDockSiteInfo :: Operator =

```
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```

### <a name="parameters"></a>Paramètres

dans *src*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfosavelistofrecentpanes"></a><a name="savelistofrecentpanes"></a> CRecentDockSiteInfo::SaveListOfRecentPanes

```cpp
void SaveListOfRecentPanes(CList<HWND,
    HWND>& lstOrg,
    BOOL bForSlider);
```

### <a name="parameters"></a>Paramètres

dans *CList<HWND*<br/>
dans *lstOrg*<br/>
dans *bForSlider*<br/>

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfosetinfo"></a><a name="setinfo"></a> CRecentDockSiteInfo :: SetInfo

```
virtual void SetInfo(
    BOOL bForSlider,
    CRecentDockSiteInfo& srcInfo);
```

### <a name="parameters"></a>Paramètres

dans *bForSlider*<br/>
dans *srcInfo*<br/>

### <a name="remarks"></a>Notes

## <a name="crecentdocksiteinfostoredockinfo"></a><a name="storedockinfo"></a> CRecentDockSiteInfo::StoreDockInfo

```
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,
    CDockablePane* pTabbedBar = NULL);
```

### <a name="parameters"></a>Paramètres

dans *pRecentContainer*<br/>
dans *pTabbedBar*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite, classe](../../mfc/reference/cdocksite-class.md)
