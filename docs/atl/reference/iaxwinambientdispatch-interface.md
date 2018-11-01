---
title: IAxWinAmbientDispatch, Interface
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
ms.openlocfilehash: f143b2c58159d1bb0812152c68d3c31153d4570d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467429"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch, Interface

Cette interface fournit des méthodes permettant de spécifier les caractéristiques du contrôle hébergé ou du conteneur.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|Le `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|
|[get_AllowShowUI](#get_allowshowui)|Le `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Le `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.|
|[get_BackColor](#get_backcolor)|Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle déterminer si elle est le contrôle par défaut.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Le `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|
|[get_DocHostFlags](#get_dochostflags)|Le `DocHostFlags` propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.|
|[get_Font](#get_font)|Le `Font` propriété spécifie la police ambiante du conteneur.|
|[get_ForeColor](#get_forecolor)|Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|
|[get_LocaleID](#get_localeid)|Le `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.|
|[get_MessageReflect](#get_messagereflect)|Le `MessageReflect` propriété ambiante Spécifie si le conteneur reflètent les messages pour le contrôle hébergé.|
|[get_OptionKeyPath](#get_optionkeypath)|Le `OptionKeyPath` propriété spécifie le chemin de clé de Registre aux paramètres utilisateur.|
|[get_ShowGrabHandles](#get_showgrabhandles)|Le `ShowGrabHandles` propriété ambiante permet au contrôle déterminer si elle doit dessiner avec des poignées de manipulation.|
|[get_ShowHatching](#get_showhatching)|Le `ShowHatching` propriété ambiante permet au contrôle déterminer si elle doit se dessiner lui-même hachée.|
|[get_UserMode](#get_usermode)|Le `UserMode` propriété indique le mode utilisateur ambiante du conteneur.|
|[put_AllowContextMenu](#put_allowcontextmenu)|Le `AllowContextMenu` propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|
|[put_AllowShowUI](#put_allowshowui)|Le `AllowShowUI` propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Le `AllowWindowlessActivation` propriété spécifie si le conteneur autorise l’activation sans fenêtre.|
|[put_BackColor](#put_backcolor)|Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` est une propriété ambiante qui permet à un contrôle déterminer si elle est le contrôle par défaut.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Le `DocHostDoubleClickFlags` propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|
|[put_DocHostFlags](#put_dochostflags)|Le `DocHostFlags` propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.|
|[put_Font](#put_font)|Le `Font` propriété spécifie la police ambiante du conteneur.|
|[put_ForeColor](#put_forecolor)|Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|
|[put_LocaleID](#put_localeid)|Le `LocaleID` propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.|
|[put_MessageReflect](#put_messagereflect)|Le `MessageReflect` propriété ambiante Spécifie si le conteneur reflètent les messages pour le contrôle hébergé.|
|[put_OptionKeyPath](#put_optionkeypath)|Le `OptionKeyPath` propriété spécifie le chemin de clé de Registre aux paramètres utilisateur.|
|[put_UserMode](#put_usermode)|Le `UserMode` propriété indique le mode utilisateur ambiante du conteneur.|

## <a name="remarks"></a>Notes

Cette interface est exposée par le contrôle ActiveX d’ATL hébergement d’objets. Appelez les méthodes sur cette interface pour définir les propriétés ambiantes disponibles pour le contrôle hébergé ou pour spécifier d’autres aspects du comportement du conteneur. Pour compléter les propriétés fournies par `IAxWinAmbientDispatch`, utilisez [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) essaie de charger les informations de type sur `IAxWinAmbientDispatch` et `IAxWinAmbientDispatchEx` à partir de la bibliothèque de types qui contient le code.

Si vous établissez une liaison à ATL90.dll, **AXHost** charge les informations de type à partir de la bibliothèque de types dans la DLL.

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour plus d’informations.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible dans plusieurs formes, comme illustré dans le tableau ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|atliface.idl|
|Bibliothèque de types|ATL.dll|
|C++|atliface.h (également inclus dans ATLBase.h)|

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

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatchEx, interface](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow, interface](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

