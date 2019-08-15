---
title: 'CAtlServiceModuleT:: ServiceMain, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491720"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain, fonction

Le gestionnaire de contrôle des services (SCM `ServiceMain` ) appelle lorsque vous ouvrez l’application services du panneau de configuration, sélectionnez le service, puis cliquez sur **Démarrer**.

Une fois le SCM `ServiceMain`appelé, un service doit fournir au SCM une fonction de gestionnaire. Cette fonction permet au SCM d’obtenir l’état du service et de transmettre des instructions spécifiques (telles que la suspension ou l’arrêt). Le SCM obtient cette fonction lorsque le service passe `_Handler` à la fonction API Win32, [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw). (`_Handler` est une fonction membre statique qui appelle le [Gestionnaire](../atl/reference/catlservicemodulet-class.md#handler)de fonctions membres non statiques.)

Au démarrage, un service doit également informer le SCM de son état actuel. Pour ce faire, il passe SERVICE_START_PENDING à la fonction API Win32, [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain`appelle `CAtlExeModuleT::InitializeCom`ensuite, qui appelle la fonction d’API Win32 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex). Par défaut, `InitializeCom` passe l’indicateur COINIT_MULTITHREADED à la fonction. Cet indicateur indique que le programme doit être un serveur à threads libres.

À présent `CAtlServiceModuleT::Run` , est appelé pour effectuer le travail principal du service. `Run`continue à s’exécuter jusqu’à ce que le service soit arrêté.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
