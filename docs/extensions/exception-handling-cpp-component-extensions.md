---
description: 'En savoir plus sur : gestion des exceptions (C++/CLI et C++/CX)'
title: Gestion des exceptions (C++/CLI et C++/CX)
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
ms.openlocfilehash: 73299cf8b562c3572452e6efd1e8d2fa65aff84c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155057"
---
# <a name="exception-handling--ccli-and-ccx"></a>Gestion des exceptions (C++/CLI et C++/CX)

Les applications compilées avec l’option de compilateur `/ZW` ou `/clr` utilisent des *exceptions* pour gérer des erreurs inattendues survenant lors de l’exécution du programme. Les rubriques suivantes présentent la gestion des exceptions dans des applications C++/CX ou C++/CLI.

## <a name="in-this-section"></a>Dans cette section

[Concepts de base de l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Décrit la levée d’exceptions et l’utilisation de **`try`** / **`catch`** blocs.

[Différences dans le comportement de gestion des exceptions sous/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Présente les différences par rapport au comportement standard de la gestion d’exceptions C++.

[suivie](../dotnet/finally.md)<br/>
Présente comment utiliser le mot clé finally.

[Comment : définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Présente comment sont capturées les exceptions non prises en charge.

[Comment : intercepter des exceptions dans du code natif levée à partir de MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Présente comment intercepter des exceptions CLR et C++ dans du code natif.

[Comment : définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Présente comment intercepter toutes les exceptions non prises en charge.

## <a name="related-sections"></a>Sections connexes

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
Décrit la gestion des exceptions en C++ standard.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
