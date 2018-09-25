---
title: Implémentation d’un point de connexion (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bba7fdfd44b0a0a97a6d110d2a44b492e1ca449
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429329"
---
# <a name="implementing-a-connection-point-visual-c"></a>Implémentation d'un point de connexion (Visual C++)

Pour implémenter un point de connexion à l’aide de l’Assistant Implémentation d’un point de connexion, vous devez avoir créé un projet, comme une application ATL COM ou une application MFC, avec une prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

> [!NOTE]
>  Pour plus d’informations sur l’implémentation des points de connexion pour un projet MFC, consultez [Points de connexion](../mfc/connection-points.md).

Une fois que vous avez créé le projet, vous devez ajouter un objet ATL pour pouvoir implémenter un point de connexion. Consultez [Ajout d’objets et de contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) pour obtenir la liste des Assistants permettant d’ajouter des objets à votre projet ATL.

> [!NOTE]
>  L’Assistant ne prend pas en charge les boîtes de dialogue ATL, les services web XML créés avec ATL Server, les objets de performance ni les compteurs de performance.

Un objet connectable (c’est-à-dire une source) peut exposer un point de connexion pour chacune de ses interfaces sortantes. Chaque interface sortante peut être implémentée par un client sur un objet (autrement dit, un récepteur). Pour plus d’informations, consultez [ATL, points de connexion](../atl/atl-connection-points.md).

### <a name="to-implement-a-connection-point"></a>Pour implémenter un point de connexion

1. Dans l’affichage de classes, cliquez avec le bouton droit sur le nom de la classe pour votre objet ATL.

1. Cliquez sur **Ajouter** dans le menu contextuel, puis sur **Ajouter un point de connexion** pour afficher [l’Assistant Implémentation d’un point de connexion](../ide/implement-connection-point-wizard.md).

1. Sélectionnez les interfaces de points de connexion à implémenter dans les bibliothèques de types appropriées et cliquez sur **Terminer**.

1. Dans l’affichage de classes, examinez les classes proxy créées pour chaque point de connexion. Les classes s’affichent sous la forme CProxy*NomInterface*\<T> et sont dérivées [d’IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Double-cliquez sur la classe du point de connexion pour afficher sa définition.

   - Si vous implémentez un point de connexion pour l’interface de votre propre projet, la définition suivante s’affiche

        ```
        template< class T >
        class CProxyInterfaceName :
           public IConnectionPointImpl< T, &IID_InterfaceName >
        {
        public:
        };
        ```

         If you implement a local interface, methods and properties appear in the class body.

   - Si vous implémentez un point de connexion pour une autre interface, la définition comprend les méthodes de l’interface, précédées chacune de `Fire_`.

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Ajout de points de connexion à un objet](../atl/adding-connection-points-to-an-object.md)