---
description: 'En savoir plus sur : Assistant DLL MFC'
title: DLL MFC (Assistant)
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.overview
helpviewer_keywords:
- MFC DLLs [MFC], creating
- MFC DLL Wizard
- DLLs [MFC], MFC
- DLL wizard [MFC]
- MFC DLLs [MFC]
- DLLs [MFC], creating
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
ms.openlocfilehash: 0f786255c22e644335c5154e0f14add59a2a418a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219159"
---
# <a name="mfc-dll-wizard"></a>DLL MFC (Assistant)

Lorsque vous utilisez l’Assistant DLL MFC pour créer un projet DLL MFC, vous bénéficiez d’une application de démarrage opérationnelle avec des fonctionnalités intégrées qui, une fois compilées, implémenteront les fonctionnalités de base d’une [dll](../../build/dlls-in-visual-cpp.md). Le programme de démarrage MFC comprend des fichiers sources C++ (. cpp), des fichiers de ressources (. RC) et un fichier projet (. vcxproj). Le code généré dans ces fichiers de démarrage est basé sur MFC. Pour plus d’informations, consultez les détails de fichier dans Readme.txt générés pour votre projet dans Visual Studio, ainsi que les [classes et fonctions générées par l’Assistant DLL MFC](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md) .

## <a name="overview"></a>Vue d’ensemble

Cette page de l’Assistant décrit les [paramètres d’application actuels pour le projet DLL MFC](../../mfc/reference/application-settings-mfc-dll-wizard.md) que vous créez. Par défaut, le projet est créé en tant que projet DLL MFC standard (MFC partagé) sans paramètres supplémentaires.

Pour modifier ces valeurs par défaut, cliquez sur paramètres de l' **application** dans la colonne de gauche de l’Assistant et apportez des modifications dans cette page de l’Assistant DLL MFC.

Après avoir créé un projet DLL MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [assistants code](../../ide/adding-functionality-with-code-wizards-cpp.md).

Vous pouvez effectuer les tâches et types d’améliorations suivants dans un projet DLL MFC de base :

- [Exporter à partir d’une DLL](../../build/exporting-from-a-dll.md)

- [Lier un exécutable à une DLL](../../build/linking-an-executable-to-a-dll.md)

- [Initialiser une DLL](../../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)<br/>
[Définir des propriétés de build et de compilateur](../../build/working-with-project-properties.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Implémentation d’une interface](../../ide/implementing-an-interface-visual-cpp.md)<br/>
