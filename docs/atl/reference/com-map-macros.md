---
title: Macros de mappage COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: e3358ff9f3f2aa5f3dde81c5eb218278178822ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563876"
---
# <a name="com-map-macros"></a>Macros de mappage COM

Ces macros définissent des tables d’interface COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marque le début des entrées de mappage d’interface COM.|
|[END_COM_MAP](#end_com_map)|Marque la fin des entrées de mappage d’interface COM.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

Mappage COM est un mécanisme qui expose des interfaces sur un objet à un client via `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Le nom de l’objet de classe que vous exposez des interfaces sur.

### <a name="remarks"></a>Notes

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) ne renvoie que des pointeurs pour les interfaces dans le mappage COM. Démarrez votre carte d’interface avec la macro BEGIN_COM_MAP, ajouter des entrées pour chacun de vos interfaces avec la [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) macro ou une de ses variantes et effectuer un mappage avec le [END_COM_MAP](#end_com_map) macro.

### <a name="example"></a>Exemple

À partir de la bibliothèque ATL [BEEPER](../../visual-cpp-samples.md) exemple :

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

Met fin à la définition de votre carte d’interface COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de mappage COM](../../atl/reference/com-map-global-functions.md)
