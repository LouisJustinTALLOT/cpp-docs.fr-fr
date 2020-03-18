---
title: IAtlMemMgr, classe
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: a0d79ae95a0604ca75f03673873e99394a1bc295
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417655"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr, classe

Cette classe représente l’interface pour un gestionnaire de mémoire.

## <a name="syntax"></a>Syntaxe

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Lui](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[Gratuit](#free)|Appelez cette méthode pour libérer un bloc de mémoire.|
|[GetSize](#getsize)|Appelez cette méthode pour récupérer la taille d’un bloc de mémoire alloué.|
|[Réallouer](#reallocate)|Appelez cette méthode pour réallouer un bloc de mémoire.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)ou [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Les fonctions de tas local et global sont plus lentes que les autres fonctions de gestion de la mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser les [fonctions de tas](/windows/win32/Memory/heap-functions). Celles-ci sont disponibles dans la classe [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** atlmem. h

##  <a name="allocate"></a>IAtlMemMgr :: Allocate

Appelez cette méthode pour allouer un bloc de mémoire.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [IAtlMemMgr :: Free](#free) ou [IAtlMemMgr :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>IAtlMemMgr :: Free

Appelez cette méthode pour libérer un bloc de mémoire.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour libérer de la mémoire obtenue par [IAtlMemMgr :: Allocate](#allocate) ou [IAtlMemMgr :: Allocate](#reallocate).

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>IAtlMemMgr :: est à obtenir

Appelez cette méthode pour récupérer la taille d’un bloc de mémoire alloué.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille du bloc de mémoire en octets.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>IAtlMemMgr :: Reallocation

Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [IAtlMemMgr :: Free](#free) ou [IAtlMemMgr :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Conceptuellement, cette méthode libère la mémoire existante et alloue un nouveau bloc de mémoire. En réalité, la mémoire existante peut être étendue ou réutilisée.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch :: get_AllowContextMenu

La propriété `AllowContextMenu` spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*pbAllowContextMenu*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_allowshowui"></a>IAxWinAmbientDispatch :: get_AllowShowUI

La propriété `AllowShowUI` spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*pbAllowShowUI*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch :: get_AllowWindowlessActivation

La propriété `AllowWindowlessActivation` spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*pbAllowWindowless*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_backcolor"></a>IAxWinAmbientDispatch :: get_BackColor

La propriété `BackColor` spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Paramètres

*pclrBackground*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

##  <a name="get_displayasdefault"></a>IAxWinAmbientDispatch :: get_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*pbDisplayAsDefault*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch :: get_DocHostDoubleClickFlags

La propriété `DocHostDoubleClickFlags` spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostDoubleClickFlags*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

##  <a name="get_dochostflags"></a>IAxWinAmbientDispatch :: get_DocHostFlags

La propriété `DocHostFlags` spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostFlags*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

##  <a name="get_font"></a>IAxWinAmbientDispatch :: get_Font

La propriété `Font` spécifie la police ambiante du conteneur.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
à Adresse d’un pointeur d’interface `IFontDisp` utilisé pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police de l’interface utilisateur graphique par défaut ou la police système comme valeur par défaut de cette propriété.

##  <a name="get_forecolor"></a>IAxWinAmbientDispatch :: get_ForeColor

La propriété `ForeColor` spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Paramètres

*pclrForeground*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur de texte de la fenêtre système comme valeur par défaut de cette propriété.

##  <a name="get_localeid"></a>IAxWinAmbientDispatch :: get_LocaleID

La propriété `LocaleID` spécifie l’ID de paramètres régionaux ambiants du conteneur.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*plcidLocaleID*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise les paramètres régionaux par défaut de l’utilisateur comme valeur par défaut de cette propriété.

Avec cette méthode, vous pouvez découvrir le LocalID ambiant, c’est-à-dire le LocaleID du programme dans lequel votre contrôle est utilisé. Une fois que vous connaissez le LocaleID, vous pouvez appeler du code pour charger des sous-titres spécifiques aux paramètres régionaux, du texte du message d’erreur, etc. à partir d’un fichier de ressources ou d’une DLL satellite.

##  <a name="get_messagereflect"></a>IAxWinAmbientDispatch :: get_MessageReflect

La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Paramètres

*pbMessageReflect*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_optionkeypath"></a>IAxWinAmbientDispatch :: get_OptionKeyPath

La propriété `OptionKeyPath` spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*pbstrOptionKeyPath*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="get_showgrabhandles"></a>IAxWinAmbientDispatch :: get_ShowGrabHandles

La `ShowGrabHandles` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même avec des poignées de manipulation.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*pbShowGrabHandles*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL retourne toujours VARIANT_FALSE comme valeur de cette propriété.

##  <a name="get_showhatching"></a>IAxWinAmbientDispatch :: get_ShowHatching

La `ShowHatching` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Paramètres

*pbShowHatching*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL retourne toujours VARIANT_FALSE comme valeur de cette propriété.

##  <a name="get_usermode"></a>IAxWinAmbientDispatch :: get_UserMode

La propriété `UserMode` spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Paramètres

*pbUserMode*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch ::p ut_AllowContextMenu

La propriété `AllowContextMenu` spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*bAllowContextMenu*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_allowshowui"></a>IAxWinAmbientDispatch ::p ut_AllowShowUI

La propriété `AllowShowUI` spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*bAllowShowUI*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch ::p ut_AllowWindowlessActivation

La propriété `AllowWindowlessActivation` spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*bAllowWindowless*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_backcolor"></a>IAxWinAmbientDispatch ::p ut_BackColor

La propriété `BackColor` spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Paramètres

*clrBackground*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

##  <a name="put_displayasdefault"></a>IAxWinAmbientDispatch ::p ut_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch ::p ut_DocHostDoubleClickFlags

La propriété `DocHostDoubleClickFlags` spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostDoubleClickFlags*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

##  <a name="put_dochostflags"></a>IAxWinAmbientDispatch ::p ut_DocHostFlags

La propriété `DocHostFlags` spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostFlags*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

##  <a name="put_font"></a>IAxWinAmbientDispatch ::p ut_Font

La propriété `Font` spécifie la police ambiante du conteneur.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police de l’interface utilisateur graphique par défaut ou la police système comme valeur par défaut de cette propriété.

##  <a name="put_forecolor"></a>IAxWinAmbientDispatch ::p ut_ForeColor

La propriété `ForeColor` spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Paramètres

*clrForeground*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur de texte de la fenêtre système comme valeur par défaut de cette propriété.

##  <a name="put_localeid"></a>IAxWinAmbientDispatch ::p ut_LocaleID

La propriété `LocaleID` spécifie l’ID de paramètres régionaux ambiants du conteneur.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*lcidLocaleID*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise les paramètres régionaux par défaut de l’utilisateur comme valeur par défaut de cette propriété.

##  <a name="put_messagereflect"></a>IAxWinAmbientDispatch ::p ut_MessageReflect

La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_optionkeypath"></a>IAxWinAmbientDispatch ::p ut_OptionKeyPath

La propriété `OptionKeyPath` spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*bstrOptionKeyPath*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="put_usermode"></a>IAxWinAmbientDispatch ::p ut_UserMode

La propriété `UserMode` spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Cette méthode est appelée pour compléter l’interface de propriété ambiante par défaut par une interface définie par l’utilisateur.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatch*<br/>
Pointeur vers la nouvelle interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque `SetAmbientDispatch` est appelée avec un pointeur vers une nouvelle interface, cette nouvelle interface est utilisée pour appeler toutes les propriétés ou méthodes demandées par le contrôle hébergé, si ces propriétés ne sont pas déjà fournies par [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Joint un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl*<br/>
dans Pointeur vers l’interface `IUnknown` du contrôle à attacher à l’objet hôte.

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="createcontrol"></a>IAxWinHostWindow :: CreateControl

Crée un contrôle, l’initialise et l’héberge dans la fenêtre identifiée par *HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*<br/>
dans Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL ou HTML brut (préfixé par **MSHTML :** ).

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
dans Pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre sera sous-classée par l’objet hôte exposant cette interface afin que les messages puissent être reflétés dans le contrôle et que d’autres fonctionnalités de conteneur fonctionnent.

L’appel de cette méthode équivaut à appeler [IAxWinHostWindow :: CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic :: CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow :: CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*<br/>
dans Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL ou HTML brut (avec le préfixe **MSHTML :** ).

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
dans Pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

*ppUnk*<br/>
à Adresse d’un pointeur qui recevra l’interface `IUnknown` du contrôle créé. Sa valeur peut être NULL.

*riidAdvise*<br/>
dans Identificateur d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkAdvise*<br/>
dans Pointeur vers l’interface `IUnknown` de l’objet récepteur à connecter au point de connexion sur l’objet contenu spécifié par `iidSink`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement à la méthode `CreateControl`, `CreateControlEx` vous permet également de recevoir un pointeur d’interface vers le contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic :: CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
dans ID d’une interface sur le contrôle demandé.

*ppvObject*<br/>
à Adresse d’un pointeur qui recevra l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Définit la dispinterface externe, qui est disponible pour les contrôles contenus par le biais de la méthode [IDocHostUIHandlerDispatch :: GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
dans Pointeur vers une interface de `IDispatch`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’interface [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) externe pour l’objet `CAxWindow`.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
dans Pointeur vers une interface de `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (tels que le contrôle de navigateur Web) qui interrogent le site de l’hôte pour l’interface `IDocHostUIHandlerDispatch`.

##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, l’initialise et l’héberge dans la fenêtre identifiée par `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
dans BSTR qui contient la clé de licence du contrôle.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [IAxWinHostWindow :: CreateControl](#createcontrol) .

L’appel de cette méthode équivaut à appeler [IAxWinHostWindowLic :: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow :: CreateControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
dans BSTR qui contient la clé de licence du contrôle.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [IAxWinHostWindow :: CreateControlEx](#createcontrolex) .

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
