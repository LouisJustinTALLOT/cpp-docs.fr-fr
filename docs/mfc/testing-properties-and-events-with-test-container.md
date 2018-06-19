---
title: Test des propriétés et des événements avec le conteneur de Test | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbf2b7c26b7fc44a526381f4fb3e4dee5c94ba8d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381034"
---
# <a name="testing-properties-and-events-with-test-container"></a>Test des propriétés et des événements avec le conteneur de test
L’application conteneur de Test, fournie avec Visual C++, est un conteneur de contrôles ActiveX pour tester et déboguer des contrôles ActiveX. Conteneur de test permet au développeur de contrôle tester les fonctionnalités du contrôle en modifiant ses propriétés, en appelant ses méthodes et en déclenchant ses événements. Conteneur de test peut afficher des journaux de notifications de liaison de données et fournit également des fonctions de test de la fonctionnalité de persistance d’un contrôle ActiveX : vous pouvez enregistrer les propriétés dans un flux de données ou sous-stockage, les recharger et examiner les données de flux stockée. Cette section décrit comment utiliser les fonctionnalités de base du conteneur de Test. Pour plus d’informations, sélectionnez le **aide** menu lors de l’exécution du conteneur de Test.  
  
### <a name="to-access-the-activex-control-test-container"></a>Pour accéder au conteneur de Test du contrôle ActiveX  
  
1.  Générer le [exemple TSTCON : ActiveX Control Test Container](../visual-cpp-samples.md).  
  
### <a name="to-test-your-activex-control"></a>Pour tester votre contrôle ActiveX  
  
1.  Sur le **modifier** menu du conteneur de Test, cliquez sur **insérer un nouveau contrôle**.  
  
2.  Dans le **insérer un contrôle** , sélectionnez le contrôle souhaité puis cliquez sur **OK**. Le contrôle s’affiche dans le conteneur de contrôle.  
  
    > [!NOTE]
    >  Si votre contrôle n’est pas répertorié dans le **insérer un contrôle** boîte de dialogue, vérifiez que vous l’avez enregistré avec le **inscrire les contrôles** commande à partir de la **fichier** menu du Test Conteneur.  
  
 À ce stade, vous pouvez tester propriétés ou les événements de votre contrôle.  
  
#### <a name="to-test-properties"></a>Pour tester les propriétés  
  
1.  Sur le **contrôle** menu, cliquez sur **appeler les méthodes**.  
  
2.  Dans le **nom de la méthode** liste déroulante, sélectionnez la méthode PropPut pour la propriété que vous souhaitez tester.  
  
3.  Modifier la **la valeur du paramètre** ou **Type de paramètre** , puis cliquez sur le **définir la valeur** bouton.  
  
4.  Cliquez sur **Invoke** pour appliquer la nouvelle valeur à l’objet.  
  
     La propriété contient maintenant la nouvelle valeur.  
  
#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Pour tester des événements et spécifier la destination des informations sur les événements.  
  
1.  Sur le **Options** menu, cliquez sur **journalisation**.  
  
2.  Spécifiez la destination des informations sur les événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Guide pratique pour déboguer un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

