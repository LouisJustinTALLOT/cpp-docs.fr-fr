---
title: CAtlServiceModuleT::Démarrer la fonction
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317279"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Démarrer la fonction

Lorsque le service `_tWinMain` est `CAtlServiceModuleT::WinMain`exécuté, les `CAtlServiceModuleT::Start`appels , qui à leur tour appelle .

`CAtlServiceModuleT::Start`met en place `SERVICE_TABLE_ENTRY` un éventail de structures qui cartographient chaque service à sa fonction de démarrage. Ce tableau est ensuite passé à la fonction Win32 API, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). En théorie, un EXE pourrait gérer plusieurs `SERVICE_TABLE_ENTRY` services et le tableau pourrait avoir plusieurs structures. À l’heure actuelle, cependant, un service généré par ATL ne prend en charge qu’un seul service par EXE. Par conséquent, le tableau dispose d’une `_ServiceMain` seule entrée qui contient le nom de service et comme la fonction de démarrage. `_ServiceMain`est une fonction `CAtlServiceModuleT` de membre statique qui appelle `ServiceMain`la fonction de membre non statique, .

> [!NOTE]
> Le `StartServiceCtrlDispatcher` fait de ne pas se connecter au gestionnaire de contrôle de service (SCM) signifie probablement que le programme ne fonctionne pas comme un service. Dans ce cas, `CAtlServiceModuleT::Run` le programme appelle directement pour que le programme puisse s’exécuter comme un serveur local. Pour plus d’informations sur l’exécution du programme comme un serveur local, voir [Debugging Tips](../atl/debugging-tips.md).

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Démarrer](../atl/reference/catlservicemodulet-class.md#start)
