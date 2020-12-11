---
description: 'En savoir plus sur : test du contrôle ATL DHTML'
title: Test du contrôle ATL DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
ms.openlocfilehash: d9e82b609b4bb9346f3db983e9734fd732ec422f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157332"
---
# <a name="testing-the-atl-dhtml-control"></a>Test du contrôle ATL DHTML

Une fois que vous avez créé votre projet, vous pouvez générer et tester l’exemple de contrôle. Avant cela, utilisez **affichage de classes** et **Explorateur de solutions** pour examiner le projet. Les éléments de votre projet sont décrits plus en détail dans [identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="to-build-and-test-the-atl-dhtml-control"></a>Pour générer et tester le contrôle ATL DHTML

1. Créez le projet. Dans le menu **Générer**, cliquez sur **Générer la solution**.

1. Une fois la génération terminée, ouvrez le **conteneur de test**. Pour plus d’informations sur l’accès à un **conteneur de test**, consultez Test des [Propriétés et des événements avec le conteneur](../mfc/testing-properties-and-events-with-test-container.md) de test.

1. Dans **Test Container**, dans le menu **Edition** , cliquez sur **Insérer un nouveau contrôle**.

1. Dans la boîte de dialogue **Insérer un contrôle** , sélectionnez votre contrôle dans la zone de liste. N’oubliez pas que son nom est basé sur le nom abrégé que vous avez indiqué dans l’Assistant contrôle ATL. Cliquez sur **OK**.

1. Examinez le contrôle. Notez qu’il comporte une barre de défilement. Utilisez les handles du contrôle pour redimensionner le contrôle afin d’activer la barre de défilement.

1. Testez les boutons du contrôle. La couleur d’arrière-plan est remplacée par la couleur indiquée par le bouton.

1. Fermez le **conteneur de test**.

Ensuite, essayez [de modifier le contrôle DHTML](../atl/modifying-the-atl-dhtml-control.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
