---
title: Infrastructure de l'application
ms.date: 11/04/2016
helpviewer_keywords:
- application framework [MFC], building applications
- applications [MFC]
- application framework [MFC]
ms.assetid: 912684e6-4418-49dc-9877-a4cd19d69d20
ms.openlocfilehash: b55635de322274ab02372251976d4ebb9511ade5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446520"
---
# <a name="application-framework"></a>Infrastructure de l'application

Le cœur de la bibliothèque MFC (Microsoft Foundation Class) est l’encapsulation d’une grande partie de l’API Windows sous C++ forme. Les classes de bibliothèque représentent des fenêtres, des boîtes de dialogue, des contextes de périphérique, des objets GDI communs tels que des pinceaux et des stylets, des contrôles et d’autres éléments Windows standard. Ces classes fournissent une interface C++ de fonction membre pratique aux structures dans les fenêtres qu’elles encapsulent. Pour plus d’informations sur l’utilisation de ces classes, consultez [rubriques relatives aux objets de fenêtre](../mfc/window-objects.md).

Toutefois, la bibliothèque MFC fournit également une couche de fonctionnalités d’application supplémentaires reposant sur l' C++ encapsulation de l’API Windows. Cette couche est une infrastructure d’application opérationnelle pour Windows qui fournit la plupart des interfaces utilisateur courantes attendues de programmes pour Windows, notamment les barres d’outils, les barres d’État, l’impression, l’aperçu avant impression, la prise en charge des bases de données et la prise en charge ActiveX. L' [utilisation des classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md) explique en détail l’infrastructure.

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception des classes](../mfc/general-class-design-philosophy.md)
