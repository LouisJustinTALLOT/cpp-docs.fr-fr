---
description: 'En savoir plus sur : test du contrôle ATL DHTML modifié'
title: Test du contrôle ATL DHTML modifié
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: a797eab308ad7fb8c5c7b72566ec3d57a169370b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138331"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Test du contrôle ATL DHTML modifié

Essayez votre nouveau contrôle pour voir comment il fonctionne maintenant.

## <a name="to-build-and-test-the-modified-control"></a>Pour générer et tester le contrôle modifié

1. Régénérez le projet et ouvrez-le dans le **conteneur de test**. Pour plus d’informations sur l’accès à un **conteneur de test**, consultez Test des [Propriétés et des événements avec le conteneur](../mfc/testing-properties-and-events-with-test-container.md) de test.

   Redimensionnez le contrôle pour afficher tous les boutons que vous avez ajoutés.

1. Examinez les deux boutons que vous avez insérés en modifiant le code HTML. Chaque bouton porte l’étiquette que vous avez identifiée dans [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Actualiser** et **HelloHTML**.

1. Testez les deux nouveaux boutons pour voir comment ils fonctionnent.

Testez maintenant les méthodes qui ne font pas partie de l’interface utilisateur.

1. Mettez en surbrillance le contrôle, afin que la bordure soit activée.

1. Dans le menu **contrôle** , choisissez **appeler les méthodes**.

   Les méthodes de la liste portant le nom de la **méthode** sont les méthodes que le conteneur peut appeler : `MethodInvoked` et `GoToURL` . Toutes les autres méthodes sont contrôlées par l’interface utilisateur.

1. Sélectionnez une méthode à appeler, puis choisissez **appeler** pour afficher la boîte de message de la méthode ou naviguer vers `www.microsoft.com` .

1. Dans la boîte de dialogue **appeler les méthodes** , choisissez **Fermer**.

Pour en savoir plus sur les différents éléments et fichiers qui composent un contrôle ATL DHTML, consultez [identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
