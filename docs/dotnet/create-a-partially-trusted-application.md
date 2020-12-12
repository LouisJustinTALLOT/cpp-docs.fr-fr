---
description: 'En savoir plus sur : Comment : créer une application partiellement approuvée en supprimant la dépendance sur la DLL de bibliothèque CRT'
title: 'Comment : créer une application de confiance partielle (C++/CLI)'
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
ms.openlocfilehash: 937262595df4415d5620b60d9ccd8c17a6c44abf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124278"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Comment : créer une application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT

Cette rubrique explique comment créer une application du Common Language Runtime d’un niveau de confiance partiel à l’aide de Visual C++ en supprimant la dépendance sur msvcm90.dll.

Une application Visual C++ générée avec **/CLR** aura une dépendance sur msvcm90.dll, qui fait partie de la bibliothèque Runtime C. Lorsque vous souhaitez que votre application soit utilisée dans un environnement de confiance partielle, le CLR applique certaines règles de sécurité d’accès du code à votre DLL. Par conséquent, il est nécessaire de supprimer cette dépendance, car msvcm90.dll contient du code natif et la stratégie de sécurité d’accès du code ne peut pas être appliquée à celle-ci.

Si votre application n’utilise aucune des fonctionnalités de la bibliothèque Runtime C et que vous souhaitez supprimer la dépendance de cette bibliothèque de votre code, vous devez utiliser l’option de l’éditeur de liens **/NODEFAULTLIB : msvcmrt. lib** et établir un lien avec ptrustm. lib ou ptrustmd. lib. Ces bibliothèques contiennent des fichiers objets pour l’initialisation et la désinitialisation d’une application, des classes d’exception utilisées par le code d’initialisation et du code de gestion des exceptions managées. La liaison de l’une de ces bibliothèques supprimera toute dépendance sur msvcm90.dll.

> [!NOTE]
> L’ordre de désinitialisation de l’assembly peut être différent pour les applications qui utilisent les bibliothèques ptrust. Pour les applications normales, les assemblys sont généralement déchargés dans l’ordre inverse de leur chargement, mais cela n’est pas garanti. Pour les applications de confiance partielle, les assemblys sont généralement déchargés dans le même ordre que celui dans lequel ils sont chargés. Cela n’est pas non plus garanti.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Pour créer une application mixte (/CLR) partiellement approuvée

1. Pour supprimer la dépendance sur msvcm90.dll, vous devez spécifier à l’éditeur de liens de ne pas inclure cette bibliothèque à l’aide de l’option de l’éditeur de liens **/NODEFAULTLIB : msvcmrt. lib** . Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [/NODEFAULTLIB (ignorer les bibliothèques)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Ajoutez l’une des bibliothèques ptrustm aux dépendances d’entrée de l’éditeur de liens. Utilisez ptrustm. lib si vous générez votre application en mode release. Pour le mode débogage, utilisez ptrustmd. lib. Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [. Fichiers lib en tant qu’entrée dans l’éditeur de liens](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Prise en charge des bibliothèques pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/Link (passer des options à l’éditeur de liens)](../build/reference/link-pass-options-to-linker.md)
