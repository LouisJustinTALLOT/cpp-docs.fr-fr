---
title: nonextensible (attribut)
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: cc57acb8bd7bc3e32c764606da651f57316ceabf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250101"
---
# <a name="nonextensible-attribute"></a>nonextensible (attribut)

Si une interface double n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournissez des méthodes ou propriétés via `IDispatch::Invoke` qui ne sont pas disponibles via la vtable), vous devez appliquer le **nonextensible** à votre interface d’attribut définition. Cet attribut fournit des informations pour les langues du client (par exemple, Visual Basic) qui peut être utilisé pour activer la vérification de code complet au moment de la compilation. Si cet attribut n’est pas fourni, bogues peuvent rester masqués dans le code client jusqu’au moment de l’exécution.

Pour plus d’informations sur la **nonextensible** attribut et un exemple, consultez [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
