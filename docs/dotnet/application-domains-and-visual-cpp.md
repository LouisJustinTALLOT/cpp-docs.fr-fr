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
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208797"
---
# <a name="application-domains-and-visual-c"></a>Domaines d’application et Visual C++

Si vous avez une fonction virtuelle `__clrcall`, la vtable sera par domaine d’application (AppDomain). Si vous créez un objet dans un AppDomain, vous pouvez uniquement appeler la fonction virtuelle à partir de cet AppDomain. En mode mixte ( **/CLR**), vous obtiendrez des vtables par processus si votre type n’a pas de fonctions virtuelles `__clrcall`. Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Pour plus d'informations, consultez les pages suivantes :

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Voir aussi

- [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
