---
title: 'Comment : créer une Application partiellement approuvée (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4a0a4b8b1045a9107158c6e67ecdfa7939b6a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108996"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Comment : créer une application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT
Cette rubrique explique comment créer une application partiellement approuvée de Common Language Runtime à l’aide de Visual C++ en supprimant la dépendance vis-à-vis de msvcm90.dll.  
  
 Une application Visual C++ construite avec **/CLR** auront une dépendance vis-à-vis de msvcm90.dll, qui fait partie de la bibliothèque Runtime C. Lorsque vous souhaitez que votre application à utiliser dans un environnement de confiance partielle, le CLR activera certaines règles de sécurité de l’accès de code sur votre DLL. Par conséquent, il sera nécessaire de supprimer cette dépendance puisque msvcm90.dll contient du code natif et que la stratégie de sécurité d’accès au code ne peut pas être appliquée.  
  
 Si votre application n’utilise pas toutes les fonctionnalités de la bibliothèque Runtime C et que vous souhaitez supprimer la dépendance sur cette bibliothèque à partir de votre code, vous devez utiliser le **/NODEFAULTLIB:msvcmrt.lib** option de l’éditeur de liens et des liens avec ptrustm.lib ou ptrustmd.lib. Ces bibliothèques contiennent des fichiers objets pour l’initialisation et la désinitialisation d’une application, les classes d’exception utilisé par le code d’initialisation et le code de gestion des exceptions managées. Liaison de l’une de ces bibliothèques supprimera toute dépendance vis-à-vis de msvcm90.dll.  
  
> [!NOTE]
>  L’ordre de désinitialisation des assemblys peut-être différer pour les applications qui utilisent les bibliothèques ptrust. Pour les applications normales, les assemblys sont habituellement déchargés dans l’ordre inverse de leur chargement, mais cela n’est pas garanti. Pour les applications de confiance partielle, les assemblys sont habituellement déchargés dans le même ordre qu’ils sont chargés. Cette opération, en outre, n’est pas garantie.  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Pour créer un niveau de confiance partiel mixte (/ clr) application  
  
1.  Pour supprimer la dépendance vis-à-vis de msvcm90.dll, vous devez spécifier à l’éditeur de liens ne pas inclure cette bibliothèque à l’aide de la **/NODEFAULTLIB:msvcmrt.lib** option de l’éditeur de liens. Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [/NODEFAULTLIB (ignorer les bibliothèques)](../build/reference/nodefaultlib-ignore-libraries.md).  
  
2.  Ajoutez l’une des bibliothèques ptrustm aux dépendances d’entrée de l’éditeur de liens. Utilisez ptrustm.lib si vous générez votre application en mode release. Pour le mode de débogage, utilisez ptrustmd.lib. Pour plus d’informations sur la façon de procéder à l’aide de l’environnement de développement Visual Studio ou par programme, consultez [. LIB des fichiers en tant qu’entrée de l’éditeur de liens](../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)   
 [Prise en charge pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)   
 [/link (Passer des options à l’Éditeur de liens)](../build/reference/link-pass-options-to-linker.md)   
