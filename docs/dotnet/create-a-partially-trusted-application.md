---
title: 'Comment : Créer une application partiellement fiable (C/CLI)'
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
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364400"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Comment : créer une application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT

Ce sujet traite de la façon de créer une application common Language Runtime partiellement fiable à l’aide de Visual CM en supprimant la dépendance à l’égard de msvcm90.dll.

Une application Visual CMMD construite avec **/clr** aura une dépendance à l’égard de msvcm90.dll, qui fait partie de la bibliothèque C-Runtime. Lorsque vous souhaitez que votre application soit utilisée dans un environnement de confiance partiel, le CLR appliquera certaines règles de sécurité d’accès au code sur votre DLL. Par conséquent, il sera nécessaire de supprimer cette dépendance parce que msvcm90.dll contient du code indigène et la politique de sécurité d’accès au code ne peut pas être appliquée sur elle.

Si votre application n’utilise aucune fonctionnalité de la bibliothèque C-Runtime et que vous souhaitez supprimer la dépendance à cette bibliothèque de votre code, vous devrez utiliser l’option **/NODEFAULTLIB:msvcmrt.lib** linker et un lien avec ptrustm.lib ou ptrustmd.lib. Ces bibliothèques contiennent des fichiers d’objets pour l’initialisation et l’uninitialisation d’une application, des classes d’exception utilisées par le code d’initialisation et un code de traitement des exceptions géré. Lier dans l’une de ces bibliothèques éliminera toute dépendance à l’égard de msvcm90.dll.

> [!NOTE]
> L’ordre d’assemblage de l’uninitialisation peut différer pour les applications qui utilisent les bibliothèques de ptrust. Pour les applications normales, les assemblages sont généralement déchargés dans l’ordre inverse qu’ils sont chargés, mais ce n’est pas garanti. Pour les applications partielles en fiducie, les assemblages sont généralement déchargés dans le même ordre qu’ils sont chargés. Cela, aussi, n’est pas garanti.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Pour créer une application mixte (/clr) partiellement fiable

1. Pour supprimer la dépendance à l’égard de msvcm90.dll, vous devez spécifier au linker de ne pas inclure cette bibliothèque en utilisant l’option **/NODEFAULTLIB:msvcmrt.lib** linker. Pour plus d’informations sur la façon de le faire en utilisant l’environnement de développement Visual Studio ou programmatiquement, voir [/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Ajoutez l’une des bibliothèques ptrustm aux dépendances d’entrée de liaison. Utilisez ptrustm.lib si vous construisez votre application en mode version. Pour le mode débogé, utilisez ptrustmd.lib. Pour plus d’informations sur la façon de le faire en utilisant l’environnement de développement Visual Studio ou programmatique, voir [. Fichiers Lib comme Linker Input](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Initialisation des assemblées mixtes](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Prise en charge de bibliothèque pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Passer des options à l'Éditeur de liens)](../build/reference/link-pass-options-to-linker.md)
