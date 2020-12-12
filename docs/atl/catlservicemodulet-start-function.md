---
description: 'En savoir plus sur : CAtlServiceModuleT :: Start, fonction'
title: 'CAtlServiceModuleT :: Start, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: cfdae47f88c7957a4470da3129f3d3e071614276
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148315"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT :: Start, fonction

Lorsque le service est exécuté, `_tWinMain` appelle `CAtlServiceModuleT::WinMain` , qui appelle à son tour `CAtlServiceModuleT::Start` .

`CAtlServiceModuleT::Start` configure un tableau de `SERVICE_TABLE_ENTRY` structures qui mappent chaque service à sa fonction de démarrage. Ce tableau est ensuite transmis à la fonction API Win32, [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw). En théorie, un EXE peut gérer plusieurs services et le tableau peut avoir plusieurs `SERVICE_TABLE_ENTRY` structures. À l’heure actuelle, toutefois, un service généré par ATL ne prend en charge qu’un seul service par EXE. Par conséquent, le tableau a une seule entrée qui contient le nom du service et `_ServiceMain` comme fonction de démarrage. `_ServiceMain` est une fonction membre statique de `CAtlServiceModuleT` qui appelle la fonction membre non statique, `ServiceMain` .

> [!NOTE]
> L’échec de la `StartServiceCtrlDispatcher` connexion au gestionnaire de contrôle des services (SCM) signifie probablement que le programme ne s’exécute pas en tant que service. Dans ce cas, le programme appelle `CAtlServiceModuleT::Run` directement afin que le programme puisse s’exécuter en tant que serveur local. Pour plus d’informations sur l’exécution du programme en tant que serveur local, consultez [conseils de débogage](../atl/debugging-tips.md).

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT :: Start](../atl/reference/catlservicemodulet-class.md#start)
