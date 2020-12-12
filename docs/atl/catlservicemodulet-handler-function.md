---
description: 'En savoir plus sur : CAtlServiceModuleT :: Handler, fonction'
title: 'CAtlServiceModuleT :: Handler, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: 934c612b6fdfd47bb9966536cc335da58fbd38c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148367"
---
# <a name="catlservicemodulethandler-function"></a>CAtlServiceModuleT :: Handler, fonction

`CAtlServiceModuleT::Handler` est la routine que le gestionnaire de contrôle des services (SCM) appelle pour récupérer l’état du service et lui fournir diverses instructions (comme l’arrêt ou la suspension). Le SCM passe un code d’opération à `Handler` pour indiquer ce que le service doit faire. Un service généré par ATL par défaut gère uniquement l’instruction Stop. Si le SCM passe l’instruction Stop, le service indique au SCM que le programme est sur le point de s’arrêter. Le service appelle ensuite `PostThreadMessage` pour envoyer un message Quit à lui-même. Cela met fin à la boucle de message et le service se ferme finalement.

Pour gérer davantage d’instructions, vous devez modifier le `m_status` membre de données initialisé dans le `CAtlServiceModuleT` constructeur. Ce membre de données indique au SCM les boutons à activer lorsque le service est sélectionné dans l’application services du panneau de configuration.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT :: Handler](../atl/reference/catlservicemodulet-class.md#handler)
