---
title: nonextensible (attribut)
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257629"
---
# <a name="nonextensible-attribute"></a>nonextensible (attribut)

Si une interface double n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournissez des méthodes ou propriétés via `IDispatch::Invoke` qui ne sont pas disponibles via la vtable), vous devez appliquer le **nonextensible** à votre interface d’attribut définition. Cet attribut fournit des informations pour les langues du client (par exemple, Visual Basic) qui peut être utilisé pour activer la vérification de code complet au moment de la compilation. Si cet attribut n’est pas fourni, bogues peuvent rester masqués dans le code client jusqu’au moment de l’exécution.

Pour plus d’informations sur la **nonextensible** attribut et un exemple, consultez [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
