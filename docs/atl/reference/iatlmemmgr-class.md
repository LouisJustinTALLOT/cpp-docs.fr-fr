---
title: Classe IAtlMemMgr
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
ms.openlocfilehash: c296c9de79c305d0f7d2f135f250d181d3cd667a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330058"
---
# <a name="iatlmemmgr-class"></a>Classe IAtlMemMgr

Cette classe représente l’interface d’un gestionnaire de mémoire.

## <a name="syntax"></a>Syntaxe

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Allouer](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[Gratuit](#free)|Appelez cette méthode pour libérer un bloc de mémoire.|
|[GetSize](#getsize)|Appelez cette méthode pour récupérer la taille d’un bloc mémoire alloué.|
|[Réaffecter](#reallocate)|Appelez cette méthode pour réaffecter un bloc de mémoire.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), ou [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
> Les fonctions locales et globales de tas sont plus lentes que d’autres fonctions de gestion de mémoire, et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications devraient utiliser les [fonctions de tas](/windows/win32/Memory/heap-functions). Ceux-ci sont disponibles dans la classe [CWin32Heap.](../../atl/reference/cwin32heap-class.md)

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr::Allocate

Appelez cette méthode pour allouer un bloc de mémoire.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [IAtlMemMgr::Free](#free) ou [IAtlMemMgr::Réallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

### <a name="example"></a>Exemple

Par exemple, voir [l’aperçu de l’IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Gratuit

Appelez cette méthode pour libérer un bloc de mémoire.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour libérer la mémoire obtenue par [IAtlMemMgr::Allocate](#allocate) ou [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Exemple

Par exemple, voir [l’aperçu de l’IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr::GetSize

Appelez cette méthode pour récupérer la taille d’un bloc mémoire alloué.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille du bloc de mémoire dans les octets.

### <a name="example"></a>Exemple

Par exemple, voir [l’aperçu de l’IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Réallocate

Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nBytes (en)*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [IAtlMemMgr::Free](#free) ou [IAtlMemMgr::Réallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Conceptuellement, cette méthode libère la mémoire existante et alloue un nouveau bloc de mémoire. En réalité, la mémoire existante peut être étendue ou réutilisée.

### <a name="example"></a>Exemple

Par exemple, voir [l’aperçu de l’IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu

La `AllowContextMenu` propriété précise si le contrôle hébergé est autorisé à afficher son propre menu contextuelle.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*pbAllowContextMenu*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

La `AllowShowUI` propriété précise si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*pbAllowShowUI*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

La `AllowWindowlessActivation` propriété précise si le conteneur permettra l’activation sans fenêtre.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*pbAllowWindowless*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

La `BackColor` propriété spécifie la couleur de fond ambiant du récipient.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Paramètres

*pclrBackground (en anglais)*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est un dialogue ou non).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`est une propriété ambiante qui permet à un contrôle de savoir si c’est le contrôle par défaut.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*pbDisplayAsDefault*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propriété spécifie l’opération qui devrait avoir lieu en réponse à un double clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostDoubleClickFlags*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

La `DocHostFlags` propriété spécifie les capacités d’interface utilisateur de l’objet hôte.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostFlags pdwDocHostFlags*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font

La `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[out] L’adresse `IFontDisp` d’un pointeur d’interface utilisé pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police GUI par défaut ou la police du système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

La `ForeColor` propriété spécifie la couleur ambiante au premier plan du récipient.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Paramètres

*pclrForeground*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur du texte de fenêtre du système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

La `LocaleID` propriété spécifie l’ID local ambiant du conteneur.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*plcidLocaleID*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise le lieu par défaut de l’utilisateur comme valeur par défaut de cette propriété.

Avec cette méthode, vous pouvez découvrir l’Ambient LocalID, c’est-à-dire, le LocalID du programme dans lequel votre contrôle est utilisé. Une fois que vous connaissez le LocalID, vous pouvez appeler le code pour charger des légendes locales spécifiques, texte de message d’erreur, et ainsi de suite à partir d’un fichier de ressources ou DLL satellite.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

La `MessageReflect` propriété ambiante précise si le conteneur reflétera les messages au contrôle hébergé.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Paramètres

*pbMessageReflect*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

La `OptionKeyPath` propriété spécifie le chemin clé du registre vers les paramètres de l’utilisateur.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*pbstrOptionKeyPath (en)*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

La `ShowGrabHandles` propriété ambiante permet au contrôle de savoir si elle doit se dessiner avec des poignées de prise.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*pbShowGrabHandles*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objets hôtes ATL revient toujours VARIANT_FALSE comme la valeur de cette propriété.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

La `ShowHatching` propriété ambiante permet au contrôle de savoir si elle doit dessiner elle-même éclos.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Paramètres

*pbShowHatching pbShowHatching*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objets hôtes ATL revient toujours VARIANT_FALSE comme la valeur de cette propriété.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Paramètres

*pbUserMode*<br/>
[out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put-AllowContextMenu

La `AllowContextMenu` propriété précise si le contrôle hébergé est autorisé à afficher son propre menu contextuelle.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*bAllowContextMenu*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put-AllowShowUI

La `AllowShowUI` propriété précise si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*bAllowShowUI (en)*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put-AllowWindowlessActivation

La `AllowWindowlessActivation` propriété précise si le conteneur permettra l’activation sans fenêtre.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*bAllowWindowless*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put-BackColor

La `BackColor` propriété spécifie la couleur de fond ambiant du récipient.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Paramètres

*clrBackground*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est un dialogue ou non).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put-DisplayAsDefault

`DisplayAsDefault`est une propriété ambiante qui permet à un contrôle de savoir si c’est le contrôle par défaut.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put-DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propriété spécifie l’opération qui devrait avoir lieu en réponse à un double clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostDoubleClickFlags*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put-DocHostFlags

La `DocHostFlags` propriété spécifie les capacités d’interface utilisateur de l’objet hôte.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostFlags*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWinAmbientDispatch::put-Font

La `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police GUI par défaut ou la police du système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put-ForeColor

La `ForeColor` propriété spécifie la couleur ambiante au premier plan du récipient.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Paramètres

*clrForeground*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur du texte de fenêtre du système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put-LocaleID

La `LocaleID` propriété spécifie l’ID local ambiant du conteneur.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*lcidLocaleID*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise le lieu par défaut de l’utilisateur comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put-MessageReflect

La `MessageReflect` propriété ambiante précise si le conteneur reflétera les messages au contrôle hébergé.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put-OptionKeyPath

La `OptionKeyPath` propriété spécifie le chemin clé du registre vers les paramètres de l’utilisateur.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*bstrOptionKeyPath (en)*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put-UserMode

La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
[dans] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La mise en œuvre de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Cette méthode est appelée pour compléter l’interface de propriété ambiante par défaut avec une interface définie par l’utilisateur.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatch*<br/>
Pointeur vers la nouvelle interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Lorsqu’elle `SetAmbientDispatch` est appelée avec un pointeur vers une nouvelle interface, cette nouvelle interface sera utilisée pour invoquer toutes les propriétés ou méthodes demandées par le contrôle hébergé - si ces propriétés ne sont pas déjà fournies par [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Attache un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl (en)*<br/>
[dans] Un pointeur `IUnknown` à l’interface du contrôle à attacher à l’objet hôte.

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Crée un contrôle, l’initialise, et l’héberge dans la fenêtre identifiée par *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData (en)*<br/>
[dans] Une chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL, ou HTML brut (préfixé par **MSHTML:**).

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[dans] Un pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre sera sous-classée par l’objet hôte exposant cette interface afin que les messages puissent être réfléchis au contrôle et que d’autres fonctionnalités de conteneur fonctionneront.

Appeler cette méthode équivaut à appeler [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, voir [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, l’initialise, et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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

*lpTricsData (en)*<br/>
[dans] Une chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL, ou HTML brut (préfixé avec **MSHTML:**).

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[dans] Un pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

*ppUnk*<br/>
[out] L’adresse d’un pointeur qui recevra l’interface `IUnknown` du contrôle créé. Sa valeur peut être NULL.

*riidAdvise*<br/>
[dans] L’identifiant d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkAdvise (en)*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet de l’évier `iidSink`à connecter au point de connexion sur l’objet contenu spécifié par .

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement `CreateControl` à `CreateControlEx` la méthode, vous permet également de recevoir un pointeur d’interface pour le contrôle nouvellement créé et mettre en place un évier d’événement pour recevoir des événements tirés par le contrôle.

Pour créer un contrôle ActiveX sous licence, voir [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
[dans] L’ID d’une interface sur le contrôle demandé.

*ppvObject*<br/>
[out] L’adresse d’un pointeur qui recevra l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Définit le dispinterface externe, qui est disponible pour les contrôles contenus par le [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) méthode.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
[dans] Un pointeur `IDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’interface externe [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pour l’objet. `CAxWindow`

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
[dans] Un pointeur `IDocHostUIHandlerDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (tels que le contrôle du `IDocHostUIHandlerDispatch` navigateur Web) qui interrogent le site de l’hôte pour l’interface.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, l’initialise, et `hWnd`l’héberge dans la fenêtre identifiée par .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic bstrLic*<br/>
[dans] Le BSTR qui contient la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Voir [IAxWinHostWindow::CreateControl](#createcontrol) pour une description des paramètres restants et la valeur de retour.

Appeler cette méthode équivaut à appeler [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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

*bstrLic bstrLic*<br/>
[dans] Le BSTR qui contient la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Voir [IAxWinHostWindow::CreateControlEx](#createcontrolex) pour une description des paramètres restants et de la valeur de retour.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
