---
description: 'En savoir plus sur : prise en charge de COM+ 1,0 dans les projets ATL'
title: Prise en charge COM+ 1,0 dans les projets ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 8e196bccf25667da28532248765e47906fdcee97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141282"
---
# <a name="com-10-support-in-atl-projects"></a>Prise en charge COM+ 1,0 dans les projets ATL

Vous pouvez utiliser l' [Assistant Projet ATL](../../atl/reference/creating-an-atl-project.md) pour créer un projet avec la prise en charge de base des composants COM+ 1,0.

COM+ 1,0 est conçu pour le développement d’applications distribuées basées sur des composants. Il fournit également une infrastructure d’exécution pour le déploiement et la gestion de ces applications.

Si vous activez la case à cocher **prendre en charge COM+ 1,0** , l’Assistant modifie le script de compilation dans l’étape de liaison. Plus précisément, le projet COM+ 1,0 est lié aux bibliothèques suivantes :

- comsvcs. lib

- Mtxguid. lib

Si vous activez la case à cocher **prendre en charge COM+ 1,0** , vous pouvez également sélectionner **prendre en charge l’inscription de composants**. L’inscription de composants permet à votre objet COM+ 1,0 d’obtenir une liste de composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou en une seule fois).

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programmation avec des Run-Time du code ATL et C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
