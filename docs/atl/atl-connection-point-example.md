---
title: Exemple de point de connexion ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 3113637a3f777a56bc0b0994203ce709fbc189d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265065"
---
# <a name="atl-connection-point-example"></a>Exemple de point de connexion ATL

Cet exemple montre un objet qui prend en charge [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) comme interface sortante :

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Lorsque vous spécifiez `IPropertyNotifySink` comme interface sortante, vous pouvez utiliser la classe [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) au lieu de `IConnectionPointImpl`. Exemple :

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)
