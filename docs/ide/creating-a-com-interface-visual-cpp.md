---
title: Créer une interface COM
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 6ad8d50049d34a711937f3d1f73157ce26f69808
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509690"
---
# <a name="create-a-com-interface"></a>Créer une interface COM

Visual Studio propose des Assistants et des modèles permettant de créer des projets qui utilisent des interfaces de définition COM et des dispinterfaces pour vos objets COM et vos classes Automation.

Vous pouvez utiliser ces Assistants pour effectuer les trois tâches courantes ci-dessous :

- [Ajouter la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

  Ajoutez la prise en charge ATL à une application MFC après avoir créé un projet MFC à l’aide de l’[Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), puis en exécutant l’Assistant Code **Ajouter la prise en charge ATL à MFC**. Cette prise en charge s’applique uniquement aux objets simples COM ajoutés à un fichier exécutable MFC ou à un projet DLL. Ces objets ATL peuvent avoir plusieurs interfaces.

- [Créer un contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)

  Ouvrez l’[Assistant Contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) pour créer un contrôle ActiveX possédant une dispinterface et une table d’événements définies dans le fichier .idl et dans la classe de contrôle, respectivement.

- [Ajoutez un contrôle ATL](../atl/reference/adding-an-atl-control.md).

  Utilisez conjointement l’[Assistant Projet ATL](../atl/reference/atl-project-wizard.md) et l’[Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md) pour créer un contrôle ActiveX ATL.

  Vous pouvez également ajouter un contrôle ATL à un projet MFC auquel vous avez ajouté la prise en charge ATL, de la manière décrite ci-dessus. De plus, si vous sélectionnez **Contrôle ATL** dans la boîte de dialogue **Ajouter une classe** alors que vous n’avez pas encore ajouté la prise en charge ATL à votre projet MFC, Visual Studio affiche une boîte de dialogue vous invitant à confirmer l’ajout de la prise en charge ATL à votre projet MFC.

  Cet Assistant crée une source IDL et une table COM dans les classes du projet.

Si un projet ATL est ouvert, la boîte de dialogue [Ajouter une classe](./adding-a-class-visual-cpp.md#add-class-dialog-box) propose des Assistants et modèles supplémentaires pour l’ajout d’interfaces COM à votre projet. Les Assistants suivants vous permettent de définir une ou plusieurs interfaces pour l’objet :

- [Assistant composant ATL COM+ 1,0](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Assistant objet simple ATL](../atl/reference/atl-simple-object-wizard.md)
- [Assistant composant ASP ATL](../atl/reference/atl-active-server-page-component-wizard.md)
- [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md)

De plus, vous pouvez implémenter de nouvelles interfaces sur votre contrôle COM. Il vous suffit de cliquer avec le bouton droit sur la classe de contrôle de l’objet dans Affichage de classes et de choisir [Implémenter l’interface](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).

> [!NOTE]
> Visual Studio ne propose pas d’Assistant pour l’ajout d’une interface à un projet. Vous pouvez ajouter une interface à un projet ATL ou [ajouter la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) en ajoutant un objet simple à l’aide de l’[Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md). Vous pouvez également ouvrir le fichier .idl du projet et créer l’interface en tapant :

```
interface IMyInterface {
};
```

Pour plus d’informations, consultez [Implémenter une interface](../ide/implementing-an-interface-visual-cpp.md) et [Ajouter des objets et des contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ propose plusieurs moyens de consulter et [modifier les interfaces COM](#edit-a-com-interface) définies pour vos projets. [L’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) propose des icônes pour les interfaces ou dispinterfaces éventuellement définies dans un fichier .idl de votre projet C++.

Pour les classes d’objets COM ATL, l’affichage de classes lit la table COM dans la classe ATL afin d’afficher la relation entre la classe ATL et les interfaces éventuelles qu’elle implémente.

Dans l’affichage de classes et ses menus contextuels, vous pouvez utiliser les interfaces pour :

- ajouter des objets ATL à une application MFC ;
- ajouter des méthodes, des propriétés et des événements ;
- accéder directement au code d’interface d’un élément en double-cliquant sur ce dernier.

## <a name="in-this-section"></a>Contenu de cette section

- [Modifier une interface COM](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Modifier une interface COM

À l’aide des commandes du menu Affichage de classes, vous pouvez définir de nouvelles méthodes et propriétés pour les interfaces COM de vos projets Visual Studio C++. Dans la boîte à outils, vous pouvez aussi définir des événements pour les contrôles ActiveX.

Pour les classes d’objets COM basées sur ATL et MFC, vous pouvez modifier l’implémentation de classe en même temps que vous modifiez l’interface.

> [!NOTE]
> Pour les interfaces que vous avez définies en dehors de la boîte de dialogue **Ajouter une classe**, Visual C++ ajoute les méthodes ou propriétés au fichier .idl, puis des stubs aux classes qui implémentent les méthodes, même si les interfaces sont ajoutées manuellement.

Les trois Assistants suivants vous aident à personnaliser les interfaces existantes. Ils sont disponibles sous Affichage de classes :

|Assistant|Type de projet|
|------------|------------------|
|[Assistant Ajout de propriété](./adding-a-property-visual-cpp.md#names-add-property-wizard)|Projets ATL ou MFC prenant en charge ATL. Cliquez avec le bouton droit sur l’interface à laquelle vous voulez ajouter la propriété.<br /><br />Visual C++ détecte le type de projet et modifie les options de l’Assistant Ajout de propriété si nécessaire :<br /><br />-Pour les dispinterfaces des projets créés à l’aide de l' [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’appel de l’Assistant Ajout de propriété fournit des options spécifiques à MFC.<br />- Pour les interfaces de contrôle ActiveX MFC, l’Assistant Ajout de propriété fournit la liste des méthodes et propriétés stock que vous pouvez utiliser telles quelles ou personnaliser pour votre contrôle.<br />- Pour toutes les autres interfaces, l’Assistant Ajout de propriété fournit des options utiles dans la plupart des situations.|
|[Assistant Ajout de méthode](./adding-a-method-visual-cpp.md#add-method-wizard)|Projets ATL ou MFC prenant en charge ATL. Cliquez avec le bouton droit sur l’interface à laquelle vous voulez ajouter la méthode.<br /><br />Visual C++ détecte le type de projet et modifie les options de l’Assistant Ajout de méthode si nécessaire :<br /><br />- Pour les dispinterfaces de projets créés à l’aide de l’[Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’utilisation de l’Assistant Ajout de méthode fournit des options propres à MFC.<br />- Pour les interfaces de contrôle ActiveX MFC, l’Assistant Ajout de méthode fournit la liste des méthodes et propriétés stock que vous pouvez utiliser telles quelles ou personnaliser pour votre contrôle.<br />-Pour toutes les autres interfaces, les assistants **Ajouter une méthode** fournissent des options utiles dans la plupart des situations.|

De plus, vous pouvez implémenter de nouvelles interfaces sur votre contrôle COM. Il vous suffit de cliquer avec le bouton droit sur la classe de contrôle de l’objet dans Affichage de classes et de choisir [Implémenter l’interface](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).
