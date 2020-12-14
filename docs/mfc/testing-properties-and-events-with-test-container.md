---
description: 'En savoir plus sur : test des propriétés et des événements avec le conteneur de test'
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
ms.openlocfilehash: 61cccbda723fb1cfac0ca3fc696639849bde9dd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216221"
---
# <a name="testing-properties-and-events-with-test-container"></a>Test des propriétés et des événements avec le conteneur de test

L’application de conteneur de test, fournie dans Visual C++, est un conteneur de contrôles ActiveX pour le test et le débogage des contrôles ActiveX. Test Container permet au développeur de contrôle de tester les fonctionnalités du contrôle en modifiant ses propriétés, en appelant ses méthodes et en déclenchant ses événements. Le conteneur de test peut afficher des journaux de notifications de liaison de données et fournit également des fonctionnalités permettant de tester la fonctionnalité de persistance d’un contrôle ActiveX : vous pouvez enregistrer des propriétés dans un flux ou dans un sous-stockage, les recharger et examiner les données de flux stockées. Cette section décrit comment utiliser les fonctionnalités de base de test Container. Pour plus d’informations, sélectionnez le menu **aide** tout en exécutant Test Container.

### <a name="to-access-the-activex-control-test-container"></a>Pour accéder au conteneur de test de contrôle ActiveX

1. Générez l' [exemple TSTCON : conteneur de test de contrôle ActiveX](../overview/visual-cpp-samples.md).

### <a name="to-test-your-activex-control"></a>Pour tester votre contrôle ActiveX

1. Dans le menu **Edition** du conteneur de test, cliquez sur **Insérer un nouveau contrôle**.

1. Dans la zone **Insérer un contrôle** , sélectionnez le contrôle souhaité, puis cliquez sur **OK**. Le contrôle s’affiche dans le conteneur de contrôle.

    > [!NOTE]
    >  Si votre contrôle n’est pas répertorié dans la boîte de dialogue **Insérer un contrôle** , vérifiez que vous l’avez inscrit à l’aide de la commande **inscrire les contrôles** à partir du menu **fichier** de test Container.

À ce stade, vous pouvez tester les propriétés ou les événements de votre contrôle.

#### <a name="to-test-properties"></a>Pour tester les propriétés

1. Dans le menu **contrôle** , cliquez sur **appeler les méthodes**.

1. Dans la liste déroulante nom de la **méthode** , sélectionnez la méthode propput pour la propriété que vous voulez tester.

1. Modifiez la **valeur du paramètre** ou le **type de paramètre** , puis cliquez sur le bouton **définir la valeur** .

1. Cliquez sur **appeler** pour appliquer la nouvelle valeur à l’objet.

   La propriété contient maintenant la nouvelle valeur.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Pour tester des événements et spécifier la destination des informations d’événement.

1. Dans le menu **options** , cliquez sur **journalisation**.

1. Spécifiez la destination des informations d’événement.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Comment : déboguer un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)
