---
title: Ajouter une classe
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: b1c64505a63b8720ed7aee855f2bbbbdb9134e28
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96188833"
---
# <a name="add-a-class"></a>Ajouter une classe

Pour ajouter une classe dans un projet Visual Studio C++, dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, choisissez **Ajouter**, puis **Classe**. Cette opération ouvre la [boîte de dialogue Ajouter une classe](#add-class-dialog-box).

Quand vous ajoutez une classe, vous devez spécifier un nom différent de celui des classes qui existent déjà dans MFC ou ATL. Si vous entrez un nom qui existe déjà dans l’une des deux bibliothèques, l’IDE affiche un message d’erreur.

Si la convention de nommage de votre projet exige que vous utilisiez un nom existant, il vous suffit de modifier la casse d’une ou de plusieurs lettres du nom, car C++ respecte la casse. Par exemple, bien que vous ne puissiez pas nommer une classe `CDocument`, vous pouvez la nommer `cdocument`.

## <a name="in-this-section"></a>Dans cette section

- [Quel genre de classe voulez-vous ajouter ?](#what-kind-of-class-do-you-want-to-add)
- [Boîte de dialogue Ajouter une classe](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>Quel genre de classe voulez-vous ajouter ?

Dans la boîte de dialogue **Ajouter une classe**, quand vous développez le nœud **Visual C++** dans le volet gauche, plusieurs groupes de modèles installés sont affichés. Il s’agit notamment des groupes **CLR**, **ATL**, **MFC** et **C++**. Quand vous sélectionnez un groupe, la liste des modèles disponibles dans ce groupe s’affiche dans le volet central. Chaque modèle contient les fichiers et le code source requis pour une classe.

Pour générer une classe, sélectionnez un modèle dans le volet central, tapez un nom pour la classe dans la zone **Nom**, puis sélectionnez **Ajouter**. Cette opération entraîne l’affichage de **l’Assistant Ajouter une classe** qui vous permet de spécifier les options relatives à la classe.

- Pour plus d’informations sur la façon de créer des classes MFC, consultez [Classe MFC](../mfc/reference/adding-an-mfc-class.md).

- Pour plus d’informations sur la façon de créer des classes ATL, consultez [Objet simple ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
> Le modèle **Ajouter la prise en charge ATL à MFC** ne crée pas de classe, mais il configure le projet pour une utilisation d’ATL. Pour plus d’informations, consultez [Ajout de la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Pour créer une classe C++ qui n’utilise pas MFC, ATL ni CLR, servez-vous du modèle **Classe C++** situé dans le groupe **C++** des modèles installés. Pour plus d’informations, consultez [Ajouter une classe C++ générique](../ide/adding-a-generic-cpp-class.md).

Deux genres de classes C++ basées sur des formulaires sont disponibles. La première, la [classe CFormView](../mfc/reference/cformview-class.md), crée une classe MFC. La deuxième crée une classe CLR Windows Forms.

## <a name="add-class-dialog-box"></a>Ajouter une classe, boîte de dialogue

La boîte de dialogue **Ajouter une classe** contient des modèles qui vous permettent de :

- Ouvrir un Assistant de code correspondant, s’il est disponible. Pour plus d’informations, consultez [Ajouter une fonctionnalité avec des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- ou -

- Créer automatiquement votre classe en ajoutant les fichiers appropriés et le code source à votre projet.

Vous pouvez accéder à la boîte de dialogue **Ajouter une classe** à partir du menu **Projet**, de **l’Explorateur de solutions** ou de l’[Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Quand vous essayez d’ajouter une classe qui ne convient pas à votre projet actuel, vous recevez un message d’erreur. Sélectionnez **OK** pour revenir à la boîte de dialogue **Ajouter une classe**.

### <a name="add-class-templates"></a>Ajouter des modèles de classe

Il existe quatre catégories de modèles **Ajouter une classe** : .NET, ATL, MFC et Générique. Quand vous sélectionnez un modèle dans le volet **Modèles** , le texte décrivant votre sélection apparaît dans les volets **Catégories** et **Modèles** .

#### <a name="net"></a>.NET

|Modèle|Assistant|
|--------------|------------|
|Service Web ASP.NET|Non disponible|
|Classe Component (.NET)|Non disponible|
|Classe Installer (.NET)|Non disponible|
|Contrôle utilisateur (.NET)|Non disponible|
|Windows Form (.NET)|Non disponible|

#### <a name="atl"></a>ATL

|Modèle|Assistant|
|--------------|------------|
|Ajouter la prise en charge ATL à MFC|Non disponible|
|Contrôle ATL|[Assistant contrôle ATL](../atl/reference/atl-control-wizard.md)|
|Boîte de dialogue ATL|[Assistant Boîte de dialogue ATL](../atl/reference/atl-dialog-wizard.md)|
|Objet simple ATL|[Assistant objet simple ATL](../atl/reference/atl-simple-object-wizard.md)|
|Fournisseur d’événements WMI|Assistant Fournisseur d’événements WMI|
|Fournisseur d’instances WMI|Assistant Fournisseur d’instances WMI|

#### <a name="mfc"></a>MFC

|Modèle|Assistant|
|--------------|------------|
|Classe MFC|[Assistant Ajout de classes MFC](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>Classes génériques

|Modèle|Assistant|
|--------------|------------|
|Classe C++ générique|[Assistant classe C++ générique](./adding-a-generic-cpp-class.md#generic-c-class-wizard)|
