---
title: Services ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 052169154a62cbd07a82f08087fc2c2db8ae46c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819055"
---
# <a name="atl-services"></a>Services ATL

Pour créer votre objet ATL COM afin qu’elle s’exécute dans un service, il suffit de sélectionner Service (EXE) à partir de la liste des options de serveur dans l’Assistant Projet ATL. L’Assistant va créer ensuite une classe dérivée de `CAtlServiceModuleT` pour implémenter le service.

Lorsque l’objet ATL COM est généré en tant que service, il sera uniquement enregistré comme un serveur local, et elle n’apparaît pas dans la liste des services dans le panneau de configuration. Il s’agit, car il est plus facile à déboguer le service comme un serveur local en tant que service. Pour l’installer en tant que service, exécutez la commande suivante à l’invite de commandes :

`YourEXE` `.exe /Service`

Pour le désinstaller, exécutez la commande suivante :

`YourEXE` `.exe /UnregServer`

Les quatre premières rubriques de cette section décrivent les actions qui se produisent pendant l’exécution de `CAtlServiceModuleT` fonctions membres. Ces rubriques s’affichent dans la même séquence que les fonctions sont généralement appelées. Pour améliorer votre compréhension de ces rubriques, il est judicieux d’utiliser le code source généré par l’Assistant Projet ATL en tant que référence. Ces quatre premières rubriques sont :

- [La fonction CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

- [La fonction CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

- [La fonction CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

- [La fonction CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

Les trois dernières rubriques expliquent les concepts relatifs au développement d’un service :

- [Entrées de Registre](../atl/registry-entries.md) pour les services ATL

- [DCOMCNFG](../atl/dcomcnfg.md)

- [Conseils de débogage](../atl/debugging-tips.md) pour les services ATL

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
