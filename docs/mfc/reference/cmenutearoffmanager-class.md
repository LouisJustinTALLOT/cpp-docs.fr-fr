---
description: 'En savoir plus sur : classe CMenuTearOffManager'
title: CMenuTearOffManager, classe
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: b80f2e935f8d1dd47bf19a11522e4556b35490b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336646"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager, classe

Gère les menus détachables. Un menu détachable est un menu de la barre de menus. L'utilisateur peut supprimer un menu détachable de la barre de menus, provoquant ainsi son flottement.

   Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Construit un objet `CMenuTearOffManager`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMenuTearOffManager :: Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager :: Initialize](#initialize)|Initialise un objet `CMenuTearOffManager`.|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager ::P faible](#parse)||
|[CMenuTearOffManager :: Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Notes

Pour pouvoir utiliser des menus détachés dans votre application, vous devez disposer d’un `CMenuTearOffManager` objet. Dans la plupart des cas, vous ne créez ou n’initialisez pas `CMenuTearOffManager` directement un objet. Cela est géré pour vous lorsque vous appelez la fonction [CWinAppEx :: EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) .

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire et initialiser un `CMenuTearOffManager` objet en appelant la `CWinAppEX::EnableTearOffMenus` méthode. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmenutearoffmanager. h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a> CMenuTearOffManager :: Build

```cpp
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Paramètres

dans *uiTearOffBarID*<br/>

dans *strText*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a> CMenuTearOffManager::CMenuTearOffManager

Construit un objet [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) .

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous ne devez pas créer un `CMenuTearOffManager` manuellement. L’infrastructure de votre application crée l' `CMenuTearOffManager` objet quand vous appelez [CWinAppEx :: EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a> CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a> CMenuTearOffManager :: Initialize

Initialise un objet [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) .

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Paramètres

*lpszRegEntry*<br/>
dans Chaîne qui contient le chemin d’accès d’une entrée de registre. Vos applications stockent les paramètres des barres détachées dans cette entrée de registre.

*uiTearOffMenuFirst*<br/>
dans Premier ID de menu pour un menu détachable.

*uiTearOffMenuLast*<br/>
dans Dernier ID de menu d’un menu détachable.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La plage d’ID de menu de *uiTearOffMenuFirst* à *uiTearOffMenuLast* doit être un intervalle continu. L’intervalle définit le nombre de menus détachables qui peuvent apparaître en même temps dans l’application.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a> CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Paramètres

dans *uiID*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a> CMenuTearOffManager ::P faible

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Paramètres

dans *chaîne*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a> CMenuTearOffManager :: Reset

```cpp
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Paramètres

dans *HMENU*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a> CMenuTearOffManager::SetInUse

```cpp
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *uiCmdId*<br/>

dans *bUse*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a> CMenuTearOffManager::SetupTearOffMenus

```cpp
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

dans *HMENU*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
