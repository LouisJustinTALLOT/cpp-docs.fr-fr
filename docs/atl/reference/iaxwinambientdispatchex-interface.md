---
title: IAxWinAmbientDispatchEx Interface
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329979"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx Interface

Cette interface implémente des propriétés ambiantes supplémentaires pour un contrôle hébergé.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[SetAmbientDispatch SetAmbientDispatch SetAmbientDispatch SetAmbi](#setambientdispatch)|Cette méthode est appelée pour compléter l’interface de propriété ambiante par défaut avec une interface définie par l’utilisateur.|

## <a name="remarks"></a>Notes

Inclure cette interface dans les applications ATL qui sont statiquement liées à ATL et héberger activeX Controls, en particulier ActiveX Controls qui ont des propriétés ambiantes. Sans compter cette interface va générer cette affirmation: "Avez-vous oublié de passer le LIBID à CComModule::Init"

Cette interface est exposée par les objets d’hébergement de contrôle ActiveX d’ATL. Dérivé de [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` ajoute une méthode qui vous permet de compléter l’interface de propriété ambiante fournie par ATL avec l’un des vôtres.

<xref:System.Windows.Forms.AxHost>essayera de charger `IAxWinAmbientDispatch` des `IAxWinAmbientDispatchEx` informations de type sur et à partir de la bibliothèque de type qui contient le code.

Si vous êtes en liaison vers ATL90.dll, **AXHost** chargera les informations de type de la bibliothèque de type dans le DLL.

Voir [Les contrôles Hosting ActiveX à l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour plus de détails.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible sous un certain nombre de formes, comme le montre le tableau suivant.

|Type de définition|Fichier|
|---------------------|----------|
|Idl|atliface.idl|
|Bibliothèque de type|ATL.dll|
|C++|atliface.h (également inclus dans ATLBase.h)|

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

Lorsqu’elle `SetAmbientDispatch` est appelée avec un pointeur vers une nouvelle interface, cette nouvelle interface sera utilisée pour invoquer toutes les propriétés ou méthodes demandées par le contrôle hébergé, si ces propriétés ne sont pas déjà fournies par [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)
