---
title: Exemple de Point de connexion ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a265d26e8733a7eb2982fb84e8d69ed621922d36
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355179"
---
# <a name="atl-connection-point-example"></a>Exemple de point de connexion ATL
Cet exemple montre un objet qui prend en charge [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) comme interface sortante :  
  
 [!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]  
  
 Lors de la spécification `IPropertyNotifySink` comme interface sortante, vous pouvez utiliser la classe [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) au lieu de `IConnectionPointImpl`. Par exemple :  
  
 [!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Point de connexion](../atl/atl-connection-points.md)

