---
title: "Mixte (natifs et managés) assemblys | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aeb0a4f21487d9d230c72bfbfc6a06928455dfe2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-native-and-managed-assemblies"></a>Assemblys mixtes (natif et managé)
Assemblys mixtes sont capables de contenir des instructions machine non managées et des instructions MSIL. Cela leur permet d’appeler et d’être appelé par les composants de .NET, tout en conservant la compatibilité avec les composants qui ne sont pas entièrement gérés. À l’aide d’assemblys mixtes, les développeurs peuvent créer des applications à l’aide d’un mélange de fonctionnalités managées et non managées. Assemblys mixtes sont donc la solution idéale pour la migration d’applications Visual C++ existantes vers la plateforme .NET.  
  
 Par exemple, une application existante entièrement composée de fonctions non managées peut mises à la plateforme .NET en recompilant simplement un module avec le **/CLR** commutateur du compilateur. Ce module est en mesure d’utiliser les fonctionnalités de .NET, mais reste compatible avec le reste de l’application. De cette façon, une application peut être convertie vers la plateforme .NET de façon progressive, élément par élément. Il est même possible de choisir entre la fonction par fonction une compilation managée et non managées dans le même fichier (consultez [managé, non managé](../preprocessor/managed-unmanaged.md)).  
  
 Visual C++ prend en charge la génération de trois types distincts d’assemblys managés : mixte, pure et vérifiable. Les deux derniers sont traités dans [Code pur et vérifiable (C + c++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : migrer vers/CLR](../dotnet/how-to-migrate-to-clr.md)  
 Décrit les étapes recommandées pour introduire ou la mise à niveau des fonctionnalités .NET dans votre application.  
  
 [Comment : compiler MFC et ATL Code à l’aide de /clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 Explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.  
  
 [Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)  
 Décrit le problème de « verrouillage du chargeur » et les solutions.  
  
 [Prise en charge de bibliothèque pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)  
 Explique comment utiliser des bibliothèques natives dans **/CLR** compilations.  
  
 [Considérations sur les performances](../dotnet/performance-considerations-for-interop-cpp.md)  
 Décrit les conséquences sur les performances des assemblys mixtes et le marshaling de données.  
  
 [Domaines d’application et Visual C++](../dotnet/application-domains-and-visual-cpp.md)  
 Décrit la prise en charge de Visual C++ pour les domaines d’application.  
  
 [Double médiateur](../dotnet/double-thunking-cpp.md)  
 Explique les implications en matière de performances d’un point d’entrée natif pour une fonction managée.  
  
 [Éviter des Exceptions CLR arrêt lors de la consommation d’objets COM générés avec /clr](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 Explique comment garantir l’arrêt correct d’une application managée qui consomme un objet COM compilé avec **/CLR**.  
  
 [Guide pratique pour créer une application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT](../dotnet/create-a-partially-trusted-application.md)  
 Explique comment créer une application partiellement approuvée de Common Language Runtime à l’aide de Visual C++ en supprimant la dépendance vis-à-vis de msvcm90.dll.  
  
 Pour plus d’informations sur les instructions de codage pour les assemblys mixtes, consultez l’article MSDN « Une vue d’ensemble de Managed/Unmanaged interopérabilité du Code » à [http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp).  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)