---
title: Com Carte Macros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326601"
---
# <a name="com-map-macros"></a>Com Carte Macros

Ces macros définissent les cartes d’interface COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marque le début des entrées de carte d’interface COM.|
|[END_COM_MAP](#end_com_map)|Marque la fin des entrées de carte d’interface COM.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

La carte COM est le mécanisme qui expose les `QueryInterface`interfaces sur un objet à un client à travers .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de l’objet de classe sur laquelle vous exposez les interfaces.

### <a name="remarks"></a>Notes

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) ne renvoie que des indications pour les interfaces dans la carte COM. Démarrez votre carte d’interface avec la macro BEGIN_COM_MAP, ajoutez des entrées pour chacune de vos interfaces avec la [macro COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes, et complétez la carte avec la [macro END_COM_MAP.](#end_com_map)

### <a name="example"></a>Exemple

De l’échantillon ATL [BEEPER](../../overview/visual-cpp-samples.md) :

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

Termine la définition de votre carte d’interface COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[COM Map Fonctions globales](../../atl/reference/com-map-global-functions.md)
