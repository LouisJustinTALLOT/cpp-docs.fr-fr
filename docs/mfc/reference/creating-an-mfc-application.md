---
description: 'En savoir plus sur : création d’une application MFC'
title: Création d'une application MFC
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 3e6541c8887f3278ac2706cb5e5cc733857e7e90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343296"
---
# <a name="creating-an-mfc-application"></a>Création d'une application MFC

Une application MFC est une application exécutable pour Windows qui se base sur la bibliothèque MFC (Microsoft Foundation Class). Les exécutables MFC se décomposent généralement en cinq types : les applications Windows standard, les boîtes de dialogue, les applications basées sur les formulaires, les applications de style Explorateur et les applications de style navigateur Web. Pour plus d'informations, consultez les pages suivantes :

- [Utilisation des classes pour l'écriture d'applications Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Création et affichage de boîtes de dialogue](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Création d’une application Forms-Based MFC](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Création d’un fichier Explorer-Style application MFC](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Création d’une application Web Browser-Style MFC](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

L'Assistant Application MFC génère les classes et fichiers appropriés pour n'importe lequel de ces types d'applications, en fonction des options sélectionnées dans l'Assistant.

Le moyen le plus simple de créer une application MFC consiste à utiliser l’Assistant Application MFC (projet d’application **MFC** dans Visual Studio 2019). Pour créer une application console MFC (un programme de ligne de commande qui utilise des bibliothèques MFC, mais qui s’exécute dans la fenêtre de console), utilisez l’Assistant de bureau Windows et choisissez l' **application console** et les options des **en-têtes MFC** .

::: moniker range=">=msvc-160"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Pour créer un formulaire MFC ou une application basée sur une boîte de dialogue

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Entrez « MFC » dans la zone de recherche, puis choisissez **application MFC** dans la liste des résultats.
1. Modifiez les valeurs par défaut en fonction des besoins, puis appuyez sur **créer** pour ouvrir l' **Assistant Application MFC**.
1. Modifiez les valeurs de configuration en fonction des besoins, puis cliquez sur **Terminer**.

Pour plus d’informations, consultez [création d’une Forms-Based application MFC](creating-a-forms-based-mfc-application.md).

![Capture d’écran de l’Assistant Application MFC dans Visual Studio 2019.](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Pour créer une application console MFC

Une application console MFC est un programme de ligne de commande qui utilise des bibliothèques MFC, mais qui s’exécute dans la fenêtre de console.

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Entrez « Bureau » dans la zone de recherche, puis choisissez **Assistant Bureau Windows** dans la liste des résultats.
1. Modifiez le nom du projet si nécessaire, puis appuyez sur **suivant** pour ouvrir l' **Assistant du bureau Windows**.
1. Cochez la case **en-têtes MFC** et définissez d’autres valeurs en fonction des besoins, puis cliquez sur **Terminer**.

![Capture d’écran de l’Assistant de bureau Windows dans Visual Studio 2019.](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=msvc-150"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Pour créer un formulaire MFC ou une application basée sur une boîte de dialogue

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Sous les modèles **installés** , choisissez **Visual C++**  >  **MFC/ATL**. Si vous ne les voyez pas, utilisez la Visual Studio Installer pour les ajouter.
1. Choisissez **application MFC** dans le volet central.
1. Modifiez les valeurs de configuration en fonction des besoins, puis cliquez sur **Terminer**.

Pour plus d’informations, consultez [création d’une Forms-Based application MFC](creating-a-forms-based-mfc-application.md).

![Capture d’écran de l’Assistant Application MFC dans Visual Studio 2017.](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Pour créer une application console MFC

Une application console MFC est un programme de ligne de commande qui utilise des bibliothèques MFC, mais qui s’exécute dans la fenêtre de console.

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Sous les modèles **installés** , choisissez **Visual C++** > **Bureau Windows**.
1. Choisissez **Windows Desktop Wizard** dans le volet central.
1. Modifiez le nom du projet en fonction des besoins, puis appuyez sur **OK** pour ouvrir l' **Assistant du bureau Windows**.
1. Cochez la case **en-têtes MFC** et définissez d’autres valeurs en fonction des besoins, puis cliquez sur **Terminer**.

![Capture d’écran de l’Assistant de bureau Windows dans Visual Studio 2017.](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=msvc-140"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Pour créer un formulaire MFC ou une application basée sur une boîte de dialogue

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Sous les modèles **installés** , choisissez **Visual C++** > **MFC**.
1. Choisissez **application MFC** dans le volet central.
1. Cliquez sur **suivant** pour démarrer l' **Assistant Application MFC**.

Pour plus d’informations, consultez [création d’une Forms-Based application MFC](creating-a-forms-based-mfc-application.md).

![Capture d’écran de l’Assistant Application MFC dans Visual Studio 2015.](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>Pour créer une application console MFC

Une application console MFC est un programme de ligne de commande qui utilise des bibliothèques MFC, mais qui s’exécute dans la fenêtre de console.

1. Dans le menu principal, choisissez **fichier** > **nouveau** > **projet**.
1. Sous les modèles **installés** , choisissez **Visual C++** > **Win32**.
1. Choisissez **application console Win32** dans le volet central.
1. Modifiez le nom du projet si nécessaire, puis cliquez sur **OK**.
1. Dans la deuxième page de l’Assistant, activez la case à cocher **Ajouter des en-têtes communs pour MFC** et définissez d’autres valeurs si nécessaire, puis cliquez sur **Terminer**.

::: moniker-end

Une fois votre projet créé, vous pouvez visualiser les fichiers créés dans l’**Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)
