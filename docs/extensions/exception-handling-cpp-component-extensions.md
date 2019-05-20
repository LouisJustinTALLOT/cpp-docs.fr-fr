---
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
ms.openlocfilehash: b477f7355ee1f4f70a0ad3df8b85c4276c07d397
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516574"
---
# <a name="exception-handling--ccli-and-ccx"></a>Gestion des exceptions (C++/CLI et C++/CX)

Les applications compilées avec l’option de compilateur `/ZW` ou `/clr` utilisent des *exceptions* pour gérer des erreurs inattendues survenant lors de l’exécution du programme. Les rubriques suivantes présentent la gestion des exceptions dans des applications C++/CX ou C++/CLI.

## <a name="in-this-section"></a>Dans cette section

[Concepts de base dans l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Décrit la génération d’exceptions et l’utilisation de blocs **try**/**catch**.

[Différences du comportement de gestion des exceptions dans /clr](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Présente les différences par rapport au comportement standard de la gestion d’exceptions C++.

[finally](../dotnet/finally.md)<br/>
Présente comment utiliser le mot clé finally.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Présente comment sont capturées les exceptions non prises en charge.

[Guide pratique pour intercepter des exceptions en code natif levées à partir de MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Présente comment intercepter des exceptions CLR et C++ dans du code natif.

[Guide pratique pour définir et installer un gestionnaire d’exceptions global](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Présente comment intercepter toutes les exceptions non prises en charge.

## <a name="related-sections"></a>Rubriques connexes

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
Décrit la gestion des exceptions en C++ standard.

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)