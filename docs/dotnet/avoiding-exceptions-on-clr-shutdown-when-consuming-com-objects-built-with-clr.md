---
title: Éviter les Exceptions levées par les objets COM générés avec - clr | Documents Microsoft
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
ms.openlocfilehash: 0efd2af7eb4bf8a70bff983d627f802f1976c6ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103510"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Éviter des exceptions à l'arrêt du CLR lors de l'utilisation d'objets COM générés avec /clr
Une fois que le common language runtime (CLR) entre en mode arrêt, les fonctions natives ont un accès limité aux services CLR. Lorsque vous tentez d’appeler Release sur un objet COM compilé avec **/CLR**, le CLR passe en code natif, puis revient en code managé pour répondre à l’appel IUnknown::Release (qui est définie dans le code managé). Le CLR empêche l’appel en code managé, car il est en mode arrêt.  
  
 Pour résoudre ce problème, assurez-vous que destructeurs appelés à partir des méthodes de mise en production ne doivent contenir du code natif.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)