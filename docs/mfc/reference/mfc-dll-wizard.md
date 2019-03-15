---
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
ms.openlocfilehash: c0c8edfd26fc6abdcef1cbb2cfa93d88f9a37cde
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822702"
---
# <a name="mfc-dll-wizard"></a>DLL MFC (Assistant)

Lorsque vous utilisez l’Assistant DLL MFC pour créer un projet DLL MFC, vous obtenez une application de démarrage pour travailler avec des fonctionnalités intégrées qui, lorsque compilées, implémentent les fonctionnalités de base d’un [DLL](../../build/dlls-in-visual-cpp.md). Le programme de démarrage MFC inclut des fichiers sources (.cpp) C++, les fichiers de ressources (.rc) et un fichier projet (.vcxproj). Le code généré dans ces fichiers de démarrage est basé sur la bibliothèque MFC. Pour plus d’informations, consultez les détails du fichier Readme.txt généré pour votre projet dans Visual Studio, et [Classes et fonctions générées par l’Assistant DLL MFC](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md)

## <a name="overview"></a>Vue d'ensemble

Cette page décrit actuel [paramètres d’application pour le projet DLL MFC](../../mfc/reference/application-settings-mfc-dll-wizard.md) que vous créez. Par défaut, le projet est créé comme un projet DLL MFC (MFC partagé) standard avec des paramètres supplémentaires.

Pour modifier ces valeurs par défaut, cliquez sur **paramètres d’Application** dans la colonne de gauche de l’Assistant et apporter des modifications dans la page de l’Assistant DLL MFC.

Après avoir créé un projet DLL MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [Assistants de code](../../ide/adding-functionality-with-code-wizards-cpp.md).

Vous pouvez effectuer les tâches et les types d’améliorations apportées à un projet DLL MFC de base suivantes :

- [Exporter à partir d’une DLL](../../build/exporting-from-a-dll.md)

- [Lier un exécutable à une DLL](../../build/linking-an-executable-to-a-dll.md)

- [Initialiser une DLL](../../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="see-also"></a>Voir aussi

[Création et gestion de projets Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)<br/>
[Définir un compilateur et les propriétés de build](../../build/working-with-project-properties.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Implémentation d’une interface](../../ide/implementing-an-interface-visual-cpp.md)<br/>
