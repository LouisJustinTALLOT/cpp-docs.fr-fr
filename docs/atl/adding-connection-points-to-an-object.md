---
description: 'En savoir plus sur : ajout de points de connexion à un objet'
title: Ajout de points de connexion à un objet
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7d8274ab37cef28a58666852aad24db7d945d26e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166237"
---
# <a name="adding-connection-points-to-an-object"></a>Ajout de points de connexion à un objet

Le [Didacticiel ATL](../atl/active-template-library-atl-tutorial.md) montre comment créer un contrôle avec prise en charge des points de connexion, comment ajouter des événements, puis comment implémenter le point de connexion. ATL implémente des points de connexion avec la classe [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) .

Pour implémenter un point de connexion, vous avez deux possibilités :

- Implémentez votre propre source d’événement sortant, en ajoutant un point de connexion au contrôle ou à l’objet.

- Réutiliser une interface de point de connexion définie dans une autre bibliothèque de types.

Dans les deux cas, l’Assistant Implémentation d’un point de connexion utilise une bibliothèque de types pour effectuer son travail.

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Pour ajouter un point de connexion à un contrôle ou un objet

1. Définissez une dispinterface dans le bloc de bibliothèque du fichier. idl. Si vous avez activé la prise en charge des points de connexion quand vous avez créé le contrôle à l’aide de l’Assistant contrôle ATL, la dispinterface sera déjà créée. Si vous n’avez pas activé la prise en charge des points de connexion lorsque vous avez créé le contrôle, vous devez ajouter manuellement une dispinterface au fichier. idl. Voici un exemple de dispinterface. Les interfaces sortantes ne doivent pas obligatoirement être des interfaces de dispatch, mais de nombreux langages de script tels que VBScript et JScript requièrent cela, donc cet exemple utilise deux dispinterfaces :

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   Utilisez l’utilitaire uuidgen.exe ou guidgen.exe pour générer un GUID.

2. Ajoutez la dispinterface en tant qu' `[default,source]` interface dans la coclasse de l’objet dans le fichier. idl du projet. Là encore, si vous avez activé la prise en charge des points de connexion lorsque vous avez créé le contrôle, l’Assistant contrôle ATL crée l' `[default,source` entrée]. Pour ajouter manuellement cette entrée, ajoutez la ligne en gras :

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   Pour obtenir un exemple, consultez le fichier. idl dans l’exemple ATL [CIRC](../overview/visual-cpp-samples.md) .

3. Utilisez Affichage de classes pour ajouter des méthodes et des propriétés à l’interface d’événement. Cliquez avec le bouton droit sur la classe dans Affichage de classes, pointez sur **Ajouter** dans le menu contextuel, puis cliquez sur **Ajouter un point de connexion**.

4. Dans la zone de liste **interfaces sources** de l’Assistant Implémentation d’un point de connexion, sélectionnez **interfaces du projet**. Si vous choisissez une interface pour votre contrôle et que vous appuyez sur **OK**, vous allez :

   - Générez un fichier d’en-tête avec une classe de proxy d’événement qui implémente le code qui effectue les appels sortants pour l’événement.

   - Ajoutez une entrée à la carte de point de connexion.

   Vous verrez également une liste de toutes les bibliothèques de types sur votre ordinateur. Vous devez uniquement utiliser l’une de ces autres bibliothèques de types pour définir votre point de connexion si vous souhaitez implémenter exactement la même interface sortante que celle trouvée dans une autre bibliothèque de types.

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Pour réutiliser une interface de point de connexion définie dans une autre bibliothèque de types

1. Dans Affichage de classes, cliquez avec le bouton droit sur une classe qui implémente une macro **BEGIN_COM_MAP** , pointez sur **Ajouter** dans le menu contextuel, puis cliquez sur **Ajouter un point de connexion**.

2. Dans l’Assistant Implémentation d’un point de connexion, sélectionnez une bibliothèque de types et une interface dans la bibliothèque de types, puis cliquez sur **Ajouter**.

3. Modifiez le fichier. idl en :

   - Copiez la dispinterface à partir du fichier. idl pour l’objet dont la source d’événements est utilisée.

   - Utilisez l’instruction **importlib** sur cette bibliothèque de types.

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)
