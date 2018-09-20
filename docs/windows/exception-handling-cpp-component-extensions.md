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
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2213266d281933c6a6a59775584532acaeb39d6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412317"
---
# <a name="exception-handling--c-component-extensions"></a>Gestion des exceptions (extensions du composant C++)

Les applications compilées avec le `/ZW` option du compilateur ou `/clr` option du compilateur utilisent tous deux *exceptions* pour gérer les erreurs inattendues pendant l’exécution du programme. Les rubriques suivantes décrivent la gestion des exceptions dans soit C + c++ / CX ou c++ / applications de l’interface CLI.

## <a name="in-this-section"></a>Dans cette section

[Concepts de base dans l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Décrit la levée d’exceptions et à l’aide de **essayez**/**catch** blocs.

[Différences de comportement sous/CLR de la gestion des exceptions](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
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
Décrit la gestion des exceptions dans C++.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)