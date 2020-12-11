---
description: 'En savoir plus sur : attribute unextensible'
title: Attribut unextensible
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5bad214d6688570bc4a69aca952f6bed98c2b0dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159399"
---
# <a name="nonextensible-attribute"></a>Attribut unextensible

Si une interface double n’est pas étendue au moment de l’exécution (autrement dit, si vous ne fournissez pas de méthodes ou de propriétés via `IDispatch::Invoke` qui ne sont pas disponibles via la vtable), vous devez appliquer l’attribut non **extensible** à votre définition d’interface. Cet attribut fournit des informations aux langages clients (tels que Visual Basic) qui peuvent être utilisés pour activer la vérification de code complète au moment de la compilation. Si cet attribut n’est pas fourni, les bogues peuvent rester masqués dans le code client jusqu’au moment de l’exécution.

Pour plus d’informations sur l’attribut non **extensible** et un exemple, consultez non [extensible](../windows/attributes/nonextensible.md).

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
