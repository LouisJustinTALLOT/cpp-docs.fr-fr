---
description: 'En savoir plus sur : domaines d’application et Visual C++'
title: Domaines d'application et Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 55f02aec7b3b2d23f10ae9142dba7c61ff60683f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282820"
---
# <a name="application-domains-and-visual-c"></a>Domaines d’application et Visual C++

Si vous avez une `__clrcall` fonction virtuelle, la vtable sera par domaine d’application (AppDomain). Si vous créez un objet dans un AppDomain, vous pouvez uniquement appeler la fonction virtuelle à partir de cet AppDomain. En mode mixte (**/CLR**), vous obtiendrez des vtables par processus si votre type n’a pas de `__clrcall` fonctions virtuelles. Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Pour plus d'informations, consultez les pages suivantes :

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [traiter](../cpp/process.md)

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
