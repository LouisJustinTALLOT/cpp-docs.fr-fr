---
title: IAtlMemMgr, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b772a548054cd9d829356436afe53748c215c193
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078918"
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
|[allouer](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[Gratuit](#free)|Appelez cette méthode pour libérer un bloc de mémoire.|
|[GetSize](#getsize)|Appelez cette méthode pour récupérer la taille d’un bloc de mémoire allouée.|
|[Réallouer](#reallocate)|Appelez cette méthode pour réallouer un bloc de mémoire.|

## <a name="remarks"></a>Notes

Cette interface est implémentée par [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), ou [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Fonctions du tas locales et globales sont plus lentes que les autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser le [fonctions de tas](/windows/desktop/Memory/heap-functions). Elles sont disponibles dans le [CWin32Heap](../../atl/reference/cwin32heap-class.md) classe.

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** atlmem.h

##  <a name="allocate"></a>  IAtlMemMgr::Allocate

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

Appelez [IAtlMemMgr::Free](#free) ou [IAtlMemMgr::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez le [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>  IAtlMemMgr::Free

Appelez cette méthode pour libérer un bloc de mémoire.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour libérer de la mémoire obtenue par [IAtlMemMgr::Allocate](#allocate) ou [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez le [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>  IAtlMemMgr::GetSize

Appelez cette méthode pour récupérer la taille d’un bloc de mémoire allouée.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille du bloc de mémoire en octets.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez le [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate

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

Appelez [IAtlMemMgr::Free](#free) ou [IAtlMemMgr::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Conceptuellement, cette méthode libère la mémoire existante et alloue un nouveau bloc de mémoire. En réalité, la mémoire existante peut être étendue ou réutilisée dans le cas contraire.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez le [vue d’ensemble de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

Le `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*pbAllowContextMenu*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

Le `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*pbAllowShowUI*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

Le `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*pbAllowWindowless*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Paramètres

*pclrBackground*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle déterminer si elle est le contrôle par défaut.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*pbDisplayAsDefault*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

Le `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostDoubleClickFlags*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

Le `DocHostFlags` propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostFlags*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

Le `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[out] L’adresse d’un `IFontDisp` pointeur d’interface utilisé pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise la police de l’interface graphique utilisateur par défaut ou la police système en tant que la valeur par défaut de cette propriété.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Paramètres

*pclrForeground*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise la couleur de texte de fenêtre système comme valeur par défaut de cette propriété.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

Le `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*plcidLocaleID*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise des paramètres régionaux par défaut de l’utilisateur en tant que la valeur par défaut de cette propriété.

Cette méthode vous pouvez de découvrir LocalID ambiante, autrement dit, LocaleID du programme de votre contrôle est utilisé dans. Une fois que vous connaissez LocaleID, vous pouvez appeler code pour charger les paramètres régionaux spécifiques, légendes, texte de message d’erreur, et ainsi de suite à partir d’un fichier de ressources ou la DLL satellite.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

Le `MessageReflect` propriété ambiante Spécifie si le conteneur reflètent les messages pour le contrôle hébergé.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Paramètres

*pbMessageReflect*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

Le `OptionKeyPath` propriété spécifie le chemin de clé de Registre aux paramètres utilisateur.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*pbstrOptionKeyPath*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

Le `ShowGrabHandles` propriété ambiante permet au contrôle déterminer si elle doit dessiner avec des poignées de manipulation.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*pbShowGrabHandles*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’ATL hôte objet implémentation retourne toujours VARIANT_FALSE comme valeur de cette propriété.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

Le `ShowHatching` propriété ambiante permet au contrôle déterminer si elle doit se dessiner lui-même hachée.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Paramètres

*pbShowHatching*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’ATL hôte objet implémentation retourne toujours VARIANT_FALSE comme valeur de cette propriété.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

Le `UserMode` propriété indique le mode utilisateur ambiante du conteneur.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Paramètres

*pbUserMode*<br/>
[out] L’adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

Le `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*bAllowContextMenu*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

Le `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*bAllowShowUI*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

Le `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*bAllowWindowless*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Paramètres

*clrBackground*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle déterminer si elle est le contrôle par défaut.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

Le `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostDoubleClickFlags*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

Le `DocHostFlags` propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostFlags*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

Le `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise la police de l’interface graphique utilisateur par défaut ou la police système en tant que la valeur par défaut de cette propriété.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Paramètres

*clrForeground*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise la couleur de texte de fenêtre système comme valeur par défaut de cette propriété.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

Le `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*lcidLocaleID*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise des paramètres régionaux par défaut de l’utilisateur en tant que la valeur par défaut de cette propriété.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

Le `MessageReflect` propriété ambiante Spécifie si le conteneur reflètent les messages pour le contrôle hébergé.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

Le `OptionKeyPath` propriété spécifie le chemin de clé de Registre aux paramètres utilisateur.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*bstrOptionKeyPath*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

Le `UserMode` propriété indique le mode utilisateur ambiante du conteneur.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
[in] La nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation d’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Cette méthode est appelée pour compléter l’interface de la propriété ambiante par défaut avec une interface définie par l’utilisateur.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatch*<br/>
Pointeur vers la nouvelle interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque `SetAmbientDispatch` est appelée avec un pointeur vers une nouvelle interface, cette nouvelle interface sera être utilisée pour appeler des propriétés ou les méthodes demandées par le contrôle hébergé, si ces propriétés ne sont pas déjà fournies par [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Attache un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl*<br/>
[in] Un pointeur vers le `IUnknown` interface du contrôle à joindre à l’objet hôte.

*hWnd*<br/>
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Crée un contrôle, il initialise et héberge ce dernier dans la fenêtre identifiée par *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*<br/>
[in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un HTML brut (précédé **MSHTML :**).

*hWnd*<br/>
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre est sous-classé par l’objet hôte exposer cette interface afin que les messages peuvent être reflétées au contrôle et d’autres fonctionnalités de conteneur fonctionneront.

Appel de cette méthode équivaut à appeler [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un HTML brut (avec le préfixe **MSHTML :**).

*hWnd*<br/>
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être NULL.

*ppUnk*<br/>
[out] L’adresse d’un pointeur qui reçoit le `IUnknown` interface du contrôle créé. Peut être NULL.

*riidAdvise*<br/>
[in] L’identificateur d’interface d’une interface sortante sur l’objet de relation contenant-contenu. Peut être IID_NULL.

*punkAdvise*<br/>
[in] Un pointeur vers le `IUnknown` interface de l’objet de récepteur à être connectés au point de connexion sur l’objet de relation contenant-contenu spécifié par `iidSink`.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement à la `CreateControl` (méthode), `CreateControlEx` vous permet également de recevoir un pointeur d’interface au contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
[in] L’ID d’une interface sur le contrôle demandé.

*ppvObject*<br/>
[out] L’adresse d’un pointeur qui reçoit l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Définit la dispinterface externe, qui est disponible pour les contrôles contenus par le biais du [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) (méthode).

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*argument pDisp*<br/>
[in] Un pointeur vers un `IDispatch` interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’externe [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interface pour le `CAxWindow` objet.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*argument pDisp*<br/>
[in] Un pointeur vers un `IDocHostUIHandlerDispatch` interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (par exemple, le contrôle de navigateur Web) qui interroge le site de l’hôte pour le `IDocHostUIHandlerDispatch` interface.

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, il initialise et héberge ce dernier dans la fenêtre identifiée par `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
[in] BSTR contenant la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Consultez [IAxWinHostWindow::CreateControl](#createcontrol) pour obtenir une description de la valeur de retour et de paramètres restants.

Appel de cette méthode équivaut à appeler [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Exemple

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] BSTR contenant la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Consultez [IAxWinHostWindow::CreateControlEx](#createcontrolex) pour obtenir une description de la valeur de retour et de paramètres restants.

### <a name="example"></a>Exemple

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
