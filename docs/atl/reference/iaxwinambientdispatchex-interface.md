---
description: 'En savoir plus sur : interface IAxWinAmbientDispatchEx'
title: Interface IAxWinAmbientDispatchEx
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: c26ce7fb4f41273a498e3b28e9d6e15d4c89f9ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139722"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interface IAxWinAmbientDispatchEx

Cette interface implémente des propriétés ambiantes supplémentaires pour un contrôle hébergé.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Cette méthode est appelée pour compléter l’interface de propriété ambiante par défaut par une interface définie par l’utilisateur.|

## <a name="remarks"></a>Notes

Incluez cette interface dans les applications ATL qui sont liées statiquement à ATL et les contrôles ActiveX hôtes, en particulier les contrôles ActiveX qui ont des propriétés ambiantes. Si cette interface n’est pas incluse, cette assertion sera générée : « avez-vous oublié de passer le LIBID à CComModule :: init »

Cette interface est exposée par les objets hébergeant le contrôle ActiveX de l’ATL. Dérivé de [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` ajoute une méthode qui vous permet de compléter l’interface de propriété ambiante fournie par ATL avec l’un de vos propres.

<xref:System.Windows.Forms.AxHost> tente de charger des informations de type sur `IAxWinAmbientDispatch` et `IAxWinAmbientDispatchEx` à partir de la bibliothèque de types qui contient le code.

Si vous établissez une liaison à ATL90.dll, **AxHost** chargera les informations de type à partir de la bibliothèque de types dans la dll.

Pour plus d’informations, consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible dans plusieurs formulaires, comme indiqué dans le tableau suivant.

|Type de définition|Fichier|
|---------------------|----------|
|MIDL|atliface. idl|
|Bibliothèque de types|ATL.dll|
|C++|atliface. h (également inclus dans ATLBase. h)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx::SetAmbientDispatch

Cette méthode est appelée pour compléter l’interface de propriété ambiante par défaut par une interface définie par l’utilisateur.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatch*<br/>
Pointeur vers la nouvelle interface.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Lorsque `SetAmbientDispatch` est appelé avec un pointeur vers une nouvelle interface, cette nouvelle interface est utilisée pour appeler toutes les propriétés ou méthodes demandées par le contrôle hébergé, si ces propriétés ne sont pas déjà fournies par [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Voir aussi

[Interface IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
