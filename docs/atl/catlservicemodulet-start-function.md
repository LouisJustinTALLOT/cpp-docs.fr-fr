---
title: CAtlServiceModuleT::Start, fonction
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 204d02a1122ee78b38850bedae5f98b1f338ab1d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816280"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Start, fonction

Lorsque le service est exécuté, `_tWinMain` appels `CAtlServiceModuleT::WinMain`, qui appelle à son tour `CAtlServiceModuleT::Start`.

`CAtlServiceModuleT::Start` définit un tableau de `SERVICE_TABLE_ENTRY` structures qui mappe chaque service à sa fonction de démarrage. Ce tableau est ensuite passé à la fonction API Win32, [StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera). En théorie, un EXE pourrait traiter plusieurs services et le tableau peut avoir plusieurs `SERVICE_TABLE_ENTRY` structures. Actuellement, toutefois, un service généré par ATL prend en charge qu’un seul service par EXE. Par conséquent, le tableau a une seule entrée qui contient le nom du service et `_ServiceMain` en tant que la fonction de démarrage. `_ServiceMain` est une fonction membre statique de `CAtlServiceModuleT` qui appelle la fonction membre non statique, `ServiceMain`.

> [!NOTE]
>  Échec de `StartServiceCtrlDispatcher` pour se connecter au contrôle de service manager (SCM) signifie probablement que le programme n’est pas en cours d’exécution en tant que service. Dans ce cas, le programme appelle `CAtlServiceModuleT::Run` directement afin que le programme peut s’exécuter comme un serveur local. Pour plus d’informations sur l’exécution du programme en tant qu’un serveur local, consultez [conseils de débogage](../atl/debugging-tips.md).

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
