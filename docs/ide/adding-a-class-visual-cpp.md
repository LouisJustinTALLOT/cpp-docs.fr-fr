---
title: Ajout d'une classe (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 8cdc8dcc4241acb805255b6a28f1518e39f2bb75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429378"
---
# <a name="adding-a-class-visual-c"></a>Ajout d'une classe (Visual C++)

Pour ajouter une classe dans un projet Visual C++, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Classe**. Cette opération ouvre la [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md).

Quand vous ajoutez une classe, vous devez spécifier un nom différent de celui des classes qui existent déjà dans MFC ou ATL. Si vous entrez un nom qui existe déjà dans l’une des deux bibliothèques, l’IDE affiche un message d’erreur.

Si la convention de nommage de votre projet exige que vous utilisiez un nom existant, il vous suffit de modifier la casse d’une ou de plusieurs lettres du nom, car C++ respecte la casse. Par exemple, bien que vous ne puissiez pas nommer une classe `CDocument`, vous pouvez la nommer `cdocument`.

## <a name="what-kind-of-class-do-you-want-to-add"></a>Quel genre de classe voulez-vous ajouter ?

Dans la boîte de dialogue **Ajouter une classe**, quand vous développez le nœud **Visual C++** dans le volet gauche, plusieurs groupes de modèles installés sont affichés. Il s’agit notamment des groupes **CLR**, **ATL**, **MFC** et **C++**. Quand vous sélectionnez un groupe, la liste des modèles disponibles dans ce groupe s’affiche dans le volet central. Chaque modèle contient les fichiers et le code source requis pour une classe.

Pour générer une classe, sélectionnez un modèle dans le volet central, tapez un nom pour la classe dans la zone **Nom**, puis cliquez sur **Ajouter**. Cette opération entraîne l’affichage de **l’Assistant Ajouter une classe** qui vous permet de spécifier les options relatives à la classe.

- Pour plus d’informations sur la création de classes MFC, consultez [Classe MFC](../mfc/reference/adding-an-mfc-class.md).

- Pour plus d’informations sur la création de classes ATL, consultez [Objet simple ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
>  Le modèle **Ajouter la prise en charge ATL à MFC** ne crée pas de classe, mais il configure le projet pour une utilisation d’ATL. Pour plus d’informations, consultez [Ajout de la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Pour créer une classe C++ qui n’utilise pas MFC, ATL ni CLR, servez-vous du modèle **Classe C++** situé dans le groupe **C++** des modèles installés. Pour plus d’informations, consultez [Ajout d’une classe C++ générique](../ide/adding-a-generic-cpp-class.md).

Deux genres de classes C++ basées sur des formulaires sont disponibles. La première, la [classe CFormView](../mfc/reference/cformview-class.md) crée une classe MFC. La deuxième crée une classe CLR Windows Forms.

## <a name="see-also"></a>Voir aussi

[Création d’une application MFC basée sur les formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md)<br>
[Boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md)<br>
[Création de projets de bureau à l’aide des Assistants Application](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)