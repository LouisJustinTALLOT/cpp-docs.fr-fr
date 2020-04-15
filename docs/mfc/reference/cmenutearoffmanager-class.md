---
title: Classe CMenuTearOffManager
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
ms.openlocfilehash: f41937179dc055213f3af093e107bcb08c8a8fcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369960"
---
# <a name="cmenutearoffmanager-class"></a>Classe CMenuTearOffManager

Gère les menus détachables. Un menu détachable est un menu de la barre de menus. L'utilisateur peut supprimer un menu détachable de la barre de menus, provoquant ainsi son flottement.

   Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

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
|[CMenuTearOffManager::Construire](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialize](#initialize)|Initialise un objet `CMenuTearOffManager`.|
|[CMenuTearOffManager::IsDynamicICID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Notes

Afin d’utiliser des menus déchirants dans votre `CMenuTearOffManager` application, vous devez avoir un objet. Dans la plupart des cas, vous `CMenuTearOffManager` ne créerez pas ou n’initialisez pas directement un objet. Ceci est géré pour vous lorsque vous appelez la fonction [CWinAppEx::EnableTearOffMenus.](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMenuTearOffManager` et initialiser `CWinAppEX::EnableTearOffMenus` un objet en appelant la méthode. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmenutearoffmanager.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearOffManager::Construire

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Paramètres

[dans] *uiTearOffBarID*<br/>

[dans] *strText (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager

Construit un objet [CMenuTearOffManager.](../../mfc/reference/cmenutearoffmanager-class.md)

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous ne devez pas créer un `CMenuTearOffManager` manuellement. Le cadre de votre `CMenuTearOffManager` application crée l’objet lorsque vous appelez [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Initialize

Initialise un objet [CMenuTearOffManager.](../../mfc/reference/cmenutearoffmanager-class.md)

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Paramètres

*lpszRegEntry (en)*<br/>
[dans] Une chaîne qui contient le chemin d’une entrée de registre. Vos applications stockent les paramètres des barres de déchirure dans cette entrée de registre.

*uiTearOffMenuFirst*<br/>
[dans] Le premier menu ID pour un menu déchirant.

*uiTearOffMenuLast*<br/>
[dans] Le dernier menu ID pour un menu déchirant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La gamme d’articles d’ID de menu *d’uiTearOffMenuFirst* à *uiTearOffMenuLast* doit être un intervalle continu. L’intervalle définit le nombre de menus déchirants qui peuvent apparaître en même temps dans l’application.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicICID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Paramètres

[dans] *uiID*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Paramètres

[dans] *str*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Paramètres

[dans] *hmenu hmenu*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *uiCmdId*<br/>

[dans] *bUse*<br/>

### <a name="remarks"></a>Notes

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

[dans] *hMenu*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
