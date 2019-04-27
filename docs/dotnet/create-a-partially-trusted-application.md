---
title: 'Procédure : Créer une Application partiellement approuvée (C++ / c++ / CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209120"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Procédure : Créer une Application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT

Cette rubrique explique comment créer une application partiellement approuvée de Common Language Runtime à l’aide de Visual C++ en supprimant la dépendance vis-à-vis de msvcm90.dll.

Une application Visual C++ générée avec **/CLR** ont une dépendance vis-à-vis de msvcm90.dll, qui fait partie de la bibliothèque Runtime C. Lorsque vous souhaitez que votre application à utiliser dans un environnement de confiance partielle, le CLR appliquera certaines règles de sécurité des accès de code sur votre DLL. Par conséquent, il sera nécessaire de supprimer cette dépendance puisque msvcm90.dll contient du code natif et que la stratégie de sécurité d’accès au code ne peut pas être appliquée.

Si votre application n’utilise pas toutes les fonctionnalités de la bibliothèque Runtime C et que vous souhaitez supprimer la dépendance sur cette bibliothèque à partir de votre code, vous devez utiliser le **/NODEFAULTLIB:msvcmrt.lib** option de l’éditeur de liens et créez un lien avec ptrustm.lib ou ptrustmd.lib. Ces bibliothèques contiennent des fichiers objets pour l’initialisation et désinitialisation d’une application, les classes d’exception utilisé par le code d’initialisation et le code de gestion des exceptions managées. Liaison dans une de ces bibliothèques supprimera toute dépendance vis-à-vis de msvcm90.dll.

> [!NOTE]
>  L’ordre de désinitialisation de l’assembly peut-être différer pour les applications qui utilisent les bibliothèques ptrust. Pour les applications normales, les assemblys sont habituellement déchargés dans l’ordre inverse qui ils sont chargés, mais cela n’est pas garanti. Pour les applications de confiance partielle, les assemblys sont habituellement déchargés dans le même ordre qu’ils sont chargés. Cela, en outre, n’est pas garanti.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Pour créer un niveau de confiance partiel mixte (/ clr) application

1. Pour supprimer la dépendance vis-à-vis de msvcm90.dll, vous devez spécifier à l’éditeur de liens ne pas inclure cette bibliothèque à l’aide de la **/NODEFAULTLIB:msvcmrt.lib** option de l’éditeur de liens. Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Ajoutez une des bibliothèques ptrustm aux dépendances d’entrée de l’éditeur de liens. Utilisez ptrustm.lib si vous générez votre application en mode release. Pour le mode de débogage, utilisez ptrustmd.lib. Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [. Fichiers lib en tant qu’entrée de l’éditeur de liens](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Prise en charge de bibliothèque pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Passer des options à l’Éditeur de liens)](../build/reference/link-pass-options-to-linker.md)
