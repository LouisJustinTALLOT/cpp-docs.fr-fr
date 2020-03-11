---
title: Macros de mappage COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864929"
---
# <a name="com-map-macros"></a>Macros de mappage COM

Ces macros définissent des mappages d’interface COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Marque le début des entrées de mappage de l’interface COM.|
|[END_COM_MAP](#end_com_map)|Marque la fin des entrées de mappage de l’interface COM.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

##  <a name="begin_com_map"></a>BEGIN_COM_MAP

La carte COM est le mécanisme qui expose les interfaces sur un objet à un client par le biais de `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de l’objet de classe sur lequel vous exposez les interfaces.

### <a name="remarks"></a>Notes

[CComObjectRootEx :: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) retourne uniquement des pointeurs pour les interfaces dans le mappage com. Démarrez votre mappage d’interface avec la macro BEGIN_COM_MAP, ajoutez des entrées pour chacune de vos interfaces avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes, puis complétez la carte avec la macro [END_COM_MAP](#end_com_map) .

### <a name="example"></a>Exemple

À partir de l’exemple de code [sonore](../../overview/visual-cpp-samples.md) ATL :

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>END_COM_MAP

Termine la définition de votre mappage d’interface COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de mappage COM](../../atl/reference/com-map-global-functions.md)
