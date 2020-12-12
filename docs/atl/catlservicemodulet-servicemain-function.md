---
description: 'En savoir plus sur : CAtlServiceModuleT :: ServiceMain, fonction'
title: 'CAtlServiceModuleT :: ServiceMain, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 97093d13a2f13ea0d6bd4ba5db46bef45d239cc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148328"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT :: ServiceMain, fonction

Le gestionnaire de contrôle des services (SCM) appelle `ServiceMain` lorsque vous ouvrez l’application services du panneau de configuration, sélectionnez le service, puis cliquez sur **Démarrer**.

Une fois le SCM appelé `ServiceMain` , un service doit fournir au SCM une fonction de gestionnaire. Cette fonction permet au SCM d’obtenir l’état du service et de transmettre des instructions spécifiques (telles que la suspension ou l’arrêt). Le SCM obtient cette fonction lorsque le service passe `_Handler` à la fonction API Win32, [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw). ( `_Handler` est une fonction membre statique qui appelle le [Gestionnaire](../atl/reference/catlservicemodulet-class.md#handler)de fonctions membres non statiques.)

Au démarrage, un service doit également informer le SCM de son état actuel. Pour ce faire, il passe SERVICE_START_PENDING à la fonction API Win32, [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus).

`ServiceMain` appelle ensuite `CAtlExeModuleT::InitializeCom` , qui appelle la fonction d’API Win32 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex). Par défaut, `InitializeCom` passe l’indicateur COINIT_MULTITHREADED à la fonction. Cet indicateur indique que le programme doit être un serveur à threads libres.

À présent, `CAtlServiceModuleT::Run` est appelé pour effectuer le travail principal du service. `Run` continue à s’exécuter jusqu’à ce que le service soit arrêté.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT :: ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
