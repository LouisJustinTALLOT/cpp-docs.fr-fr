---
title: nonextensible (attribut) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40b4b79701862ca07e704aca098419479923ef1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355631"
---
# <a name="nonextensible-attribute"></a>nonextensible (attribut)
Si une interface double n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournissez des méthodes ou propriétés via **IDispatch::Invoke** qui ne sont pas disponibles via la vtable), vous devez appliquer le **nonextensible** attribut à votre définition d’interface. Cet attribut fournit des informations pour les langues du client (par exemple, Visual Basic) qui peut être utilisé pour activer la vérification du code au moment de la compilation. Si cet attribut n’est pas fourni, les bogues peuvent rester masqués dans le code client jusqu’au moment de l’exécution.  
  
 Pour plus d’informations sur la **nonextensible** attribut et un exemple, consultez [nonextensible](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

