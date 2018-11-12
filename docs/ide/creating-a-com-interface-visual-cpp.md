---
title: Création d'une interface COM (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.creating.interfaces
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 53379a7937bd96b50de61652f67bd0dcb34a6730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569735"
---
# <a name="creating-a-com-interface-visual-c"></a>Création d'une interface COM (Visual C++)

Visual C++ propose des Assistants et modèles permettant de créer des projets qui utilisent des interfaces de définition COM et des dispinterfaces pour vos objets COM et classes Automation.

Vous pouvez utiliser ces Assistants pour accomplir les trois tâches courantes ci-dessous :

- [Ajout de la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

   Ajoute la prise en charge ATL à une application MFC après la création d’un projet MFC à l’aide de [l’Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), puis en exécutant l’Assistant Code **Ajouter la prise en charge ATL à MFC**. Cette prise en charge s’applique uniquement aux objets simples COM ajoutés à un fichier exécutable MFC ou à un projet DLL. Ces objets ATL peuvent posséder plusieurs interfaces.

- [Création d’un contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)

   Ouvre [l’Assistant Contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) pour créer un contrôle ActiveX possédant une dispinterface et une table d’événements définies dans le fichier .idl et dans la classe de contrôle, respectivement.

- [Ajout d’un contrôle ATL](../atl/reference/adding-an-atl-control.md)

   Utilise conjointement [l’Assistant Projet ATL](../atl/reference/atl-project-wizard.md) et [l’Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md) pour créer un contrôle ActiveX ATL.

   Vous pouvez également ajouter un contrôle ATL à un projet MFC auquel vous avez ajouté la prise en charge ATL, de la manière décrite ci-dessus. En outre, si vous sélectionnez **Contrôle ATL** dans la boîte de dialogue **Ajouter une classe** alors que vous n’avez pas encore ajouté la prise en charge ATL à votre projet MFC, Visual Studio affiche une boîte de dialogue vous demandant de confirmer l’ajout de la prise en charge ATL à votre projet MFC.

   Cet Assistant crée une source IDL et une table COM dans les classes du projet.

Si un projet ATL est ouvert, la boîte de dialogue [Ajouter une classe](../ide/add-class-dialog-box.md) propose des Assistants et modèles supplémentaires pour l’ajout d’interfaces COM à votre projet. Les Assistants suivants vous permettent de définir une ou plusieurs interfaces pour l’objet :

- [Assistant Composant COM+ 1.0 ATL](../atl/reference/atl-com-plus-1-0-component-wizard.md)

- [Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md)

- [Assistant Composant ASP ATL](../atl/reference/atl-active-server-page-component-wizard.md)

- [Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md)

Vous pouvez également implémenter de nouvelles interfaces sur votre contrôle COM en cliquant avec le bouton droit sur la classe de contrôle de l’objet dans l’affichage de classes et en cliquant sur [Implémenter l’interface](../ide/implement-interface-wizard.md).

> [!NOTE]
>  Visual Studio ne propose pas d’Assistant pour l’ajout d’une interface à un projet. Vous pouvez ajouter une interface à un projet ATL ou [ajouter la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) en ajoutant un objet simple à l’aide de [l’Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md). Vous pouvez également ouvrir le fichier .idl du projet et créer l’interface en tapant :

```
interface IMyInterface {
};

```

Pour plus d’informations, consultez [Implémentation d’une interface](../ide/implementing-an-interface-visual-cpp.md) et [Ajout d’objets et de contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ propose plusieurs moyens de consulter et [modifier les interfaces COM](../ide/editing-a-com-interface.md) définies pour vos projets. [L’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) propose des icônes pour les interfaces ou dispinterfaces éventuellement définies dans un fichier .idl de votre projet C++.

Pour les classes d’objets COM ATL, l’affichage de classes lit la table COM dans la classe ATL afin d’afficher la relation entre la classe ATL et les interfaces éventuelles qu’elle implémente.

Dans l’affichage de classes et ses menus contextuels, vous pouvez utiliser les interfaces pour :

- ajouter des objets ATL à une application MFC ;

- ajouter des méthodes, des propriétés et des événements ;

- accéder directement au code d’interface d’un élément en double-cliquant sur ce dernier.

## <a name="see-also"></a>Voir aussi

[Création de projets de bureau à l’aide des Assistants Application](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)