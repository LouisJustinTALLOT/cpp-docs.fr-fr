---
title: Prise en charge COM + 1.0 dans les projets ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 4bc7683d6121dec748e30c1ea717042b9cf1ecbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562459"
---
# <a name="com-10-support-in-atl-projects"></a>Prise en charge COM + 1.0 dans les projets ATL

Vous pouvez utiliser la [Assistant Projet ATL](../../atl/reference/creating-an-atl-project.md) pour créer un projet avec prise en charge de base des composants COM + 1.0.

COM + 1.0 est conçu pour le développement d’applications distribuées dans un composant. Il fournit également une infrastructure runtime pour le déploiement et la gestion de ces applications.

Si vous sélectionnez le **prise en charge COM + 1.0** case à cocher, l’Assistant modifie le script de génération dans l’étape de liaison. Plus précisément, les COM + 1.0 liens du projet aux bibliothèques suivantes :

- Comsvcs.lib

- Mtxguid.lib

Si vous sélectionnez le **prise en charge COM + 1.0** case à cocher, vous pouvez également sélectionner **bureau d’enregistrement du composant de prise en charge**. L’inscription de composants permet à votre objet COM + 1.0 obtenir la liste des composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou tous en même temps).

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

