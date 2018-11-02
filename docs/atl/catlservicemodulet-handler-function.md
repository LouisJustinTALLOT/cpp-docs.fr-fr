---
title: CAtlServiceModuleT::Handler, fonction
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: 74c52e07f5be4ac16c8f9a20115a623c53f46090
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553684"
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT::Handler, fonction

`CAtlServiceModuleT::Handler` est la routine que le Gestionnaire de contrôle des services (SCM) appelle pour récupérer l’état du service et lui donner différentes instructions (par exemple, arrêter ou suspendre). Le SCM passe un code d’opération à `Handler` pour indiquer que le service doit faire. Un service de généré par ATL par défaut gère uniquement l’instruction d’arrêt. Si le SCM passe l’instruction d’arrêt, le service indique au SCM que le programme est prêt à arrêter. Le service appelle ensuite `PostThreadMessage` pour publier un message quit à lui-même. Cela met fin à la boucle de message et le service se ferme définitivement.

Pour gérer des instructions plus détaillées, vous devez modifier le `m_status` le membre de données initialisé dans le `CAtlServiceModuleT` constructeur. Ce membre de données indique au SCM les boutons à activer lorsque le service est sélectionné dans l’application Services du panneau.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

