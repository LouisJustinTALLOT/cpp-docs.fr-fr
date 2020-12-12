---
description: 'En savoir plus sur : chargement de toutes les importations pour une DLL Delay-Loaded'
title: Chargement de toutes les importations pour une DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: 0f1334f30568e4722bd97579145ddcae9851b901
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190917"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Chargement de toutes les importations pour une DLL à chargement différé

La fonction **__HrLoadAllImportsForDll** , qui est définie dans delayhlp. cpp, indique à l’éditeur de liens de charger toutes les importations à partir d’une DLL spécifiée avec l’option de l’éditeur de liens [/delayload](delayload-delay-load-import.md) .

Le chargement de toutes les importations vous permet de placer la gestion des erreurs à un seul emplacement dans votre code et de ne pas avoir à utiliser la gestion des exceptions autour des appels réels aux importations. Cela évite également une situation dans laquelle votre application échoue partiellement par le biais d’un processus suite à un échec du chargement d’une importation par le code d’assistance.

L’appel de **__HrLoadAllImportsForDll** ne modifie pas le comportement des raccordements et la gestion des erreurs ; Pour plus d’informations [, consultez Gestion des erreurs et notification](error-handling-and-notification.md) .

Le nom de la DLL passé à **__HrLoadAllImportsForDll** est comparé au nom stocké à l’intérieur de la dll et respecte la casse.

L’exemple suivant montre comment appeler **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
