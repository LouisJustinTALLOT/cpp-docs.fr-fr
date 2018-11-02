---
title: Iaxwinambientdispatchex, Interface
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 5b4afabe2c12dff048bc6a6fb904a82b3cea4d01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539436"
---
# <a name="iaxwinambientdispatchex-interface"></a>Iaxwinambientdispatchex, Interface

Cette interface implémente des propriétés ambiantes supplémentaires pour un contrôle hébergé.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Cette méthode est appelée pour compléter l’interface de la propriété ambiante par défaut avec une interface définie par l’utilisateur.|

## <a name="remarks"></a>Notes

Inclure cette interface dans les applications ATL qui sont liées statiquement ATL et l’héberger des contrôles ActiveX, en particulier les contrôles ActiveX qui ont des propriétés ambiantes. Non compris cette interface génère cette assertion : « Vous avez oublié à passer LIBID à CComModule::Init »

Cette interface est exposée par le contrôle ActiveX d’ATL hébergement d’objets. Dérivé [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` ajoute une méthode qui vous permet de compléter l’interface de propriété ambiante fournie par ATL avec celle de votre choix.

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) essaie de charger les informations de type sur `IAxWinAmbientDispatch` et `IAxWinAmbientDispatchEx` à partir de la bibliothèque de types qui contient le code.

Si vous établissez une liaison à ATL90.dll, **AXHost** charge les informations de type à partir de la bibliothèque de types dans la DLL.

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour plus d’informations.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible dans plusieurs formes, comme illustré dans le tableau suivant.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|atliface.idl|
|Bibliothèque de types|ATL.dll|
|C++|atliface.h (également inclus dans ATLBase.h)|

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

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatch, interface](../../atl/reference/iaxwinambientdispatch-interface.md)
