---
description: 'En savoir plus sur : exemple de point de connexion ATL'
title: Exemple de point de connexion ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 6416720b5366838f9687f31947cac9a6824da058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165808"
---
# <a name="atl-connection-point-example"></a>Exemple de point de connexion ATL

Cet exemple montre un objet qui prend en charge [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) comme interface sortante :

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Lorsque vous spécifiez `IPropertyNotifySink` en tant qu’interface sortante, vous pouvez utiliser la classe [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) au lieu de `IConnectionPointImpl` . Par exemple :

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)
