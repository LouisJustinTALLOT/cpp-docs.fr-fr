---
title: Éviter les Exceptions levées par les objets COM générés avec /CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 687585d0b25c64f5575646de3cd4823e0a89988e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408970"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Éviter des exceptions à l'arrêt du CLR lors de l'utilisation d'objets COM générés avec /clr

Une fois que le common language runtime (CLR) entre en mode arrêt, des fonctions natives ont un accès limité aux services CLR. Lorsque vous tentez d’appeler la version sur un objet COM compilé avec **/CLR**, le CLR passe en code natif, puis revient en code managé pour répondre à l’appel IUnknown::Release (qui est définie dans le code managé). Le CLR empêche l’appel en code managé, car il est en mode arrêt.

Pour résoudre ce problème, assurez-vous que les destructeurs appelés à partir de méthodes de mise en production contiennent uniquement le code natif.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)