---
title: Domaines d’application et Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b935b9a5d1561fa1c8b961ee48b92f59b98e2bd2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704332"
---
# <a name="application-domains-and-visual-c"></a>Domaines d’application et Visual C++

Si vous avez un `__clrcall` une fonction virtuelle, la vtable sera par domaine d’application (appdomain). Si vous créez un objet dans un domaine d’application, vous pouvez uniquement appeler la fonction virtuelle à partir de cet AppDomain. En mode mixte (**/CLR**) vous devez les vtables par processus si votre type n’a pas `__clrcall` fonctions virtuelles. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Pour plus d'informations, voir :

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)