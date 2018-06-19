---
title: Classe de CMenuTearOffManager | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dcbd5ea33b50e66d1c9e858669a3174042a19e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367667"
---
# <a name="cmenutearoffmanager-class"></a>Classe de CMenuTearOffManager
Gère les menus détachables. Un menu détachable est un menu de la barre de menus. L'utilisateur peut supprimer un menu détachable de la barre de menus, provoquant ainsi son flottement.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
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
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|Initialise un `CMenuTearOffManager` objet.|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>Notes  
 Pour utiliser les menus détachables dans votre application, vous devez disposer un `CMenuTearOffManager` objet. Dans la plupart des cas, vous ne créez ou initialisez une `CMenuTearOffManager` directement l’objet. Cela s’effectue lorsque vous appelez le [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) (fonction).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer et initialiser un `CMenuTearOffManager` objet en appelant le `CWinAppEX::EnableTearOffMenus` (méthode). Cet extrait de code fait partie de l’ [exemple Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxmenutearoffmanager.h  
  
##  <a name="build"></a>  CMenuTearOffManager::Build  

  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiTearOffBarID`  
 [in] `strText`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager  
 Construit un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objet.  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>Notes  
 Dans la plupart des cas, vous ne devez créer un `CMenuTearOffManager` manuellement. L’infrastructure de votre application crée le `CMenuTearOffManager` lorsque vous appelez l’objet [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).  
  
##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath  

  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="initialize"></a>  CMenuTearOffManager::Initialize  
 Initialise un [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objet.  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszRegEntry`  
 Chaîne qui contient le chemin d’accès d’une entrée de Registre. Vos applications stocke les paramètres pour les barres de détachable dans cette entrée de Registre.  
  
 [in] `uiTearOffMenuFirst`  
 Le premier ID de menu pour un menu détachable.  
  
 [in] `uiTearOffMenuLast`  
 Le dernier ID de menu pour un menu détachable.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La plage d’ID de menu à partir de `uiTearOffMenuFirst` à `uiTearOffMenuLast` doit être un intervalle continu. L’intervalle définit le nombre de menus détachables qui peuvent s’afficher en même temps dans l’application.  
  
##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID  

  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiID`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="parse"></a>  CMenuTearOffManager::Parse  

  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `str`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="reset"></a>  CMenuTearOffManager::Reset  

  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hmenu`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse  

  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmdId`  
 [in] `bUse`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus  

  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hMenu`  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
