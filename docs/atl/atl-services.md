---
description: 'En savoir plus sur : ATL services'
title: Services ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 1cb1f526434cefe57dc4675d592f836e04a6cdb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148601"
---
# <a name="atl-services"></a>Services ATL

Pour créer votre objet ATL COM afin qu’il s’exécute dans un service, sélectionnez simplement service (EXE) dans la liste des options de serveur dans l’Assistant Projet ATL. L’Assistant crée ensuite une classe dérivée de `CAtlServiceModuleT` pour implémenter le service.

Lorsque l’objet ATL COM est créé en tant que service, il n’est inscrit qu’en tant que serveur local et n’apparaît pas dans la liste des services du panneau de configuration. Cela est dû au fait qu’il est plus facile de déboguer le service comme un serveur local que comme un service. Pour l’installer en tant que service, exécutez la commande suivante à l’invite de commandes :

`YourEXE` `.exe /Service`

Pour le désinstaller, exécutez la commande suivante :

`YourEXE` `.exe /UnregServer`

Les quatre premières rubriques de cette section traitent des actions qui se produisent pendant l’exécution des `CAtlServiceModuleT` fonctions membres. Ces rubriques s’affichent dans la même séquence que les fonctions qui sont généralement appelées. Pour améliorer votre compréhension de ces rubriques, il est judicieux d’utiliser le code source généré par l’Assistant Projet ATL comme référence. Ces quatre premières rubriques sont les suivantes :

- [La fonction CAtlServiceModuleT :: Start](../atl/reference/catlservicemodulet-class.md#start)

- [Fonction CAtlServiceModuleT :: ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Fonction CAtlServiceModuleT :: Run](../atl/reference/catlservicemodulet-class.md#run)

- [La fonction CAtlServiceModuleT :: Handler](../atl/reference/catlservicemodulet-class.md#handler)

Les trois dernières rubriques abordent les concepts liés au développement d’un service :

- [Entrées de Registre](../atl/registry-entries.md) pour les services ATL

- [DCOMCNFG](../atl/dcomcnfg.md)

- [Conseils de débogage](../atl/debugging-tips.md) pour ATL services

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
