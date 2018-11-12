---
title: Test des propriétés et des événements avec le conteneur de test
ms.date: 11/04/2016
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
ms.openlocfilehash: cf36514c6ce2cd25a49901165fcf919cffd5da7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633361"
---
# <a name="testing-properties-and-events-with-test-container"></a>Test des propriétés et des événements avec le conteneur de test

L’application conteneur de Test, fournie avec Visual C++, est un conteneur de contrôles ActiveX pour tester et déboguer des contrôles ActiveX. Conteneur de test permet au développeur de contrôle tester les fonctionnalités du contrôle en modifiant ses propriétés, en appelant ses méthodes et en déclenchant ses événements. Conteneur de test peut afficher des journaux de notifications de liaison de données et fournit également des mécanismes pour tester la fonctionnalité de persistance d’un contrôle ActiveX : vous pouvez enregistrer les propriétés dans un flux ou sous-stockage, les recharger et examiner les données de flux stockée. Cette section décrit comment utiliser les fonctionnalités de base du conteneur de Test. Pour plus d’informations, sélectionnez le **aide** menu lors de l’exécution du conteneur de Test.

### <a name="to-access-the-activex-control-test-container"></a>Pour accéder au conteneur de Test du contrôle ActiveX

1. Générer le [exemple TSTCON : ActiveX Control Test Container](../visual-cpp-samples.md).

### <a name="to-test-your-activex-control"></a>Pour tester votre contrôle ActiveX

1. Sur le **modifier** menu du conteneur de Test, cliquez sur **insérer un nouveau contrôle**.

1. Dans le **insérer un contrôle** zone, sélectionnez le contrôle souhaité, puis cliquez sur **OK**. Le contrôle s’affiche dans le conteneur de contrôle.

    > [!NOTE]
    >  Si votre contrôle n’est pas répertorié dans le **insérer un contrôle** boîte de dialogue, assurez-vous que vous l’avez enregistré avec le **inscrire les contrôles** commande à partir de la **fichier** menu du Test Conteneur.

À ce stade vous pouvez tester les propriétés ou les événements de votre contrôle.

#### <a name="to-test-properties"></a>Pour tester les propriétés

1. Sur le **contrôle** menu, cliquez sur **appeler les méthodes**.

1. Dans le **nom de la méthode** liste déroulante, sélectionnez la méthode PropPut pour la propriété que vous souhaitez tester.

1. Modifier le **valeur du paramètre** ou **Type de paramètre** , puis cliquez sur le **définir la valeur** bouton.

1. Cliquez sur **Invoke** pour appliquer la nouvelle valeur à l’objet.

   La propriété contient maintenant la nouvelle valeur.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Pour tester des événements et spécifier la destination des informations sur les événements.

1. Sur le **Options** menu, cliquez sur **journalisation**.

1. Spécifiez la destination des informations sur les événements.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Guide pratique pour déboguer un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

