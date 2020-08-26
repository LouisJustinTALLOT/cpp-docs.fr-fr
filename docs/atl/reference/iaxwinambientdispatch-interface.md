---
title: Interface IAxWinAmbientDispatch
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
ms.openlocfilehash: a53481a57676b5b4a253a3501d3536e5115907a7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833411"
---
# <a name="iaxwinambientdispatch-interface"></a>Interface IAxWinAmbientDispatch

Cette interface fournit des méthodes pour spécifier les caractéristiques du conteneur ou du contrôle hébergé.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|La `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|
|[get_AllowShowUI](#get_allowshowui)|La `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|La `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.|
|[get_BackColor](#get_backcolor)|La `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|
|[get_DocHostFlags](#get_dochostflags)|La `DocHostFlags` propriété spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.|
|[get_Font](#get_font)|La `Font` propriété spécifie la police ambiante du conteneur.|
|[get_ForeColor](#get_forecolor)|La `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|
|[get_LocaleID](#get_localeid)|La `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiants du conteneur.|
|[get_MessageReflect](#get_messagereflect)|La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.|
|[get_OptionKeyPath](#get_optionkeypath)|La `OptionKeyPath` propriété spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.|
|[get_ShowGrabHandles](#get_showgrabhandles)|La `ShowGrabHandles` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même avec des poignées de manipulation.|
|[get_ShowHatching](#get_showhatching)|La `ShowHatching` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même.|
|[get_UserMode](#get_usermode)|La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.|
|[put_AllowContextMenu](#put_allowcontextmenu)|La `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|
|[put_AllowShowUI](#put_allowshowui)|La `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|La `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.|
|[put_BackColor](#put_backcolor)|La `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|
|[put_DocHostFlags](#put_dochostflags)|La `DocHostFlags` propriété spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.|
|[put_Font](#put_font)|La `Font` propriété spécifie la police ambiante du conteneur.|
|[put_ForeColor](#put_forecolor)|La `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|
|[put_LocaleID](#put_localeid)|La `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiants du conteneur.|
|[put_MessageReflect](#put_messagereflect)|La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.|
|[put_OptionKeyPath](#put_optionkeypath)|La `OptionKeyPath` propriété spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.|
|[put_UserMode](#put_usermode)|La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.|

## <a name="remarks"></a>Notes

Cette interface est exposée par les objets hébergeant le contrôle ActiveX de l’ATL. Appelez les méthodes sur cette interface pour définir les propriétés ambiantes disponibles pour le contrôle hébergé ou pour spécifier d’autres aspects du comportement du conteneur. Pour compléter les propriétés fournies par `IAxWinAmbientDispatch` , utilisez [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost> tente de charger des informations de type sur `IAxWinAmbientDispatch` et `IAxWinAmbientDispatchEx` à partir de la TypeLib qui contient le code.

Si vous établissez une liaison à ATL90.dll, **AxHost** chargera les informations de type à partir de la TypeLib dans la dll.

Pour plus d’informations, consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible dans plusieurs formulaires, comme indiqué dans le tableau ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|MIDL|atliface. idl|
|Bibliothèque de types|ATL.dll|
|C++|atliface. h (également inclus dans ATLBase. h)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch :: get_AllowContextMenu

La `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*pbAllowContextMenu*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch :: get_AllowShowUI

La `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*pbAllowShowUI*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch :: get_AllowWindowlessActivation

La `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*pbAllowWindowless*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch :: get_BackColor

La `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Paramètres

*pclrBackground*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch :: get_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*pbDisplayAsDefault*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch :: get_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostDoubleClickFlags*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch :: get_DocHostFlags

La `DocHostFlags` propriété spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*pdwDocHostFlags*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch :: get_Font

La `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
à Adresse d’un `IFontDisp` pointeur d’interface utilisé pour recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police de l’interface utilisateur graphique par défaut ou la police système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch :: get_ForeColor

La `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Paramètres

*pclrForeground*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur de texte de la fenêtre système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch :: get_LocaleID

La `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiants du conteneur.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*plcidLocaleID*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise les paramètres régionaux par défaut de l’utilisateur comme valeur par défaut de cette propriété.

Avec cette méthode, vous pouvez découvrir le LocalID ambiant, c’est-à-dire le LocaleID du programme dans lequel votre contrôle est utilisé. Une fois que vous connaissez le LocaleID, vous pouvez appeler du code pour charger des sous-titres spécifiques aux paramètres régionaux, du texte du message d’erreur, etc. à partir d’un fichier de ressources ou d’une DLL satellite.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch :: get_MessageReflect

La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Paramètres

*pbMessageReflect*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch :: get_OptionKeyPath

La `OptionKeyPath` propriété spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*pbstrOptionKeyPath*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch :: get_ShowGrabHandles

La `ShowGrabHandles` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même avec des poignées de manipulation.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Paramètres

*pbShowGrabHandles*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL retourne toujours VARIANT_FALSE comme valeur de cette propriété.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch :: get_ShowHatching

La `ShowHatching` propriété ambiante permet au contrôle de déterminer s’il doit se dessiner lui-même.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Paramètres

*pbShowHatching*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL retourne toujours VARIANT_FALSE comme valeur de cette propriété.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch :: get_UserMode

La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Paramètres

*pbUserMode*<br/>
à Adresse d’une variable devant recevoir la valeur actuelle de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch ::p ut_AllowContextMenu

La `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Paramètres

*bAllowContextMenu*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch ::p ut_AllowShowUI

La `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Paramètres

*bAllowShowUI*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch ::p ut_AllowWindowlessActivation

La `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Paramètres

*bAllowWindowless*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch ::p ut_BackColor

La `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Paramètres

*clrBackground*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise COLOR_BTNFACE ou COLOR_WINDOW comme valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch ::p ut_DisplayAsDefault

`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle de déterminer s’il s’agit du contrôle par défaut.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Paramètres

*bDisplayAsDefault*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_FALSE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch ::p ut_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostDoubleClickFlags*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIDBLCLK_DEFAULT comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch ::p ut_DocHostFlags

La `DocHostFlags` propriété spécifie les fonctionnalités de l’interface utilisateur de l’objet hôte.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Paramètres

*dwDocHostFlags*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise DOCHOSTUIFLAG_NO3DBORDER comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch ::p ut_Font

La `Font` propriété spécifie la police ambiante du conteneur.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la police de l’interface utilisateur graphique par défaut ou la police système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch ::p ut_ForeColor

La `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Paramètres

*clrForeground*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise la couleur de texte de la fenêtre système comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch ::p ut_LocaleID

La `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiants du conteneur.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Paramètres

*lcidLocaleID*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise les paramètres régionaux par défaut de l’utilisateur comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch ::p ut_MessageReflect

La `MessageReflect` propriété ambiante spécifie si le conteneur doit refléter les messages dans le contrôle hébergé.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Paramètres

*bMessageReflect*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch ::p ut_OptionKeyPath

La `OptionKeyPath` propriété spécifie le chemin d’accès à la clé de Registre pour les paramètres utilisateur.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Paramètres

*bstrOptionKeyPath*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch ::p ut_UserMode

La `UserMode` propriété spécifie le mode utilisateur ambiant du conteneur.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Paramètres

*bUserMode*<br/>
dans Nouvelle valeur de cette propriété.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation de l’objet hôte ATL utilise VARIANT_TRUE comme valeur par défaut de cette propriété.

## <a name="see-also"></a>Voir aussi

[Interface IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Interface IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
