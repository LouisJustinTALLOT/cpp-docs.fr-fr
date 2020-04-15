---
title: IAxWinAmbientDispatch Interface
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330007"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch Interface

Cette interface fournit des méthodes pour spécifier les caractéristiques du contrôle ou du conteneur hébergé.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|La `AllowContextMenu` propriété précise si le contrôle hébergé est autorisé à afficher son propre menu contextuelle.|
|[get_AllowShowUI](#get_allowshowui)|La `AllowShowUI` propriété précise si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|La `AllowWindowlessActivation` propriété précise si le conteneur permettra l’activation sans fenêtre.|
|[get_BackColor](#get_backcolor)|La `BackColor` propriété spécifie la couleur de fond ambiant du récipient.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`est une propriété ambiante qui permet à un contrôle de savoir si c’est le contrôle par défaut.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propriété spécifie l’opération qui devrait avoir lieu en réponse à un double clic.|
|[get_DocHostFlags](#get_dochostflags)|La `DocHostFlags` propriété spécifie les capacités d’interface utilisateur de l’objet hôte.|
|[get_Font](#get_font)|La `Font` propriété spécifie la police ambiante du conteneur.|
|[get_ForeColor](#get_forecolor)|La `ForeColor` propriété spécifie la couleur ambiante au premier plan du récipient.|
|[get_LocaleID](#get_localeid)|La `LocaleID` propriété spécifie l’ID local ambiant du conteneur.|
|[get_MessageReflect](#get_messagereflect)|La `MessageReflect` propriété ambiante précise si le conteneur reflétera les messages au contrôle hébergé.|
|[get_OptionKeyPath](#get_optionkeypath)|La `OptionKeyPath` propriété spécifie le chemin clé du registre vers les paramètres de l’utilisateur.|
|[get_ShowGrabHandles](#get_showgrabhandles)|La `ShowGrabHandles` propriété ambiante permet au contrôle de savoir si elle doit se dessiner avec des poignées de prise.|
|[get_ShowHatching](#get_showhatching)|La `ShowHatching` propriété ambiante permet au contrôle de savoir si elle doit dessiner elle-même éclos.|
|[get_UserMode](#get_usermode)|La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.|
|[put_AllowContextMenu](#put_allowcontextmenu)|La `AllowContextMenu` propriété précise si le contrôle hébergé est autorisé à afficher son propre menu contextuelle.|
|[put_AllowShowUI](#put_allowshowui)|La `AllowShowUI` propriété précise si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|La `AllowWindowlessActivation` propriété précise si le conteneur permettra l’activation sans fenêtre.|
|[put_BackColor](#put_backcolor)|La `BackColor` propriété spécifie la couleur de fond ambiant du récipient.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`est une propriété ambiante qui permet à un contrôle de savoir si c’est le contrôle par défaut.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propriété spécifie l’opération qui devrait avoir lieu en réponse à un double clic.|
|[put_DocHostFlags](#put_dochostflags)|La `DocHostFlags` propriété spécifie les capacités d’interface utilisateur de l’objet hôte.|
|[put_Font](#put_font)|La `Font` propriété spécifie la police ambiante du conteneur.|
|[put_ForeColor](#put_forecolor)|La `ForeColor` propriété spécifie la couleur ambiante au premier plan du récipient.|
|[put_LocaleID](#put_localeid)|La `LocaleID` propriété spécifie l’ID local ambiant du conteneur.|
|[put_MessageReflect](#put_messagereflect)|La `MessageReflect` propriété ambiante précise si le conteneur reflétera les messages au contrôle hébergé.|
|[put_OptionKeyPath](#put_optionkeypath)|La `OptionKeyPath` propriété spécifie le chemin clé du registre vers les paramètres de l’utilisateur.|
|[put_UserMode](#put_usermode)|La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.|

## <a name="remarks"></a>Notes

Cette interface est exposée par les objets d’hébergement de contrôle ActiveX d’ATL. Appelez les méthodes de cette interface pour définir les propriétés ambiantes disponibles au contrôle hébergé ou pour spécifier d’autres aspects du comportement du conteneur. Pour compléter les `IAxWinAmbientDispatch`propriétés fournies par , utilisez [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost>essayera de charger `IAxWinAmbientDispatch` des `IAxWinAmbientDispatchEx` informations de type sur et à partir du typelib qui contient le code.

Si vous êtes en liaison vers ATL90.dll, **AXHost** chargera les informations de type à partir du typelib dans le DLL.

Voir [Les contrôles Hosting ActiveX à l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour plus de détails.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible sous un certain nombre de formes, comme indiqué dans le tableau ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|Idl|atliface.idl|
|Bibliothèque de type|ATL.dll|
|C++|atliface.h (également inclus dans ATLBase.h)|

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

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatchEx Interface](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow Interface](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
