---
title: Gestion des exceptions (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: 8886480b6f4497d042c6dd79dc2215887b84fceb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505025"
---
# <a name="exception-handling--ccli-and-ccx"></a>Gestion des exceptions (C++ / c++ / CLI et c++ / CX)

Les applications compilées avec le `/ZW` option du compilateur ou `/clr` option du compilateur utilisent tous deux *exceptions* pour gérer les erreurs inattendues pendant l’exécution du programme. Les rubriques suivantes décrivent la gestion des exceptions dans soit C + c++ / CX ou c++ / applications de l’interface CLI.

## <a name="in-this-section"></a>Dans cette section

[Concepts de base dans l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Décrit la levée d’exceptions et à l’aide de **essayez**/**catch** blocs.

[Différences dans l’Exception comportement gestion sous /clr](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Décrit les différences du comportement standard de gestion des exceptions C++.

[finally](../dotnet/finally.md)<br/>
Explique comment utiliser le mot clé finally.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Montre comment non prise en charge des exceptions peuvent être capturées.

[Guide pratique pour intercepter des exceptions en code natif levées à partir de MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Explique comment intercepter des exceptions CLR et C++ en code natif.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Montre comment intercepter des exceptions non gérées.

## <a name="related-sections"></a>Rubriques connexes

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
Décrit la gestion des exceptions dans C++ standard.

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)