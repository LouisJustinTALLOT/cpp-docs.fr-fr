---
title: Chargement de toutes les importations pour une DLL à chargement différé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ef1c576af7930e157dafd0f57bf0b8dff49fa6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715583"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Chargement de toutes les importations pour une DLL à chargement différé

Le **__HrLoadAllImportsForDll** (fonction), qui est définie dans delayhlp.cpp, indique à l’éditeur de liens charger toutes les importations à partir d’une DLL qui a été spécifiée avec la [/delayload](../../build/reference/delayload-delay-load-import.md) option de l’éditeur de liens.

Chargement de toutes les importations vous permet placer au même endroit dans votre code de gestion des erreurs et sans devoir utiliser des exceptions autour des appels réels pour les importations. Il permet également d’éviter une situation où votre application échoue partiellement via un processus à la suite du code d’assistance ne parvient pas à charger une importation.

Appel **__HrLoadAllImportsForDll** ne modifie pas le comportement des raccordements et erreurs de gestion des ; consultez [Notification et gestion des erreurs](../../build/reference/error-handling-and-notification.md) pour plus d’informations.

Le nom de la DLL passé à **__HrLoadAllImportsForDll** est comparé à celui stocké à l’intérieur de la DLL proprement dite et respecte la casse.

L’exemple suivant montre comment appeler **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)