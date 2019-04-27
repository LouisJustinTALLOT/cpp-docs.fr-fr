---
title: CAtlServiceModuleT::ServiceMain, fonction
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 81cd8fcbdf275063b243e215301eff504a2b5cc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223207"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain, fonction

Appelle le Gestionnaire de contrôle des services (SCM) `ServiceMain` lorsque vous ouvrez l’application Services du panneau, sélectionnez le service, puis cliquez sur **Démarrer**.

Une fois le GCL appelle `ServiceMain`, un service doit donner au SCM une fonction gestionnaire. Cette fonction vous permet du GCL obtenir l’état du service et passer des instructions spécifiques (par exemple, la suspension ou l’arrêt). Le SCM obtient cette fonction lorsque le service passe `_Handler` à la fonction API Win32, [RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera). (`_Handler` est une fonction membre statique qui appelle la fonction membre non statique [gestionnaire](../atl/reference/catlservicemodulet-class.md#handler).)

Au démarrage, un service doit également informer le SCM de son état actuel. Pour cela, en passant SERVICE_START_PENDING à la fonction API Win32, il [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` appelle ensuite `CAtlExeModuleT::InitializeCom`, qui appelle la fonction API Win32 [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex). Par défaut, `InitializeCom` passe l’indicateur COINIT_MULTITHREADED à la fonction. Cet indicateur indique que le programme doit être un serveur libre de threads.

Maintenant, `CAtlServiceModuleT::Run` est appelée pour effectuer le travail principal du service. `Run` continue à s’exécuter jusqu'à ce que le service est arrêté.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
