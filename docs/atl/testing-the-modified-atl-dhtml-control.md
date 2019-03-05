---
title: Test du contrôle ATL DHTML modifié
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: 55cdaba64ccb95ee5695c082a5e146b1e7dc2cf3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277234"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Test du contrôle ATL DHTML modifié

Tester votre nouveau contrôle pour voir comment il fonctionne maintenant.

## <a name="to-build-and-test-the-modified-control"></a>Pour générer et tester le contrôle modifié

1. Régénérez le projet et ouvrez-le dans **conteneur de Test**. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur l’accès à **conteneur de Test**.

   Redimensionner le contrôle pour afficher tous les boutons que vous avez ajouté.

1. Examinez les deux boutons que vous avez inséré en modifiant le code HTML. Chaque bouton porte l’étiquette que vous avez identifiés dans [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Actualiser** et **HelloHTML**.

1. Tester les deux nouveaux boutons pour voir comment ils fonctionnent.

Les méthodes qui ne font pas partie de l’interface utilisateur de test maintenant.

1. Mettez en surbrillance le contrôle, afin de la bordure est activée.

1. Sur le **contrôle** menu, choisissez **appeler les méthodes**.

   Les méthodes dans la liste intitulée **nom de la méthode** sont les méthodes que le conteneur peut appeler : `MethodInvoked` et `GoToURL`. Toutes les autres méthodes sont contrôlées par l’interface utilisateur.

1. Sélectionnez une méthode à appeler et choisissez **Invoke** pour afficher la boîte de message de la méthode ou pour accéder à `www.microsoft.com`.

1. Dans le **appeler les méthodes** boîte de dialogue, sélectionnez **fermer**.

Pour en savoir plus sur les différents éléments et les fichiers qui composent un contrôle ATL DHTML, consultez [identification des éléments du projet de contrôle DHTML Edit](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge pour le contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
