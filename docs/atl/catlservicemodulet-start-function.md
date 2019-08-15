---
title: 'CAtlServiceModuleT:: Start, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491663"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start, fonction

Lorsque le service est exécuté, `_tWinMain` appelle `CAtlServiceModuleT::WinMain`, qui appelle `CAtlServiceModuleT::Start`à son tour.

`CAtlServiceModuleT::Start`configure un tableau de `SERVICE_TABLE_ENTRY` structures qui mappent chaque service à sa fonction de démarrage. Ce tableau est ensuite transmis à la fonction API Win32, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). En théorie, un exe peut gérer plusieurs services et le tableau peut avoir plusieurs `SERVICE_TABLE_ENTRY` structures. À l’heure actuelle, toutefois, un service généré par ATL ne prend en charge qu’un seul service par EXE. Par conséquent, le tableau a une seule entrée qui contient le nom du `_ServiceMain` service et comme fonction de démarrage. `_ServiceMain`est une fonction membre statique de `CAtlServiceModuleT` qui appelle la fonction membre non statique,. `ServiceMain`

> [!NOTE]
>  L’échec `StartServiceCtrlDispatcher` de la connexion au gestionnaire de contrôle des services (SCM) signifie probablement que le programme ne s’exécute pas en tant que service. Dans ce cas, le programme appelle `CAtlServiceModuleT::Run` directement afin que le programme puisse s’exécuter en tant que serveur local. Pour plus d’informations sur l’exécution du programme en tant que serveur local, consultez [conseils](../atl/debugging-tips.md)de débogage.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
