---
title: Infrastructure de l'application
ms.date: 11/04/2016
helpviewer_keywords:
- application framework [MFC], building applications
- applications [MFC]
- application framework [MFC]
ms.assetid: 912684e6-4418-49dc-9877-a4cd19d69d20
ms.openlocfilehash: 3d6616380e9461489d208281a34e0b0b4aa2caf0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626017"
---
# <a name="application-framework"></a>Infrastructure de l'application

Le cœur de la bibliothèque MFC (Microsoft Foundation Class) est l’encapsulation d’une grande partie de l’API Windows au format C++. Les classes de bibliothèque représentent des fenêtres, des boîtes de dialogue, des contextes de périphérique, des objets GDI communs tels que des pinceaux et des stylets, des contrôles et d’autres éléments Windows standard. Ces classes fournissent une interface de fonction membre C++ pratique aux structures dans les fenêtres qu’elles encapsulent. Pour plus d’informations sur l’utilisation de ces classes, consultez [rubriques relatives aux objets de fenêtre](window-objects.md).

Toutefois, la bibliothèque MFC fournit également une couche de fonctionnalités d’application supplémentaires reposant sur l’encapsulation C++ de l’API Windows. Cette couche est une infrastructure d’application opérationnelle pour Windows qui fournit la plupart des interfaces utilisateur courantes attendues de programmes pour Windows, notamment les barres d’outils, les barres d’État, l’impression, l’aperçu avant impression, la prise en charge des bases de données et la prise en charge ActiveX. L' [utilisation des classes pour écrire des applications pour Windows](using-the-classes-to-write-applications-for-windows.md) explique en détail l’infrastructure.

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception de classes](general-class-design-philosophy.md)
