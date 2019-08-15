---
title: Exemple de point de connexion ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: f33364cee65031c358fb546312f3fe2b7ae854d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491793"
---
# <a name="atl-connection-point-example"></a>Exemple de point de connexion ATL

Cet exemple montre un objet qui prend en charge [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) comme interface sortante:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Lorsque vous `IPropertyNotifySink` spécifiez en tant qu’interface sortante, vous pouvez utiliser `IConnectionPointImpl`la classe [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) au lieu de. Par exemple :

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)
