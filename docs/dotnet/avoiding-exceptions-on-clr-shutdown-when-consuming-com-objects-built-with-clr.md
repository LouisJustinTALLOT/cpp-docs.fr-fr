---
title: Éviter les Exceptions levées par les objets COM générés avec /CLR
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: 23af1d8b48a6579b8cc20261691c1f090dc858a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633439"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Éviter des exceptions à l'arrêt du CLR lors de l'utilisation d'objets COM générés avec /clr

Une fois que le common language runtime (CLR) entre en mode arrêt, des fonctions natives ont un accès limité aux services CLR. Lorsque vous tentez d’appeler la version sur un objet COM compilé avec **/CLR**, le CLR passe en code natif, puis revient en code managé pour répondre à l’appel IUnknown::Release (qui est définie dans le code managé). Le CLR empêche l’appel en code managé, car il est en mode arrêt.

Pour résoudre ce problème, assurez-vous que les destructeurs appelés à partir de méthodes de mise en production contiennent uniquement le code natif.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)