---
description: 'En savoir plus sur : éviter des exceptions lors de l’arrêt du CLR lors de l’utilisation d’objets COM générés avec/CLR'
title: Éviter les exceptions levées par les objets COM générés avec-CLR
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: 899f7905aafcf1bff92e37ee70253e74759b3f57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282612"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Éviter des exceptions à l'arrêt du CLR lors de l'utilisation d'objets COM générés avec /clr

Une fois que le common language runtime (CLR) passe en mode arrêt, les fonctions natives ont un accès limité aux services CLR. Quand vous tentez d’appeler Release sur un objet COM compilé avec **/CLR**, le CLR passe au code natif, puis revient dans le code managé pour traiter l’appel IUnknown :: Release (qui est défini dans le code managé). Le CLR empêche le rappel dans le code managé, car il est en mode arrêt.

Pour résoudre ce code, assurez-vous que les destructeurs appelés à partir des méthodes de mise en sortie contiennent uniquement du code natif.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
