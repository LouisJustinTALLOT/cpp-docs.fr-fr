---
title: Test du contrôle ATL DHTML modifié | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b140788cd409aa5a11f93689e96fa40c1a167dfe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360343"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Test du contrôle ATL DHTML modifié
Tester votre nouveau contrôle pour voir comment il fonctionne maintenant.  
  
#### <a name="to-build-and-test-the-modified-control"></a>Pour générer et tester le contrôle modifié  
  
1.  Régénérez le projet et ouvrez-le dans le conteneur de Test. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur la façon d’accéder au conteneur de Test.  
  
     Redimensionner le contrôle pour afficher tous les boutons que vous avez ajouté.  
  
2.  Examinez les deux boutons que vous avez insérée en modifiant le code HTML. Chaque bouton porte l’étiquette que vous avez identifiés dans [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Actualiser** et **HelloHTML**.  
  
3.  Tester les deux nouveaux boutons pour voir comment ils fonctionnent.  
  
 À présent tester les méthodes qui ne font pas partie de l’interface utilisateur.  
  
1.  Mettez en surbrillance le contrôle, afin de la bordure est activée.  
  
2.  Sur le **contrôle** menu, cliquez sur **appeler les méthodes**.  
  
 Les méthodes dans la liste intitulée **nom de la méthode** sont les méthodes que le conteneur peut appeler : `MethodInvoked` et `GoToURL`. Toutes les autres méthodes sont contrôlées par l’interface utilisateur.  
  
1.  Sélectionnez une méthode à appeler et cliquez sur `Invoke` pour afficher la boîte de message de la méthode ou pour accéder à www.microsoft.com.  
  
2.  Dans le **appeler les méthodes** boîte de dialogue, cliquez sur **fermer**.  
  
 Pour en savoir plus sur les différents éléments et fichiers qui composent un contrôle ATL DHTML, consultez [identifier les éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

