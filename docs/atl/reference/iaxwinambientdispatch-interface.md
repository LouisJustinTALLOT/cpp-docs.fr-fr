---
title: Interface de IAxWinAmbientDispatch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d082faf4c25f76fd7a98cc897760adc424ffb49e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366326"
---
# <a name="iaxwinambientdispatch-interface"></a>Interface de IAxWinAmbientDispatch
Cette interface fournit des méthodes permettant de spécifier les caractéristiques du contrôle hébergé ou du conteneur.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|Le **AllowContextMenu** propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|  
|[get_AllowShowUI](#get_allowshowui)|Le **AllowShowUI** propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Le **AllowWindowlessActivation** propriété spécifie si le conteneur autorise l’activation sans fenêtre.|  
|[get_BackColor](#get_backcolor)|Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault** est une propriété ambiante qui permet à un contrôle savoir s’il est le contrôle par défaut.|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Le **DocHostDoubleClickFlags** propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|  
|[get_DocHostFlags](#get_dochostflags)|Le **DocHostFlags** propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.|  
|[get_Font](#get_font)|Le **police** propriété spécifie la police ambiante du conteneur.|  
|[get_ForeColor](#get_forecolor)|Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|  
|[get_LocaleID](#get_localeid)|Le **LocaleID** propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.|  
|[get_MessageReflect](#get_messagereflect)|Le **MessageReflect** propriété ambiante Spécifie si le conteneur refléteront les messages pour le contrôle hébergé.|  
|[get_OptionKeyPath](#get_optionkeypath)|Le **OptionKeyPath** propriété spécifie le chemin de clé de Registre pour les paramètres de l’utilisateur.|  
|[get_ShowGrabHandles](#get_showgrabhandles)|Le **ShowGrabHandles** propriété ambiante permet au contrôle déterminer si elle doit dessiner avec des poignées de manipulation.|  
|[get_ShowHatching](#get_showhatching)|Le **ShowHatching** propriété ambiante permet au contrôle déterminer si elle doit être dessiné lui-même livrés.|  
|[get_UserMode](#get_usermode)|Le **UserMode** propriété indique le mode utilisateur ambiante du conteneur.|  
|[put_AllowContextMenu](#put_allowcontextmenu)|Le **AllowContextMenu** propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.|  
|[put_AllowShowUI](#put_allowshowui)|Le **AllowShowUI** propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Le **AllowWindowlessActivation** propriété spécifie si le conteneur autorise l’activation sans fenêtre.|  
|[put_BackColor](#put_backcolor)|Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault** est une propriété ambiante qui permet à un contrôle savoir s’il est le contrôle par défaut.|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Le **DocHostDoubleClickFlags** propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.|  
|[put_DocHostFlags](#put_dochostflags)|Le **DocHostFlags** propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.|  
|[put_Font](#put_font)|Le **police** propriété spécifie la police ambiante du conteneur.|  
|[put_ForeColor](#put_forecolor)|Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.|  
|[put_LocaleID](#put_localeid)|Le **LocaleID** propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.|  
|[put_MessageReflect](#put_messagereflect)|Le **MessageReflect** propriété ambiante Spécifie si le conteneur refléteront les messages pour le contrôle hébergé.|  
|[put_OptionKeyPath](#put_optionkeypath)|Le **OptionKeyPath** propriété spécifie le chemin de clé de Registre pour les paramètres de l’utilisateur.|  
|[put_UserMode](#put_usermode)|Le **UserMode** propriété indique le mode utilisateur ambiante du conteneur.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est exposée par le contrôle ActiveX de d’ATL qui héberge les objets. Appelez les méthodes sur cette interface pour définir les propriétés ambiantes disponibles pour le contrôle hébergé ou pour spécifier d’autres aspects du comportement du conteneur. Pour compléter les propriétés fournies par `IAxWinAmbientDispatch`, utilisez [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) essaie de charger les informations de type sur `IAxWinAmbientDispatch` et `IAxWinAmbientDispatchEx` à partir de la bibliothèque de types qui contient le code.  
  
 Si vous établissez la liaison ATL90.dll, **AXHost** charge les informations de type à partir de la bibliothèque de types dans la DLL.  
  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour plus d’informations.  
  
## <a name="requirements"></a>Spécifications  
 La définition de cette interface est disponible dans plusieurs formes, comme indiqué dans le tableau ci-dessous.  
  
|Type de définition|Fichier|  
|---------------------|----------|  
|IDL|atliface.idl|  
|Bibliothèque de types|ATL.dll|  
|C++|atliface.h (également inclus dans ATLBase.h)|  
  
##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu  
 Le **AllowContextMenu** propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbAllowContextMenu*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI  
 Le **AllowShowUI** propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbAllowShowUI*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **VARIANT_FALSE** comme valeur par défaut de cette propriété.  
  
##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 Le **AllowWindowlessActivation** propriété spécifie si le conteneur autorise l’activation sans fenêtre.  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbAllowWindowless*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor  
 Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrBackground*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **COLOR_BTNFACE** ou **COLOR_WINDOW** en tant que la valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).  
  
##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault** est une propriété ambiante qui permet à un contrôle savoir s’il est le contrôle par défaut.  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbDisplayAsDefault*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **VARIANT_FALSE** comme valeur par défaut de cette propriété.  
  
##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 Le **DocHostDoubleClickFlags** propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *pdwDocHostDoubleClickFlags*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **DOCHOSTUIDBLCLK_DEFAULT** en tant que la valeur par défaut de cette propriété.  
  
##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags  
 Le **DocHostFlags** propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *pdwDocHostFlags*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **DOCHOSTUIFLAG_NO3DBORDER** en tant que la valeur par défaut de cette propriété.  
  
##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font  
 Le **police** propriété spécifie la police ambiante du conteneur.  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFont`  
 [out] L’adresse d’un **IFontDisp** pointeur d’interface utilisé pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise la police de l’interface graphique utilisateur par défaut ou la police système en tant que la valeur par défaut de cette propriété.  
  
##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor  
 Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrForeground*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise la couleur du texte fenêtre système en tant que la valeur par défaut de cette propriété.  
  
##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID  
 Le **LocaleID** propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>Paramètres  
 *plcidLocaleID*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise des paramètres régionaux par défaut de l’utilisateur en tant que la valeur par défaut de cette propriété.  
  
 Avec cette méthode, vous pouvez découvrir LocalID ambiante, autrement dit, l’identificateur des paramètres régionaux du programme de votre contrôle est utilisé dans. Une fois que vous connaissez l’identificateur des paramètres régionaux, vous pouvez appeler code pour charger les paramètres régionaux spécifiques, légendes, texte du message d’erreur, et ainsi de suite à partir d’un fichier de ressources ou d’une DLL satellite.  
  
##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect  
 Le **MessageReflect** propriété ambiante Spécifie si le conteneur refléteront les messages pour le contrôle hébergé.  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbMessageReflect*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath  
 Le **OptionKeyPath** propriété spécifie le chemin de clé de Registre pour les paramètres de l’utilisateur.  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbstrOptionKeyPath*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles  
 Le **ShowGrabHandles** propriété ambiante permet au contrôle déterminer si elle doit dessiner avec des poignées de manipulation.  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbShowGrabHandles*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’ATL hôte objet implémentation retourne toujours **VARIANT_FALSE** en tant que la valeur de cette propriété.  
  
##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching  
 Le **ShowHatching** propriété ambiante permet au contrôle déterminer si elle doit être dessiné lui-même livrés.  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbShowHatching*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’ATL hôte objet implémentation retourne toujours **VARIANT_FALSE** en tant que la valeur de cette propriété.  
  
##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode  
 Le **UserMode** propriété indique le mode utilisateur ambiante du conteneur.  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbUserMode*  
 [out] L’adresse d’une variable pour recevoir la valeur actuelle de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu  
 Le **AllowContextMenu** propriété spécifie si le contrôle hébergé est autorisé à afficher son propre menu contextuel.  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAllowContextMenu*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI  
 Le **AllowShowUI** propriété spécifie si le contrôle hébergé est autorisé à afficher sa propre interface utilisateur.  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAllowShowUI*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **VARIANT_FALSE** comme valeur par défaut de cette propriété.  
  
##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 Le **AllowWindowlessActivation** propriété spécifie si le conteneur autorise l’activation sans fenêtre.  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAllowWindowless*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor  
 Le `BackColor` propriété spécifie la couleur d’arrière-plan ambiante du conteneur.  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrBackground*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **COLOR_BTNFACE** ou **COLOR_WINDOW** en tant que la valeur par défaut de cette propriété (selon que le parent de la fenêtre hôte est une boîte de dialogue ou non).  
  
##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault** est une propriété ambiante qui permet à un contrôle savoir s’il est le contrôle par défaut.  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 `bDisplayAsDefault`  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **VARIANT_FALSE** comme valeur par défaut de cette propriété.  
  
##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 Le **DocHostDoubleClickFlags** propriété spécifie l’opération qui doit avoir lieu en réponse à un double-clic.  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDocHostDoubleClickFlags*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **DOCHOSTUIDBLCLK_DEFAULT** en tant que la valeur par défaut de cette propriété.  
  
##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags  
 Le **DocHostFlags** propriété spécifie les fonctionnalités d’interface utilisateur de l’objet hôte.  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDocHostFlags*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise **DOCHOSTUIFLAG_NO3DBORDER** en tant que la valeur par défaut de cette propriété.  
  
##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font  
 Le **police** propriété spécifie la police ambiante du conteneur.  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFont`  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise la police de l’interface graphique utilisateur par défaut ou la police système en tant que la valeur par défaut de cette propriété.  
  
##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor  
 Le `ForeColor` propriété spécifie la couleur de premier plan ambiante du conteneur.  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrForeground*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise la couleur du texte fenêtre système en tant que la valeur par défaut de cette propriété.  
  
##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID  
 Le **LocaleID** propriété spécifie l’ID de paramètres régionaux ambiante du conteneur.  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>Paramètres  
 *lcidLocaleID*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise des paramètres régionaux par défaut de l’utilisateur en tant que la valeur par défaut de cette propriété.  
  
##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect  
 Le **MessageReflect** propriété ambiante Spécifie si le conteneur refléteront les messages pour le contrôle hébergé.  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>Paramètres  
 `bMessageReflect`  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath  
 Le **OptionKeyPath** propriété spécifie le chemin de clé de Registre pour les paramètres de l’utilisateur.  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrOptionKeyPath*  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode  
 Le **UserMode** propriété indique le mode utilisateur ambiante du conteneur.  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `bUserMode`  
 [in] La nouvelle valeur de cette propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’implémentation d’objet hôte ATL utilise `VARIANT_TRUE` comme valeur par défaut de cette propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface de IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [Interface de l’interface IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









