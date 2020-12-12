---
description: En savoir plus sur les méthodes de création d’une barre d’État
title: Méthodes de création d'une barre d'état
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 06ae4002fdffb8ba90964b5ef488d0c115b3a0e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203053"
---
# <a name="methods-of-creating-a-status-bar"></a>Méthodes de création d'une barre d'état

MFC fournit deux classes pour créer des barres d’État : [CStatusBar](reference/cstatusbar-class.md) et [CStatusBarCtrl](reference/cstatusbarctrl-class.md) (qui encapsule l’API de contrôle commun Windows). `CStatusBar` fournit toutes les fonctionnalités du contrôle commun de barre d’État, il interagit automatiquement avec les menus et les barres d’outils et gère un grand nombre des paramètres et structures de contrôle communs requis pour vous. Toutefois, l’exécutable qui en résulte sera généralement plus grand que celui créé à l’aide de `CStatusBarCtrl` .

`CStatusBarCtrl` entraîne généralement un fichier exécutable plus petit, et vous pouvez utiliser `CStatusBarCtrl` si vous n’avez pas l’intention d’intégrer la barre d’État dans l’architecture MFC. Si vous envisagez d’utiliser `CStatusBarCtrl` et d’intégrer la barre d’État dans l’architecture MFC, vous devez faire attention à la communication des manipulations de contrôle de barre d’État aux MFC. Cette communication n’est pas difficile. Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CStatusBar` .

Visual C++ offre deux façons de tirer parti du contrôle commun de barre d’État.

- Créez la barre d’État à l’aide de `CStatusBar` , puis appelez [CStatusBar :: GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl) pour accéder aux `CStatusBarCtrl` fonctions membres.

- Créez la barre d’État à l’aide du constructeur de [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

L’une ou l’autre des méthodes vous donne accès aux fonctions membres du contrôle de barre d’État. Quand vous appelez `CStatusBar::GetStatusBarCtrl` , elle retourne une référence à un `CStatusBarCtrl` objet afin que vous puissiez utiliser l’un ou l’autre ensemble de fonctions membres. Pour plus d’informations sur la construction et la création d’une barre d’État à l’aide de, consultez [CStatusBar](reference/cstatusbar-class.md) `CStatusBar` .

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Contrôles](controls-mfc.md)
