---
title: Domaines d'application et Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 2296654e6935bc40f301226b184cf34f77cb126d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539267"
---
# <a name="application-domains-and-visual-c"></a>Domaines d’application et Visual C++

Si vous avez un `__clrcall` fonction virtuelle, la vtable sera par domaine d’application (appdomain). Si vous créez un objet dans un appdomain, vous pouvez uniquement appeler la fonction virtuelle à partir de cet AppDomain. En mode mixte (**/CLR**) avoir par processus vtable si votre type n’a pas `__clrcall` fonctions virtuelles. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Pour plus d'informations, voir :

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)