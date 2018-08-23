---
title: Gestion des exceptions (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling, managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- managed exceptions
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 566ed55df84accef0c3e5308e750a2684c36b91c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606792"
---
# <a name="exception-handling--c-component-extensions"></a>Gestion des exceptions (extensions du composant C++)

Les applications compilées avec le `/ZW` option du compilateur ou `/clr` option du compilateur utilisent tous deux *exceptions* pour gérer les erreurs inattendues pendant l’exécution du programme. Les rubriques suivantes décrivent la gestion des exceptions dans soit C + c++ / CX ou c++ / applications de l’interface CLI.

## <a name="in-this-section"></a>Dans cette section

[Concepts de base dans l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
Décrit la levée d’exceptions et à l’aide de **essayez**/**catch** blocs.

[Différences de comportement sous/CLR de la gestion des exceptions](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
Décrit les différences du comportement standard de gestion des exceptions C++.

[finally](../dotnet/finally.md)  
Explique comment utiliser le mot clé finally.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Montre comment non prise en charge des exceptions peuvent être capturées.

[Guide pratique pour intercepter des exceptions en code natif levées à partir de MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
Explique comment intercepter des exceptions CLR et C++ en code natif.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Montre comment intercepter des exceptions non gérées.

## <a name="related-sections"></a>Rubriques connexes

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)  
Décrit la gestion des exceptions dans C++.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)