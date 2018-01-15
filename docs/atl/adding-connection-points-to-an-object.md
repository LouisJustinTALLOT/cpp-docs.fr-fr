---
title: "Ajout de Points de connexion à un objet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f63ec5bd9029302192e640e42a3d012df347219d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="adding-connection-points-to-an-object"></a>Ajout de points de connexion à un objet
Le [didacticiel ATL](../atl/active-template-library-atl-tutorial.md) montre comment créer un contrôle avec prise en charge des points de connexion, comment ajouter des événements, puis comment implémenter le point de connexion. ATL implémente les points de connexion avec le [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) classe.  
  
 Pour implémenter un point de connexion, vous avez deux possibilités :  
  
-   Implémenter votre propre source d’événements sortante, en ajoutant un point de connexion à l’objet ou le contrôle.  
  
-   Réutiliser une interface de point de connexion définie dans une autre bibliothèque de types.  
  
 Dans les deux cas, Assistant Implémentation d’un Point de connexion utilise une bibliothèque de types pour effectuer son travail.  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Pour ajouter un point de connexion à un objet ou un contrôle  
  
1.  Définissez une dispinterface dans le bloc de bibliothèque du fichier .idl. Si vous avez activé la prise en charge des points de connexion lorsque vous avez créé le contrôle avec l’Assistant contrôle ATL, la dispinterface aura déjà été créée. Si vous n’avez pas activé la prise en charge des points de connexion lorsque vous avez créé le contrôle, vous devez ajouter manuellement une dispinterface au fichier .idl. Voici un exemple d’une dispinterface. Les interfaces sortantes ne sont pas nécessairement être des interfaces de dispatch, mais de nombreux langages de script tels que VBScript et JScript imposent, par conséquent, cet exemple utilise deux dispinterfaces :  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     Utilisez l’utilitaire uuidgen.exe ou guidgen.exe pour générer un GUID.  
  
2.  Ajoutez la dispinterface comme le `[default,source]` interface dans la coclasse pour l’objet dans le fichier du fichier .idl. Là encore, si vous avez activé la prise en charge des points de connexion lorsque vous avez créé le contrôle, Assistant contrôle ATL créera le `[default,source`] entrée. Pour ajouter manuellement cette entrée, ajoutez la ligne en gras :  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     Consultez le fichier .idl dans le [Circ](../visual-cpp-samples.md) exemple ATL pour obtenir un exemple.  
  
3.  Utilisez l’affichage de classes pour ajouter des méthodes et des propriétés à l’interface d’événement. Avec le bouton droit de la classe dans l’affichage de classes, pointez sur **ajouter** dans le menu contextuel, cliquez sur **ajouter un Point de connexion**.  
  
4.  Dans le **Interfaces sources** zone de liste de l’Assistant de Point de connexion implémentez, sélectionnez **les interfaces du projet**. Si vous choisissez une interface pour votre contrôle appuyez sur **OK**, vous allez :  
  
    -   Générer un fichier d’en-tête avec une classe de proxy d’événements qui implémente le code qui fera les appels sortants pour l’événement.  
  
    -   Ajoutez une entrée pour le mappage de point de connexion.  
  
     Vous verrez également une liste de toutes les bibliothèques de types sur votre ordinateur. Vous devez uniquement utiliser un de ces autres bibliothèques de types pour définir votre point de connexion si vous souhaitez implémenter l’interface sortante même exacte trouvée dans une autre bibliothèque de types.  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Pour réutiliser une interface de point de connexion définie dans une autre bibliothèque de types  
  
1.  Dans l’affichage de classes, cliquez sur une classe qui implémente un **BEGIN_COM_MAP** (macro), pointez sur **ajouter** dans le menu contextuel, cliquez sur **ajouter un Point de connexion**.  
  
2.  Assistant Implémentation de Point de connexion, sélectionnez une bibliothèque de types et une interface dans la bibliothèque de types et cliquez sur **ajouter**.  
  
3.  Modifiez le fichier .idl pour :  
  
    -   Copiez la dispinterface à partir du fichier .idl de l’objet dont source d’événements est utilisée.  
  
    -   Utilisez le **importlib** instruction sur cette bibliothèque de types.  
  
## <a name="see-also"></a>Voir aussi  
 [Point de connexion](../atl/atl-connection-points.md)

